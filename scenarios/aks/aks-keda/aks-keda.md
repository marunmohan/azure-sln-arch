# Kubernetes-based Event Driven Autoscaler (KEDA)

## References

* [KEDA](https://keda.sh/)
* [KEDA at Alibaba](https://bit.ly/alibaba-cloud-keda)
* [Azure Functions on Kubernetes with KEDA](https://docs.microsoft.com/en-us/azure/azure-functions/functions-kubernetes-keda)
* [Thinktecture, Serverless workloads in K8s with KEDA](https://www.thinktecture.com/en/kubernetes/serverless-workloads-with-keda/serverless-workloads-with-keda/)

## Why do you want KEDA?

KEDA lets you scale deployments in Kubernetes based on **external** events or metrics.

In Kubernetes, you can use Horizontal Pod Autoscaler (HPA) to scale Deployments based on metrics generated **inside** of the cluster. Especially when running Kubernetes in combination with external, cloud-based services such as Azure Service Bus, your application artifacts have to scale on those external metrics.

## Scenario Setup

### Azure Environment Setup

Run the setup script to create the Azure resources and install KEDA. It's taken from [Thinktecture, Serverless workloads in K8s with KEDA](https://www.thinktecture.com/en/kubernetes/serverless-workloads-with-keda/serverless-workloads-with-keda/).

```sh
./scripts/create-azure-resources.sh
```

### Azure Function

```sh
% mkdir Thinktecture.MessageTransformer
% cd Thinktecture.MessageTransformer
% func version
4.0.3971
% func init --worker-runtime dotnet --docker

Writing /azure-sln-arch/scenarios/aks/aks-keda/Thinktecture.MessageTransformer/.vscode/extensions.json
Writing Dockerfile
Writing .dockerignore
% func new -n MessageTransformer -l csharp -t ServiceBusQueueTrigger
Select a number for template:Function name: MessageTransformer

The function "MessageTransformer" was created successfully from the "ServiceBusQueueTrigger" template.
```

There's some code updates in the function. See the code and the Thinktecture blog. It's updated to work with the inbound and outbound queues and has functionality to reverse the message.

### Build and Publish the Docker Image

```sh
docker build . -t $acr.azurecr.io/message-transformer:0.0.1 \
    -t $acr.azurecr.io/message-transformer:latest

docker push $acr.azurecr.io/message-transformer:0.0.1
docker push $acr.azurecr.io/message-transformer:latest
```

### Deploy Azure Functions to Kubernetes

Run command to split out Kubernetes definitions which we can then modify.

```sh
func kubernetes deploy --namespace tt \
    --name transformer-fn \
    --image-name $acr.azurecr.io/message-transformer:0.0.1 \
    --polling-interval 5 \
    --cooldown-interval 10 \
    --min-replicas 0 \
    --max-replicas 50 \
    --secret-name tt-func-auth \
    --dry-run > keda-deployment.yaml
```

This gives you a keda-deployment.yaml file which then needs updating to add the *TriggerAuthentication* resource, and modify the *ScaledObject* resource.

### Create Load

Create a new console app for adding messages to the queue.

```sh
dotnet new console -n Thinktecture.Samples.KEDA.Publisher -o ./Publisher
cd Publisher
```

Code was written to load messages to the queue.

You need to add the creds for the publisher to the app config. Get the key:

```sh
az servicebus queue authorization-rule keys list -g $rg \
    --namespace-name adt-sb-2659 \
    --queue-name inbound \
    -n publisher-app \
    --query "primaryConnectionString" \
    -o tsv
```

## Installing KEDA on Kubernetes

> Note: You don't need to do this if you run the script to setup the environment. It's included in the script.

### Create the K8s cluster

```sh
id=$RANDOM
rg=adt-rg-$id
loc=westeurope
acr=adt0acr0$id
aks=adt-aks-$id

az group create -g $rg -l $loc
az acr create -g $rg -n $acr -l $loc --sku Basic
az aks create -g $rg -n $aks -l $loc --attach-acr $acr --generate-ssh-keys

az aks install-cli
az aks get-credentials -g $rg -n $aks
```

### Install KEDA

```sh
# add KEDA repo
helm repo add kedacore https://kedacore.github.io/charts

# update the repo
kubectl create namespace keda
helm install keda kedacore/keda --namespace keda
```

### Verify deployment

```sh
kubectl get all -n keda

NAME                                                   READY   STATUS    RESTARTS   AGE
pod/keda-operator-778cf49bcf-vbqdc                     1/1     Running   0          53s
pod/keda-operator-metrics-apiserver-5ccf7b74dd-bt2jp   1/1     Running   0          53s

NAME                                      TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)          AGE
service/keda-operator-metrics-apiserver   ClusterIP   10.0.142.28   <none>        443/TCP,80/TCP   53s

NAME                                              READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/keda-operator                     1/1     1            1           53s
deployment.apps/keda-operator-metrics-apiserver   1/1     1            1           53s

NAME                                                         DESIRED   CURRENT   READY   AGE
replicaset.apps/keda-operator-778cf49bcf                     1         1         1       53s
replicaset.apps/keda-operator-metrics-apiserver-5ccf7b74dd   1         1         1       53s
```
