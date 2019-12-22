# AZ 900 Study Guide

# CLOUD CONCEPTS

## Cloud computing
- rent vs. purchase
- pay as you go
- shared responsibility model

## Core Cloud Services
- Compute
- Network
- Storage
- Application Services
- Analytics

## Elasticity
Major pattern benefitting from cloud computing
Resources change according to the workload changes 
Either static or elastic scaling (e.g. seasonal demand for a retail web site)

## Scalability
- Increase/Decrease resources based on workload demand
- Vertical scaling
  - Also known as scaling up
  - Add additional resources to increase the power of the workload (e.g. more CPU to a VM)
- Horizontal scaling
  - Also known as scaling out
  - Adding many smaller resources to cater to a workload


## Defitnion of SLA
: Service Level Agreement (SLA) is an agreement with business and application teams
on the expected performance and availability of a specific service

## General SLA practices:
- Define SLA for each workload
- Depdendency mapping (include internal and external dependencies)
- Identify single points of failure (e.g. app needs 99.99% but is depdending on a service with 99.9%)

## Key terms:
| Term | Definition |
| ----------- | ----------- |
| Mean Time To Recovery (MTTR) | Average time to recover from an outage |
| Mean Time Between Failures (MTBF) | Average time between outages |
| Recovery Point Objective (RPO) | Interval of time in which data could be lost during a recovery (e.g. 5min RPO means up to 5 minutes of data are lost.) |
| Recovery Time Objective (RTO) | Time requirement for recovery to be completed in before there is a business impact. |

## Fault Tolerance:
- Redundency is built into services so that if one component fails, another takes its place.
- Reduce impact when disaster occurs.

## Disaster Recovery:
- Planning for catastrophic failure of workloads
- Region to region failover
- OnPrem to cloud failover
- Automation & Orchestration.

## High Availability (HA) eamples:
*Host outage*
- When an underlying host has a catastrophic failure, the VM will automatically restarted on another host.
- Availability sets and zones further incrase the availability.

*Cross Region Deployment*
- An application is deployed in a configuration to be highly available across regions
- When a service in one region has an outage, traffic can continue to run in the second region.

## Cloud Service Models
Revolves around what is managed:
1. Application
2. Data
3. Runtime
4. Middleware
5. O/S
6. Virtualization
7. Servers
8. Storage
9. Networking

### Pizza As A Service Example

![Pizza As A Service](https://s3.amazonaws.com/algamthe.dev/images/PizzaAsService.jpeg "Pizza As A Service")

- Traditional (we manage everything)
- Infrastructure As A Service (IaaS) (we manage 1-5, vendor manages 6-9). 
Typically used for "lift and shift" scenarios where we move VMs from onPrem to cloud.
- Platform As A Service (PaaS) (manage 1 and 2, rest is on the vendor).
Either used as a development framework (e.g. Azure App services, Pivotal Cloud Foundry, IoT, Biz Analytics)
- Software As A Service (SaaS) (all is managed by the vendor)
(e.g. Office365, Salesforce, etc)

### IT Cloud Services
![IT Cloud Service](https://s3.amazonaws.com/algamthe.dev/images/CloudServiceModels.png "IT Cloud Service")


## Cloud Economics

### Economies of scale
> Ability to do things efficiently or at lower cost due to operating at a large scale.

### Benefits
- Able to acquire hardware at lower costs
- Local Gov deals
- These savings are passed on to the consumer
- Datacenter efficiencies
  
### CAPEX vs. OPEX

| CAPEX | OPEX |
| ----------- | ----------- |
| Spending on infrastructure is completed upfront | No upfront cost |
| Cost written off over a period of time | Pay as you go |
|  | Deduct from tax bill in same year as expense occurs |

#### Typical *onPrem* OPEX costs
- Server costs
- Storage costs
- Network costs
- Backup and Archive costs
- Datacenter Costs (includes Disaster Recovery)

#### Typical *Cloud* OPEX costs
- Server lease costs
- Software and future leases
- Usage/Demand cost scaling

#### CAPEX vs OPEX Benefits
| CAPEX | OPEX |
| ----------- | ----------- |
| Predictability | Try and buy |
| Cost effective when you consume the infrastructure quickly | Low initial costs |
|  | Demand fluctuation |

## Cloud Deployment Models

### Public Cloud
- Common deployment model
- Azure/AWS/GCP examples
- Everything runs on the provider's hardware

| Advantages | Disadvantages |
| ----------- | ----------- |
| High scalability/agility | some security requirements cannot be met by the public cloud |
| Pay as you go pricing, pay for usage, no OPEX | Gov/Industry/Legal policies that cannot<br>be met by the public cloud |
| Not responsible for maintenance or hardware updates | You don't own the infrastructure |
| *Minimal* tech knowledge needed to get *started* | Unique business requirements |

### Private Cloud
- Create a cloud-like environment onPrem
- Responsible for hardware and software services
- Characterised by:
  - Self service
  - Automation
  - Agility
  - Financial Transparency

| Advantages | Disadvantages |
| ----------- | ----------- |
| Complete control over all resources | Large upfront costs |
| Complete security control | High skillset required |
| May be able to meet strict compliance requirements<br>that cannot be met by the public cloud | Owning the equipment adds a lag into provisioning process |
| *Minimal* tech knowledge needed to get *started* | Datacenter management |

### Hybrid Cloud
- Combines public and private clouds
- Allows flexibility to run in the most appropriate location
- Consume public cloud services as needed, and potentially keep legacy workloads running onPrem

| Advantages | Disadvantages |
| ----------- | ----------- |
| Flexibility | Complicated to maintain and setup<br>(need to factor in specific cloud knowledge vs. onPrem<br>and also when going with multiple cloud providers) |
| Support for legacy apps while enabling modern apps to move  | Can be more expensive than simply selecting one model |
| Continue to use your own equipment and investments |  |
|  |  |

# AZURE CORE SERVICES
## Azure Cloud Services Overview

![Azure Cloud Services Overview](https://s3.amazonaws.com/algamthe.dev/images/AzureServicesOverview.png "Azure Cloud Services Overview")

## Azure Portal Overview Demo

- Can create and share Dashboards
- There is a CLI option to run Powershell commands right in the portal
- Subscription is the billing group this resource will be part of
- Resource group is a logical grouping of resources
- There is a download template option available after creating a VM

## Resource Group Demo

- there is an activity log that logs everything done with a resource group
- IAM controls can be added directly to a resource group
- Resource groups can be tagged (stuff like MaintenanceWindow, CostCentre, etc)
- there are events that be added to a resource group, more related to logic apps and the like.
- costs can be seen under a given group's resource costs option
- Deployment can display all deployments done (either via portal or ARM templates) - pay attention to this
- resource groups can have policies added to them (force encryption, restrict VM types within a resource group) - pay attention to this
- there is an option to download the deployment scripts via the Automation Scripts option.

# AZURE CORE SERVICES: COMPUTE

## Azure VMs
### What is a VM:

![What is a VM](https://s3.amazonaws.com/algamthe.dev/images/WhatIsAVM.png "What is a VM")

### VM Types:

| Type | Purpose |
| ----------- | ----------- |
| A - Basic | Basic version of the A series for<br>testing and development |
| A - Standard | General purpose VMs |
| B - Burstable | Burstable instances that can burst to the<br>full capacity of the CPU when needed.<br>Mostly for things like webservers, as when they are not in use,<br>they would accumulate CPU credits that will be consumed when utilised |
| D - General Purpose | Built for enterprise applications.<br> DS instances offer premium storage. |
| E - Memory Optimized | High memory to CPU core ratio.<br> ES instances offer premium storage. |
| F - CPU Optimized | High CPU core to memory ratio.<br> FS instances offer premium storage. |
| G - Godzilla | Very large instances ideal for<br>large databases and big data use cases. |
| H - High performance compute | High performance compute instances<br>aimed at very high-end computational needs<br>such as molecular modelling and other scientific applications. |
| L - Storage optimized | Storage optimized instances<br>which offer a higher disk throughput and IO. |
| M - Large memory | Another large scale memory option<br>that allows for up to 3.5 TB of RAM. |
| N - GPU enabled | GPU enabled instances. |
| SAP HANA on<br>Azure certified instances| Specialized instances purposely<br>built and certified for running SAP HANA |

### VM Specializations
- S -> Premium storage option available (e.g. DSv2)
- M -> Large memory configuration of the instance (e.g. Standard A2m_v2)
- R -> Supports remote direct memory access (RDMA) (e.g. H16mr)

### Connecting to a Windows VM
- Using RDP
- Using Powershell (Get-AzureRmRemoteDesktopFile)
- WinRM (Http**s** on port 5986/Http on port 5985)

#### WINRM Self-signed process
- Create key vault
- Create self-signed certificate
- Upload cert to key vault
- Get URL for cert from key vault
- Reference the cert when creating the VM

[More info here](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/winrm)

## VM Availability

### Availability Sets

**Potential for VM impact**
- Planned maintenance
- Unplanned hardware maintenance
- Unexpected Downtime

**Availablity Sets**
> - Group two or more machines in a set
> - Separated based on fault and update domains

### Fault and Update Domains

#### Fault Domain (FD):
- A rack that has its own power and networking connectivity
- A single availability set can have up to 3 FDs
- So our VMs can be spread across those 3 FDs, so if one FD has an outage<br>the other VMs will remain unaffected.

#### Update Domain (UD):
- These help Microsoft update their **underlying hosts** sequentially.
- Microsoft wont update the same UDs at the same time.
- Up to 20 UDs can be allowed
- Order cannot be controlled

![Fault and Update Domains](https://s3.amazonaws.com/algamthe.dev/images/FaultUpdateDomains.png "Fault and Update Domains")

### Planning for availability
- Seperate the VMs across sets

![Planning for availability](https://s3.amazonaws.com/algamthe.dev/images/PlanningAvailability.png "Planning for availability")

## Availability Zones

- An Availability Zone in an Azure region is a combination of a fault domain and an update domain
- Offers 99.99% availability
- Minimize impact of planned and unplanned downtime
- Enforce them like availability sets but you get to choose your azure zone
- It is either zones or sets, can't have both. You will be moved to zones - double check this

![Azure Availability Zones](https://docs.microsoft.com/en-us/azure/availability-zones/media/az-overview/az-graphic-two.png "Azure Availability Zones")

Azure services that support Availability Zones fall into two categories:

- Zonal services – you pin the resource to a specific zone (for example, virtual machines, managed disks, Standard IP addresses), or
- Zone-redundant services – platform replicates automatically across zones (for example, zone-redundant storage, SQL Database).

## App Services
Consist of the following:
- Web apps
  - formarly known as "websites"
  - build an host using various programming languages
  - auto-scalable
  - highly available
  - DevOps features
- Mobile apps
  - build a mobile app backend
  - highly scalable and available
  - build native (iOS/Android/Windows/cross-core) apps
  - Benefit: shares the same app service deployment to reduce run rates
- Logic apps
  - automate business process and workflows
  - use orchestration engine to build a solution
  - Examples:
    - Every time your app calls an API, do something
    - Routinely ingest data from a storage blob or external SaaS-based service
    - Regularly check tweets or #Slack messages from a specific account
- API apps
  - Create consume or call APIs
  - Can also call external API services or your own

### Security features
- Features run on isolated VM
- ISO, SOC, and PCI compliant
- Fully integrated Azure Active Directory
- Managed service identity
- Supports custom domains, SSL/TLS, as well as custom certificates<br>using wildcard or subject alternate name
- Support for multiple authentication protocols (OAuth/OpenID/AD)
- Integration with WAF

### DevOps features
- CI/CD support with Git/Github/Bitbucket/MS VSTS
- IDE tool integration
- Deployment from external folders like Dropbox and OneDrive
- Deployment slots: stage environments (Dev/Prod/etc)

### App service plans overview
Define the following first:
- Which subscription the plan belongs to?
- Location
- Pricing tier
- Instance size

Then Configure the following:
- Scale count (e.g. 1,2,3 instances)
- Scale rules (allow for autoscaling where applicable)
- Scale up (increase the resources associated with the app plan,<br>this is how you switch the plan you first created)

[More info here](https://docs.microsoft.com/en-us/azure/app-service/overview-hosting-plans)

### App service pricing tiers

Runs on shared compute resources
- free
- shared

Runs on dedicated azure VMs
- basic
- premium
- isolated (also known as app service environment)

[MUST READ ABOUT SERVICE LIMITS](https://docs.microsoft.com/en-us/azure/azure-subscription-service-limits)

### App service plans general guidelines
- Create for specific apps
- Deploy app services to support the application
- DO NOT use a single plan for every web app (difficult to scale and manage)
- Combine app services vs mass VM creation
- Combine other services in the same resource group

### App service environments (ASEs)
- Fully isolated environments
- Can host mobile apps/web apps/API apps/azure functions
- For high performance apps - high CPU and/or memory
- Individual or multiple services plan
- Can be deployed
  - Internal ASE: Internal Virtual IP is created on an internal Azure Load Balancer (AKA ILB ASE).
  - External ASE: Accessible via the Internet. After selecting the VNet, you select the IP address you want to use.
- Created in a subnet of a VNet to achieve isolation.
- May take hours to provision due to the dedicated nature of the resource.

## Containers

## Serverless computing

## Comparing compute options
