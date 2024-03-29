# Azure Solutions Architect Expert

This repo contains notes and examples for passing the AZ-303 / AZ-304 exams and getting Azure Solutions Architect Expert certified.

The repository has a notes from the MS Learn series for the certification and CLI code for all the different technologies. The [scenarios](./scenarios) folder contains CLI examples of deploying the technologies into a subscription.

## Certification

[![Credential](.assets/microsoft-certified-azure-solutions-architect-expert.1.png)](https://www.credly.com/badges/60e941a4-18ad-45e1-a72a-fdf5a0d028e2/public_url)

## References

- Azure Certifications Solutions Architect [home page](https://docs.microsoft.com/en-us/learn/certifications/azure-solutions-architect/)
- [Exam AZ-303: Microsoft Azure Architect Technologies](https://docs.microsoft.com/en-us/learn/certifications/exams/az-303)
  - [skils outline](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4psD6)
- [Exam AZ-304: Microsoft Azure Architect Design](https://docs.microsoft.com/en-us/learn/certifications/exams/az-304)
- [Azure CLI docs](https://docs.microsoft.com/en-gb/cli/azure/)
- [Azure Well-Architected Framework - intro](https://azure.microsoft.com/en-gb/blog/introducing-the-microsoft-azure-wellarchitected-framework/)

## Microsoft Learn Resources

- [x] [Architect network infrastructure in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-network-infrastructure/)
- [x] [Architect storage infrastructure in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-storage-infrastructure/)
- [x] [Architect compute infrastructure in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-compute-infrastructure/)
- [x] [Architect infrastructure operations in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-infrastructure-operations/)
- [x] [Architect a data platform in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-data-platform/)
- [x] [Architect message brokering and serverless applications in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-messaging-serverless/)
- [x] [Architect modern applications in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-modern-apps/)
- [x] [Architect API integration in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-api-integration/)
- [x] [Architect migration, business continuity, and disaster recovery in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-migration-bcdr/)

## Microsoft Docs

### Implement and Monitor an Azure Infrastructure (50-55%)

Implement cloud infrastructure monitoring

- [ ] monitor security
    - [Azure Security Fundamentals](https://docs.microsoft.com/en-us/azure/security/fundamentals/overview)
    - [Azure Security Center](https://docs.microsoft.com/en-us/azure/security-center/) - prevent, detect, respond to threats with visibility / control over security of Azure resources.
    - [Microsoft Cloud App Security (MCAS)](https://docs.microsoft.com/en-us/cloud-app-security/)
    - [Vulnerability scanning with Tinfoil](https://azure.microsoft.com/en-gb/blog/web-vulnerability-scanning-for-azure-app-service-powered-by-tinfoil-security/)
- [ ] monitor performance
    - [Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/)
    - [Azure App Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)
    - [Azure Advisor performance efficiency](https://docs.microsoft.com/en-us/azure/advisor/advisor-performance-recommendations)
- [ ] monitor health and availability
- [ ] monitor cost
    - [Azure Advisor cost optimisation](https://docs.microsoft.com/en-us/azure/advisor/advisor-cost-recommendations)
- [ ] configure advanced logging
- [ ] configure logging for workloads
- [ ] initiate automated responses by using Action Groups
- [ ] configure and manage advanced alerts

Implement storage accounts

- [ ] select storage account options based on a use case
- [ ] configure Azure Files and blob storage
- [ ] configure network access to the storage account
- [ ] implement Shared Access Signatures and access policies
- [ ] implement Azure AD authentication for storage
- [ ] manage access keys
- [ ] implement Azure storage replication
- [ ] implement Azure storage account failover


Implement VMs for Windows and Linux

- [Linux, automate configuration](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-automate-vm-deployment)
- [Use cloud init](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/using-cloud-init)

- [ ] configure High Availability
- [ ] configure storage for VMs
- [ ] select virtual machine size
- [ ] implement Azure Dedicated Hosts
- [ ] deploy and configure scale sets
    - [Virtual Machines Scale Sets docs](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/)
- [ ] configure Azure Disk Encryption


Automate deployment and configuration of resources

- [ ] save a deployment as an Azure Resource Manager template
- [ ] modify Azure Resource Manager template
- [ ] evaluate location of new resources
- [ ] configure a virtual disk template
- [ ] deploy from a template
- [ ] manage a template library
- [ ] create and execute an automation runbook


Implement virtual networking

- [x] implement VNet to VNet connections
    - [Configure a VNet-to-VNet VPN gateway connection by using the Azure portal](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-vnet-vnet-resource-manager-portal)
- [x] implement VNet peering
    - [Virtual network peering](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)


Implement Azure Active Directory

- [x] add custom domains
    - [Add your custom domain name using the Azure Active Directory portal](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/add-custom-domain)
- [ ] configure Azure AD Identity Protection
    - [Azure AD Identity Protection documentation](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/)
- [ ] implement self-service password reset
- [ ] implement Conditional Access including MFA
- [ ] configure user accounts for MFA
- [ ] configure fraud alerts
- [ ] configure bypass options
- [ ] configure Trusted IPs
- [ ] configure verification methods
- [ ] implement and manage guest accounts
- [ ] manage multiple directories


Implement and manage [hybrid identities](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/)

- [x] install and configure Azure AD Connect
    - [Detailed setup commands](hybrid-identity/)
    - [Install a new AD forest using CLI](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/virtual-dc/adds-on-azure-vm)
    - [Installing AD DS using PowerShell](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/install-active-directory-domain-services--level-100-#BKMK_PS)
    - [Install Azure AD Connect with Express Settings (PHS)](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-install-express)
- [x] identity synchronization options
    - [What is Hybrid Identity, common scenarios](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-hybrid-identity?toc=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Factive-directory%2Fhybrid%2Ftoc.json&bc=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fbread%2Ftoc.json#common-scenarios-and-recommendations)
    - [AD FS](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-fed-whatis)
- [x] configure and manage password sync and password writeback
- [ ] configure single sign-on
- [ ] use Azure AD Connect Health



### Implement Management and Security Solutions (25-30%)

Manage workloads in Azure

- [x] migrate workloads using Azure Migrate
    - [Virtual Machines docs](https://docs.microsoft.com/en-us/azure/virtual-machines/)
    - [Prepare a VHD to upload](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/prepare-for-upload-vhd-image)
    - [Support for gen2 VMs on Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/generation-2)
    - [Add-AzVhd](https://docs.microsoft.com/en-us/powershell/module/az.compute/add-azvhd?view=azps-5.9.0)
- [ ] implement Azure Backup for VMs
- [ ] implement disaster recovery
- [ ] implement Azure Update Management


Implement load balancing and network security

- [ ] implement Azure Load Balancer
- [ ] implement an application gateway
- [ ] implement a Web Application Firewall
- [ ] implement Azure Firewall
- [ ] implement Azure Firewall Manager
- [ ] implement the Azure Front Door Service
- [ ] implement Azure Traffic Manager
- [ ] implement Network Security Groups and Application Security Groups
- [x] implement Bastion
    - Secure seamless RDP/SSH connectivity to VMs via Azure Portal. Basically jump servers on the perimeter network.
    - [Bastion documentation](https://docs.microsoft.com/en-us/azure/bastion/)
    - [Bastion peered network scenario in CLI](scenarios/bastion-vnet-peer.md)


Implement and manage Azure governance solutions

- [Azure Governance docs](http://aka.ms/governancedocs)
- [Azure Cloud Adoption Framework](http://aka.ms/cloudadoption)
- [Well architected framework](https://docs.microsoft.com/en-us/azure/architecture/framework/)
- [Azure Architecture Center](https://docs.microsoft.com/en-us/azure/architecture/)
- [John Savill, Azure Master Class Part 3 - Governance](https://www.youtube.com/watch?v=cIh_Nfl67T0)
- [MS learn, Build a cloud governance strategy on Azure](https://docs.microsoft.com/en-us/learn/modules/build-cloud-governance-strategy-azure/3-create-subscription-governance-strategy)
- [Azure Policy docs](https://docs.microsoft.com/en-gb/azure/governance/policy/)

- [Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/)
    - [Identity governance](https://docs.microsoft.com/en-us/azure/active-directory/governance/identity-governance-overview)
    - [Entitlement management](https://docs.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-overview)
    - [Access reviews](https://docs.microsoft.com/en-us/azure/active-directory/governance/access-reviews-overview)
    - [Lifecycle management](https://docs.microsoft.com/en-us/azure/active-directory/governance/what-is-identity-lifecycle-management) - automate and manage the entire digital identity lifecycle process.
- [Five disciplines of cloud governance](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/govern/governance-disciplines)


https://docs.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review
https://docs.microsoft.com/en-us/azure/active-directory/governance/access-reviews-overview

- [x] create and manage hierarchical structure that contains management groups, subscriptions and resource groups
- [x] assign RBAC roles
- [x] create a custom RBAC role
    - [Azure RBAC docs](https://docs.microsoft.com/en-us/azure/role-based-access-control/)
    - [Azure custom roles](https://docs.microsoft.com/en-us/azure/role-based-access-control/custom-roles)
- [ ] configure access to Azure resources by assigning roles
- [ ] configure management access to Azure
- [ ] interpret effective permissions
- [x] set up and perform an access review
- [ ] implement and configure an Azure Policy
- [ ] implement and configure an Azure Blueprint


Manage security for applications

[Azure Security Benchmark](https://docs.microsoft.com/en-us/security/benchmark/azure/introduction)

- [ ] implement and configure Key Vault
- [ ] implement and configure Managed Identities
- [ ] register and manage applications in Azure AD


### Implement Solutions for Apps (10-15%)

Implement an application infrastructure

- [ ] create and configure Azure App Service
- [ ] create an App Service Web App for Containers
- [ ] create and configure an App Service plan
- [ ] configure an App Service
- [ ] configure networking for an App Service
- [ ] create and manage deployment slots
- [ ] implement Logic Apps
- [ ] implement Azure Functions


Implement container-based applications

- [x] create a container image
- [x] configure Azure Kubernetes Service
    - [Azure Kubernetes Service](https://docs.microsoft.com/en-us/azure/aks/)
    - [Deploy a cluster with CLI](https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough)
    - [Container insights](https://docs.microsoft.com/en-us/azure/azure-monitor/containers/container-insights-overview)
- [x] publish and automate image deployment to the Azure Container Registry
    - [Deployment strategies and Canary](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/kubernetes/deployment-strategies?view=azure-devops)
    - [Build and deploy to Kubernetes service](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/kubernetes/aks-template?view=azure-devops)
    - [Canary deployment strategy for Kubernetes deployments](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/kubernetes/canary-demo?view=azure-devops&tabs=yaml)
    - [Multi-cloud Kubernetes deployments](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/kubernetes/multi-cloud?view=azure-devops)
    - [Azure DevOps](https://docs.microsoft.com/en-us/azure/devops-project/azure-devops-project-aks)
    - Lab: [Deploying a multi-container app to AKS](https://azuredevopslabs.com/labs/vstsextend/kubernetes/)
- [x] publish a solution on an Azure Container Instance


### Implement and Manage Data Platforms (10-15%)

Implement NoSQL databases

- [ ] configure storage account tables
- [ ] select appropriate Cosmos DB APIs
- [ ] set up replicas in Cosmos DB


Implement Azure SQL databases

https://docs.microsoft.com/en-us/azure/azure-sql/database/auto-failover-group-overview

- [ ] configure Azure SQL database settings
    - [Backup and restore](https://docs.microsoft.com/en-us/azure/azure-sql/virtual-machines/windows/automated-backup)
    - [Backup and restore decision matrix](https://docs.microsoft.com/en-us/azure/azure-sql/virtual-machines/windows/backup-restore#decision-matrix)
- [ ] implement Azure SQL Database managed instances
- [ ] configure HA for an Azure SQL database
- [ ] publish an Azure SQL database


### Azure Arc

- [ ] [Azure Arc Jumpstart](https://azurearcjumpstart.io)
- [ ] [Azure Arc docs](https://docs.microsoft.com/en-us/azure/azure-arc/)
