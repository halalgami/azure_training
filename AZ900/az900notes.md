**AZ 900 Study Guide**

1. [CLOUD CONCEPTS](#cloud-concepts)
   1. [Cloud computing](#cloud-computing)
   2. [Core Cloud Services](#core-cloud-services)
   3. [Elasticity](#elasticity)
   4. [Scalability](#scalability)

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

### What are containers?
- Standardized packages for software and their depdencies
- A way to isolate apps from each other
- Works on Linux and Windows
- Allows separate apps to share the same OS kernel

#### Reasons behind popularity
- Monolithic app issues
  - Minor code changes required full recompile and testing
  - Application becomes a single point of failure
  - Application becomes difficult and often expensive to scale

#### Solution to the above is the following
- Microservices: break an application to separate services
- 12 Factor apps: make the app independently scalable, stateless, highly available by design

### Monolithic vs. Microservices
| Monolithic | Microservices |
| ----------- | ----------- |
| Simple deployments | Partial deploymens |
| Inter-module refactoring | Strong module boundaries |
| Vertical scaling | Horizontal scaling |
| Technology mono-culture | Technology diversity |

### Keys to microservices
- Functional decomposition (decompose the app into separate services)
- Horizontal scale (scale what you need, not what you don't and what scaling options)
- Data decoupling (pick the best DB for each service)

## Serverless computing

- Abstraction of server infrastructure and operating system
- Fully managed services
- Only pay for what you use
- Flexibility to scale as needed
- Stitch together applications and services seemlessly

### Azure serverless computing services
- Azure functions
  - Support for C#,F#,Javascript, Java
  - Pay per use pricing
    - Consumption plan
    - App service plan (run on the same plan as other services)
  - Integrated security using OAuth providers
  - Code in the portal or deploy via DevOps tools
- Logic apps
  - Workflow engine
  - Orchestrate and stitch together functions and services
  - Visualize, design, build, automate
  - Key concept of trigger -> action
- Event grid


### Comparing compute options

![Cloud Compute options](https://s3.amazonaws.com/algamthe.dev/images/ComparisonCompute.png "Cloud Compute options")

# AZURE CORE SERVICES: NETWORKING

![Networking Overview](https://s3.amazonaws.com/algamthe.dev/images/NetOverview.png "Networking Overview")

[Read more about VNets](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)


## Azure Virtual Network

![Azure Virtual Network](https://s3.amazonaws.com/algamthe.dev/images/VNetExample.png "Azure Virtual Network")

**Capabilities**
- Isolation
- Internet access
- Can contain multiple Azure resources (VMs and other cloud services)
- VNet connectivity
- OnPrem connectivity
- Traffic filtering
- Routing

**Key Points**
- Primary building block for Azure networking
- Private network in azure based on address space prefix
- Create subnets in your VNet with your IP ranges
- Bring your own DNS or use Azure-provided DNS
- Choose to connect the network to onPrem or the Internet

*Note: look at the demo again and study the script/automation of deploying a VNet*

## Hybrid connectivity options

### Site-to-Site (S2S)
![Site-to-Site](https://s3.amazonaws.com/algamthe.dev/images/Site2SiteOverview.png "Site-to-Site")
- S2S VPN gateway connection is a connection over IPSec/IKE (IKEv1 or v2) VPN tunnel
- Requires a VPN device in an enterprise datacenter that has a public IP address assigned to it
- Must **not** be located behind a NAT
- S2S connections can be used for cross-premises and hybrid configuratoins  

### Point-to-Site (P2P)
![Point-to-Site](https://s3.amazonaws.com/algamthe.dev/images/Point2Site.png "Point-to-Site")
- Secure connection from an individual computer. Greate for remote workers.
- No need for VPN device or public IP. Connect whereever user has Internet connection
- Supports OSes: Win 7,8,8.1 (32/64bit),10. Win Server 2008 R2,2012,2012 R2 64 bit
- Throughput up to 100Mbps (depending on Internet)
- Doesn't scale easily, so only useful for few workstations

#### VPN Gateway SKUs
| SKU | S2S/VNet-to-VNet tunnels | P2S connections | Aggregate throughput benchmark
| ----------- | ----------- | ----------- | ----------- |
| VpnGw1 | Max. 30 | Max. 128 | 650Mbps |
| VpnGw2 | Max. 30 | Max. 128 | 1Gbps |
| VpnGw3 | Max. 30 | Max. 128 | 1.25Gbps |
| Basic | Max. 10 | Max. 128 | 100Mbps |

#### VPN Gateway Recommendations
|Workload | SKUs |
| ----------- | ----------- |
| Production, critical workload | VpnGw1,VpnGw2,VpnGw3 |
| Dev-test or proof of concept| Basic |


|SKU | Features |
| ----------- | ----------- |
| Basic | **Route-based VPN**: 10 tunnels with P2S;<br>no RADIUS auth for P2S;<br>no IKEv2 for P2S<br>**Policy-based VPN**: (IKEv1): 1 tunnel no P2S |
| VpnGw1,VpnGw2,VpnGw3 | **Route-based VPN**: up to 30 tunnels(*),P2S,<br>BGP,active-active, custom IPSec/IKE policy<br>ExpressRoute/VPN co-exsitence |

[More about VPN gateways here](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways)

### ExpressRoute
![ExpressRoute](https://docs.microsoft.com/en-us/azure/expressroute/media/expressroute-introduction/expressroute-connection-overview.png "ExpressRoute")

[More about ExpressRoute here](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-introduction)

![ExpressRoute connectivity models](https://docs.microsoft.com/en-us/azure/expressroute/media/expressroute-connectivity-models/expressroute-connectivity-models-diagram.png "ExpressRoute connectivity models")

[More about ExpressRoute connectivity models](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models)

#### Benefits of ExpressRoute
- Layer 3 connectivity: between your onPrem and Microsoft through a connectivity provider.<br>Can be from any-to-any (IPVPN) network, point-to-point Ethernet connection,<br> or through a virtual cross-connection via an Ethernet exchange.
- Connectivity in all regions in a given geopolitical region towards Microsoft cloud.
- Global connectivity towards Microsoft cloud with the premium add-on
- Dynamic routing between your network and Microsoft over industry standard protocols (BGP)
- Built-in redunduncy in every peering location for higher reliability.

#### Provisioning ExpressRoute
![ExpressRoute Provisioning workflow](https://docs.microsoft.com/en-us/azure/expressroute/media/expressroute-workflows/expressroute-circuit-workflow.png "ExpressRoute Provisioning workflow")

[More about ExpressRoute workflow](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-workflows)

Make sure you have the following pieces of information
![Required information for ExpressRoute Provisioning workflow](https://docs.microsoft.com/en-us/azure/expressroute/media/expressroute-workflows/routing-workflow.png "Required information for ExpressRoute Provisioning workflow")

#### Unlimited vs. Metered
|Unlimited | Metered |
| ----------- | ----------- |
| Speeds from 50Mbps to 10Gbps | Speeds from 50Mbps to 10Gbps |
| Unlimited **inbound** data transfer | Unlimited **inbound** data transfer |
| Unlimited **outbound** data transfer| Outbound data transfer charged at rate/Gb |
| Higher monthly fee | Lower monthly fee |

#### Express considerations
- Understand the models
  - Differences between unlimited and metered data
  - Understand what model to use to accelerate adoption
  - Understand differences in available port speeds, locations and approach
  - Understand the limits that drive additional circuits

- Understand the providers
  - Each offer a different experience based on ecosystem and capabilities
  - Some provide complete solutions and management
- Understand the costs
  - Connection costs can be broken out by the service connection costs (Azure)<br>and the authorized carrier costs(telco partner).
  - Unlike other azure services, look beyond the pricing calculator.

## Azure Load Balancers

### Load balancer 
Most common, works at the transport layer/layer 4.<br>Provides network level distribution to resources located in the same datacenter.
- Layer 4 
- Basic and Standard (preview) SKUs <-- review any SKUs
- Service monitoring (allows to probe the health of VM behind it)
- Automatic reconfiguration (i.e. when adding new webserver instances)
- Hash based distribution. This is how it distributes its traffic.<br>Has a 5 tuple hash of the following
  - Source IP
  - Source Port
  - Destination IP
  - Destination Port
  - Protocol Type
  Also has session stickiness
- Internal (e.g. infront of 2 DB instances), Public (e.g. infront of webservers) and multi-tier (mix of internal and public) options.
### Application gateway
workks at layer 7/app layer. Also acts as a reverse proxy
- Layer 7 load balancer
- Cookie based session affinity
- SSL offload
- End2End SSL (terminate SSL at the app gateway, apply routing rules to the traffic, then re-encrypting it again)
- WAF
- URL based content routing
- Requires its own subnet before you deploy it
  
**App gateway sizes (approximate)**

|Page response | Small | Medium | Large |
| ----------- |----------- | ----------- |----------- |
| 6K | 7.5Mbps | 13Mbps | 50Mbps |
| 100K | 35Mbps | 100Mbps | 200Mbps |
  
### Traffic manager (global scale, globally available end points. works at the DNS level)

### Comparison
|Service | Azure load balancer | App gateway | Traffic manager |
| ----------- | ----------- | ----------- | ----------- |
| Technology | Transport layer (layer 4) | Application layer (layer 7) | DNS-level |
| Application Protocols<br>Supported| Any | HTTP(s) and websockets | Any (HTTP endpoint is needed for endpoint monitoring)|
| Endpoints | Azure VMs, cloud service<br>role instances | Any Azure internal IP address,<br>public IP address<br>Azure VM,<br>or Azure cloud service | Azure VMs, cloud services,<br>Azure web apps, external endpoints |
| VNet | Can be used for both Internet<br> and internal (VNet) apps | Can be used for both Internet<br> and internal (VNet) apps | Only supports Internet facing apps |
| Endpoint monitoring | via probes | via probes | via HTTP(s) GET |

## CDN
A content delivery network (CDN) is a distributed network of servers that can efficiently deliver web content to users. CDNs store cached content on edge servers in point-of-presence (POP) locations that are close to end users, to minimize latency.

[More about Azure CDN](https://docs.microsoft.com/en-us/azure/cdn/cdn-overview)

### Offerings
- Standard Akamai
- Standard Verizon
- Premium Verizon

![CDN Offerings](https://s3.amazonaws.com/algamthe.dev/images/AzureCDNOfferings.png "CDN Offerings")

### Features
- Dynamic site acceleration
- CDN caching rules
- HTTPS custom domain support
- Azure diagnostic logs
- File compression
- Geo-filtering
- Video streaming optimization
- Large file optimization
- URL redirect/rewrite
- Mobile device rules

[MUST READ CDN FEATURES](https://docs.microsoft.com/en-us/azure/cdn/cdn-features)

### Benefits
- Better performance and improved user experience for end users, especially when using applications in which multiple round-trips are required to load content.
- Large scaling to better handle instantaneous high loads, such as the start of a product launch event.
- Distribution of user requests and serving of content directly from edge servers so that less traffic is sent to the origin server.

### How does it work?

- A user (Alice) requests a file (also called an asset) by using a URL with a special domain name, such as <endpointname>.azureedge.net. This name can be an endpoint hostname or a custom domain. The DNS routes the request to the best performing POP location, which is usually the POP that is geographically closest to the user.

- If no edge servers in the POP have the file in their cache, the POP requests the file from the origin server. The origin server can be an Azure Web App, Azure Cloud Service, Azure Storage account, or any publicly accessible web server.

- The origin server returns the file to an edge server in the POP.

- An edge server in the POP caches the file and returns the file to the original requestor (Alice). The file remains cached on the edge server in the POP until the time-to-live (TTL) specified by its HTTP headers expires. If the origin server didn't specify a TTL, the default TTL is seven days.

- Additional users can then request the same file by using the same URL that Alice used, and can also be directed to the same POP.

- If the TTL for the file hasn't expired, the POP edge server returns the file directly from the cache. This process results in a faster, more responsive user experience.

### Limitations
- The number of CDN profiles that can be created.
- The number of endpoints that can be created in a CDN profile.
- The number of custom domains that can be mapped to an endpoint.

# AZURE CORE SERVICES: DATA AND STORAGE SERVICES

## Types of Data

### Structured Data
- Adheres to a schema
- All the data has the same field or properties
- Stored in a database table with rows and columns
- Relies on keys to indicate how one row<br>in a table relates to another row in another table
- Referred to as relational data

### Semi Structured Data
- Doesn't fit into tables/rows/columns
- Uses tags/keys to organize and provide a heirarchy
- Referred to as NoSQL or non-relational data

### Unstructure Data
- No designated structure
- No restrictions on what type of data it can hold
- Example, blob can hold PDF/JPEG/JSON/Videos/etc
- Enterprises struggling to manage and gain insight<br>from this data


## Azure SQL
- Relational DB as a service
- Latest stable version of MSSQL
- Either create new or migrate using<br>
Microsoft Data Migration Assistant

### Features
- Predictable performance: Measure in Database Throughput Units (DTU)
- High compatibility: Supports existing SQL clients<br>via tubular database stream (TDS) endpoint
- Simplified Management: Icludes SQL server specific Azure tools
  
### Database tiers
|Basic | Standard | Premium |
| ----------- | ----------- | ----------- |
| Small DB with<br>single concurrent user| Medium sized DB that<br>must support multi-concurrent<br>connections | Large DB that must<br>a large number of concurrent<br>connections & operations |
| - Small DBs<br>- Single active operation<br>- Dev/Test<br>- Small scale apps<br>- 5 DTU| - Good for cloud apps<br>- Multiple operations<br>- Workgroup or web apps<br>- 10-100 DTU | - High txn volumes<br>- Large number of users<br>- Multiple operations<br>- Mission critical apps<br>- 100-800 DTU |

### NEW - Managed Azure SQL Instances
- Managed SQL servers
- More compatible with legacy workloads

### rd party DBs - Managed (MySQL/PostgreSQL)
- Managed DB options
  - built-in HA (no additional cost)
  - Predictable performance
  - Pay as you go
  - Auto scaling
  - Encryption (in motion/at rest)
  - Auto backups with point in time restore (upto 35 days)
  - Enterprise grade security and compliance

### rd party DBs - NON Managed (ClearDB/etc)
- Non managed options
  - Win Azure VM hosting MySQL
  - Linux Azure VM hosting MySQL
  - ClearDB offering managed MySQL instance

## Cosmos DB
- Globally distributed database service
- Supports schema-less data
- Used to build highly available responsive<br>always-on apps with constantly changing data

**Example**
Devs frequently updating catalog ---> online course catalog ---> Cosmos DB <--- Global users

[More on Azure Cosmos DB here](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction)

### Azure Cosmos DB topology

![Azure Cosmos DB Topology](https://docs.microsoft.com/en-us/azure/cosmos-db/media/distribute-data-globally/deployment-topology.png "Azure Cosmos DB Topolgy")

[More on Azure Cosmos DB topology](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally)

### Azure Cosmos DB features

Can access via following APIs

- Document DB (SQL) API
- MongoDB API
- Graph (Gremplin) API
- Tables (Key/Value) API

Automatically partitioned for
- Performance
- Storage capacity

**MUST READ MORE**

## Azure Storage
### Azure blob storage
- Unstructured storage for storing objects
- Store images/videos/files of any type
- Uses cases:
  - Streaming
  - Backup/DR
  - Archive

### Azure file services (SMB file storage)

- Easy way to create file shares
- Supports SMB 2.1 (unsecured) and 3.0 (secured)
- Mountable on Win/Linux/OS X
- Azure file sync can be utilized to<br>sync onPrem file servers with Azure files

### Azure table storage
- NoSQL key/value store
- Schemaless design
- Structured/Unstructured data
- Access using Odata protocol and LINQ queries<br>WCF data service .net libraries

[Azure Table Storage Overview](https://docs.microsoft.com/en-us/azure/cosmos-db/table-storage-overview)


![Table Storage Components](https://docs.microsoft.com/en-us/azure/includes/media/storage-table-concepts-include/table1.png "Table Storage Components")

[Understanding Table Service Data Model](https://docs.microsoft.com/en-us/rest/api/storageservices/Understanding-the-Table-Service-Data-Model)

### Azure Queue Storage

- Provides reliable mechanism for storage and delivery of messages
- Single queue message can be 64Kb and a queue can contain<br>millions of messages, up to the total capcity limit of a storage account

[Azure Queue Storage Overview](https://docs.microsoft.com/en-us/azure/storage/queues/storage-queues-introduction)

![Queue Storage concepts](https://docs.microsoft.com/en-us/azure/storage/queues/media/storage-queues-introduction/queue1.png "Queue Storage concepts")

## VM Disk Storage

- Standard HDD
  - backed by traditional HDDs
  - most cost effective
  - throughput based on VM
  - IOPS based on VM
- Standard SSD
  - backed by SSD drives
  - recommended for most workloads
  - max through put 500MB/s per disk
  - max IOPS 2000 IOPS per disk
- Premium Storage
  - backed by SSD drives
  - higher performance, lower latency
  - max through put 750MB/s per disk
  - max IOPS 7500 IOPS per disk

### Managed disks - Standard storage sizes
| Type | S4 | S6 | S10 | S20 | S30 | S40 | S50|
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |----------- |----------- |
|Disk Size | 32 | 64 | 128 | 512 | 1024 | 2048 | 4095|

Note: IOPS and through put depend on the performance of the VM and are not provisioned.

### Managed disks - Standard SSD storage sizes
| Type | E4 | E6 | E10 | E15 | E20 | E30 | E40| E50|
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |----------- |----------- | ----------- |
|Disk Size | 32 | 64 | 128 | 256 | 512 | 1024 | 2048 | 4095|
|MAX IOPS | 120 | 240 | 500 | 500 | 500 | 500 | 500 | 500 |
|MAX throughput | 25 MB/s | 50 MB/s | 60 MB/s | 60 MB/s | 60 MB/s | 60 MB/s | 60 MB/s | 60 MB/s|

### Managed disks - Premium SSD storage sizes
| Type | P4 | P6 | P10 | P15 | P20 | P30 | P40| P50|
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |----------- |----------- | ----------- |
|Disk Size | 32 | 64 | 128 | 256 | 512 | 1024 | 2048 | 4095|
|MAX IOPS | 120 | 240 | 500 | 1100 | 2300 | 5000 | 7500 | 7500 |
|MAX throughput | 25 MB/s | 50 MB/s | 100 MB/s | 125 MB/s | 150 MB/s | 200 MB/s | 250 MB/s | 250 MB/s|

### Ultra SSDs storage sizes
| Type | P4 | P6 | P10 | P15 | P20 | P30 | P40| P50|
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |----------- |----------- | ----------- |
|Disk Size | 4 | 8 | 16 | 32 | 64 | 128 | 256 | 512|
|MAX IOPS | 1200 | 2400 | 4800 | 9600 | 19200 | 38400 | 7600 | 80000 |
|MAX throughput | 300 MB/s | 600 MB/s | 1200 MB/s | 2000 MB/s | 2000 MB/s | 2000 MB/s | 2000 MB/s | 2000 MB/s|

Note: 1,024 - 65,536 sizes also available increasing in incrememnts of 1 TiB<br>IOPs capped at 160,000 and throughput capped at 2,000<br>Read more about it as it is GA on August 2019

### VM LIMITS
> Make sure the VM you have can handle the bandwidth of the storage you selected (throughput and IOPS)

### Managed vs. Un-Managed
| Managed | Unmanaged |
| ----------- | ----------- |
| DIY option| Simplest option |
| Management overhead<br>20,000 IOPS/storage account limit| Lower management overhead<br>as Azure manages the storage accounts|
| Supports all replication modes<br>(LRS, ZRS, GRS, RA-GRS)| Only LRS replication<br>mode currently supported |

### Replication Options
**MUST READ**

| Type | Description |
| ----------- | ----------- |
| Locally replicated storage<br>(LRS)| Replicated 3 times within a storage scale unit.<br>This is a collection of racks of storage nodes hosted in a datacenter<br>in the same region as your storage account |
| Zone replicated storage<br>(ZRS)| Replicated 3 time across 1 or 2 datacenters in addition<br>to storing 3 replicas similar to LRS.<br>Data stored in ZRS is durable even in the event<br>that the primary datacenter is unavailable or unrecoverable|
| Geographically replicated storage<br>(GRS)| Replicates your data to a second region<br>that is 100s miles away from your primary region.<br>Data is durable even in the event of complete region outage.|
| Read-Only geographically<br>replicated storage (RA-GRS)| Same replication as GRS but also provides<br>read only access to the data in the other region. | 

**Comparison**
| Replication Strategy | LRS | ZRS | GRS | RA-GRS|
| ----------- | ----------- | ----------- | ----------- | ----------- |
| Data is replicated across<br>multiple datacenters? | No | Yes | Yes | Yes |
| Data can be read from<br>a secondary location *and* the primary location? | No | No | No | Yes |
| Number of copies of data<br>maintained on separate nodes | 3 | 3 | 6 | 6 |

## Storage Account Overview

### 3 types
- General Purpose v1 (GPv1) - only allowed for blob storage
- Blob account
- General Purpose v2 (GPv2) - main type used when creating storage accounts in Azure<br>allows us to create everything (page/block/etc)

### Block Blob vs. Page Blob
| Block Blob Strategy | Page Blob |
| ----------- | ----------- |
| Ideal for storing text or binary files| Efficient for read/write ops |
| Single block blob can contain 50,000 blocks<br>up to 100MB each<br>total size of **4.75TB**| Used by Azure VMs|
| Append blobs are optimized for append ops (e.g. logging)| Up to **8TB** in size|

### Storage tiers
- Hot
  - high storage costs
  - lower access costs
- Cold
  - lower storage costs
  - higher access costs
  - Intended for data that will remain cool for 30days or more
- Archive
  - lowest storage costs
  - highest retrieval costs
  - when a blob is in storage<br>it is offline and cannot be read

Implement lifecycle (same as AWS S3) concepts

### Choosing between blobs, files, disks
| Type | Benefits |
| ----------- | ----------- |
| Blobs | Access application data from anywhere<br>Large amount of objects to store (images/vids/etc) |
| Files | Access across multiple machines<br>Jumpbox scenarios for shared dev purposes|
| Disks | Do not need access outside of VM<br>Lift and shift of machines from onPrem<br>Disk expansion for app installations|


# AZURE CORE SERVICES: OTHER SERVICES

## IoT Services (Azure IoT)
- Collection of Microsoft managed cloud services focused<br>on connecting, monitoring, and controlling IoT assets
- IoT solutions are made up of 1 or more IoT devices<br>and 1 or more back end services running in the cloud

## Examples
- Water sensors for farming
- Pressure sensors on a remote oil pump
- Temp and humidity sensors in HVAC unit

## IoT Services in Azure
- IoT central: SaaS solution to connect and manage your devices
- IoT hub: The service needed to facilitate messaging between your IoT apps and devices
- IoT solution accelerators: Complete ready to deploy solutions that implement common IoT scenarios

Note: be able to describe and understand IoT and where it fits in from a high level for the exam.

## Big Data Solutions

![Big Data Solutions](https://s3.amazonaws.com/algamthe.dev/images/BigDataSolutions.png "Big Data Solutions")

For ingestion: there is Azure data factory

Components
- SQL data warehouse
  - key component of a big data solution
  - cloud based enterprise data warehouse (EDW) that<br>uses massive parallel processing (MPP)<br>to run complex queries across petabytes of data.
  - Stores data in relational tables to reduce storage costs and improve performance
- HDInsight
  - Fully managed open source analytic service for enterprises
  - Uses popular frameworks like Hadoop, Spark, Hive, etc
  - Scenarios
    - Batch processing (ETL)
    - Data warehousing
- Data lake analytics
  - on-demand job service that simplifies big data
  - pay only for the job when it is running
  - write queries to transform data and extract insights

**Which service do I use?**

|If you want... | Use this|
|---------------| --------|
|A fully managed, elastic data warehouse with security at every level of scale at no extra cost | SQL Data Warehouse|
| A fully managed, fast, easy and collaborative Apache® SparkTM based analytics platform optimized for Azure| Azure data bricks|
| A fully managed cloud Hadoop and Spark service backed by 99.9% SLA for your enterprise | HDInsight |
| A data integration service to orchestrate and automate data movement and transformation| Data Factory|
| Open and elastic AI development spanning the cloud and the edge | Machine learning |
| Real-time data stream processing from millions of IoT devices | Azure Stream Analytics |
| A fully managed on-demand pay-per-job analytics service with enterprise-grade security, auditing, and support | Data Lake Analytics |
| Enterprise grade analytics engine as a service | Azure Analysis Services |
| A hyper-scale telemetry ingestion service that collects, transforms, and stores millions of events | Event Hubs |
| Fast and highly scalable data exploration service | Azure Data Explorer|

## Machine Learning

- Machine learning is a data science technique that allows computers to use existing data to forecast future behaviors, outcomes, and trends. By using machine learning, computers learn without being explicitly programmed.
- Azure Machine Learning service provides a cloud-based environment you can use to **prep data, train, test, deploy, manage, and track machine learning models**.
- Automated ML and DevOps capabilities

### Machine learning Studio
- Collaborative, drag-and-drop visual workspace where you can build, test, and deploy machine learning solutions without needing to write code.
- Uses prebuilt and preconfigured machine learning algorithms and data-handling modules as well as a proprietary compute platform

# IDENTITY

## Accounts and Subs Overview

Azure Account Hierarchy

Azure enterprise --> ea.azure.com<br>
        | (1-Many)<br> 
        V<br> 
Departments<br>
        | (1-Many)<br>
        V<br>
Accounts        --> account.azure.com<br>
        | (1-Many)<br>
        V<br>
Subscriptions   --> portal.azure.com<br>
        |<br>
        V<br>
Resource Groups<br>
        |<br>
        V<br>        
Resources<br>    


## Domain Services

## Azure AD

## RBAC

## Azure Policy

## Resource Locks

# COMPLIANCE, SECURITY AND COST

## Compliance and Security

## Security Center

## Support Plans