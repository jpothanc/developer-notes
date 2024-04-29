# Azure Virtual Machines (VMs)

## Overview

Azure Virtual Machines offer the flexibility of virtualization without the need to buy and maintain the physical hardware that runs it. You can configure, manage, and maintain the OS and software.

| Service                                  | Key Features                                                                                           | Common Use Cases                                                                                                                                                                                            |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Azure Virtual Machines**               | - Full OS control<br>- Rapid provisioning with VM images<br>- Scalable with availability sets          | - Development & Testing<br>- Disaster Recovery                                                                                                                                                              |
| **Azure Virtual Desktop**                | - Accessible anywhere<br>- Enhanced security with multi-factor authentication                          | - Remote work solutions<br>- Multi-user environments                                                                                                                                                        |
| **Azure Containers**                     | - Lightweight and scalable<br>- Supports Kubernetes with AKS                                           | - Microservices<br>- Event-driven applications                                                                                                                                                              |
| **Azure Functions**                      | - Serverless, event-driven compute<br>- Scales automatically                                           | - Respond to events<br>- Integrate systems                                                                                                                                                                  |
| **Azure App Service**                    | - Supports multiple languages and frameworks<br>- Integrated deployment options                        | - Web apps<br>- REST APIs<br>- Mobile backends                                                                                                                                                              |
| **Azure Networking**                     | - Virtual Networks, VPN Gateway, ExpressRoute<br>- Load balancing and peering                          | - Extend datacenters<br>- Connect cloud resources                                                                                                                                                           |
| **Azure DNS**                            | - Anycast networking<br>- Integrated with Azure management                                             | - Manage domain name system settings                                                                                                                                                                        |
| **Azure Virtual Networking**             | Enables Azure resources like VMs, web apps, and databases to communicate within a secured environment. | - **Isolation and segmentation**: Multiple virtual networks.<br>- **Communication**: Between Azure resources, and on-premises networks.<br>- **Routing and filtering**: Customizable network traffic rules. |
| **Azure Virtual Private Networks (VPN)** | Uses VPN gateways to connect disparate networks securely over the internet.                            | - **Site-to-site connections**: Link entire networks to Azure.<br>- **Point-to-site connections**: Connect individual devices to Azure.<br>- **Encryption**: Secure data transfer across the internet.      |
| **Azure ExpressRoute**                   | Provides a private connection to Azure services, bypassing the public internet.                        | - **Private connectivity**: Direct connection to Azure without going through the public internet.<br>- **High-speed connections**: Up to 100 Gbps.<br>- **Global reach**: Connect facilities globally.      |
| **Azure DNS**                            | Manages DNS names and records using Azure infrastructure.                                              | - **High availability**: Uses Azure's global network.<br>- **Security features**: Includes Azure RBAC and activity logs.<br>- **Integration**: With Azure management tools.                                 |

## Key Features

- **Control**: Full control over the operating system for custom software and configurations.
- **Image Provisioning**: Rapid deployment using pre-configured or custom images.
- **Scalability**:
  - Single VMs for small tasks.
  - VM scale sets for high availability, automatic scaling, and load balancing.
- **Availability**:
  - **Scale Sets**: Manage a group of load-balanced VMs.
  - **Availability Sets**: Improve fault tolerance by distributing VMs across fault and update domains.

## Use Cases

- **Development and Testing**: Temporary, isolated environments for testing new applications.
- **Running Applications**: Hosting applications that can scale based on demand.
- **Datacenter Extension**: Extending on-premises datacenters to the cloud for more flexible resource management.
- **Disaster Recovery**: Quick provisioning during a disaster recovery to maintain business continuity.

## Pricing

- You only pay for the VM instances you use, and there's no additional cost for using availability sets.

# Azure Virtual Desktop

## Overview

Azure Virtual Desktop is a desktop and app virtualization service that runs on the cloud.

## Key Features

- **Accessibility**: Access from anywhere, on any device, providing a Windows desktop environment.
- **Security**:
  - Centralized security management with Microsoft Entra ID.
  - Multi-factor authentication and granular role-based access controls (RBAC).
- **Multi-session Windows 10/11**: Supports multiple users on a single VM, reducing costs and resource usage.

# Azure Containers

## Overview

Azure provides containerized environments which are lightweight, provide a consistent development environment, and are easy to scale.

## Services

- **Azure Container Instances (ACI)**: Easily run containers on Azure without managing servers.
- **Azure Kubernetes Service (AKS)**: Manage complex containerized applications with a Kubernetes-based orchestration service.
- **Azure Container Apps**: A serverless container service that supports agile development.

## Use Cases

- **Microservices**: Run each component in its own container for better agility and scale.
- **Event-driven Applications**: Quickly deploy and scale based on demand without over-provisioning resources.

# Azure Functions

## Overview

Azure Functions is a serverless compute service that runs code in response to events and automatically manages the compute resources.

## Key Features

- **Event-driven**: Triggers from Azure services, third-party services, or on-premises systems.
- **Scaling**: Automatically scales based on demand, and you only pay for the compute time you consume.
- **Stateless and Stateful**: Supports stateless functions and durable functions for stateful operations.

# Azure App Service

## Overview

Platform as a Service (PaaS) offering for hosting web apps, REST APIs, and mobile back ends.

## Key Features

- **Multi-language Support**: Supports .NET, Java, Ruby, Node.js, PHP, Python.
- **Integration**: Continuous deployment from GitHub, Azure DevOps, and any Git repo.
- **Scaling**: High availability with auto-scaling capabilities.

## App Types

- **Web Apps**
- **API Apps**
- **WebJobs**: Background service running in the same context as your web app.
- **Mobile Apps**: Backend services for mobile applications.

# Azure Networking

## Services

- **Virtual Networks**: Provision private networks, optionally connecting to on-premises datacenters.
- **Load Balancing**: Distribute network traffic across multiple loads to ensure high availability and reliability.
- **VPN Gateway**: Connect your on-premises infrastructure to Azure through a private connection.

## Key Concepts

- **Peering**: Connect multiple virtual networks to each other, enabling resources to communicate across Azure regions.
- **ExpressRoute**: Extend on-premises networks into the Azure cloud over a private connection facilitated by a connectivity provider.

# Azure DNS

## Overview

Azure DNS provides name resolution using Microsoft Azure infrastructure.

## Key Features

- **Anycast Network**: Every DNS query is answered by the nearest available DNS server for performance and reliability.
- **Integration**: Seamlessly manage DNS alongside your Azure services.
- **Security**: Leverage Azure's security features to manage and protect your DNS data.

## Azure Virtual Networking

Azure Virtual Networking allows Azure resources like VMs, web apps, and databases to communicate securely both internally and externally. It can be viewed as an extension of your on-premises network.

### Key Features

- **Isolation and Segmentation**: Create multiple isolated virtual networks within Azure for enhanced security and organization.
- **Internet Communications**: Resources can communicate over the internet by assigning public IP addresses or using load balancers.
- **Communication with Azure Resources**: Facilitates secure communication between Azure resources using either direct links or service endpoints.
- **On-premises Connectivity**: Connect your on-site infrastructure to Azure with VPNs or ExpressRoute for a seamless network experience across environments.
- **Traffic Routing and Filtering**: Customize how network traffic is routed and filtered to optimize performance and security.
- **Network Peering**: Connect multiple virtual networks directly to allow resources to interact as if they were part of the same network.

## Azure Virtual Private Networks (VPN)

Azure VPNs utilize encrypted tunnels to securely connect different networks over the internet, ideal for linking private networks securely.

### Key Features

- **VPN Gateways**: Deployed within Azure virtual networks to manage all VPN connections.
- **Connection Types**:
  - **Site-to-Site**: Connects entire networks to Azure.
  - **Point-to-Site**: Connects individual devices directly to Azure.
  - **Network-to-Network**: Connects different Azure virtual networks.
- **High Availability Configurations**: Supports configurations like active/standby and active/active to ensure continuous connectivity.
- **ExpressRoute Failover**: Use VPN as a failover for ExpressRoute to maintain connectivity even if the primary connection fails.

## Azure ExpressRoute

ExpressRoute provides a private connection to Microsoft Azure and other Microsoft cloud services, bypassing the public internet to offer more reliability, faster speeds, and lower latencies.

### Key Features

- **Direct Connection**: Connect directly to Azure from your premises without transiting the internet.
- **Global Reach**: Connect your different geographical locations via Azure with ExpressRoute Global Reach.
- **Dynamic Routing**: Uses BGP for automatic routing between your on-premises networks and Azure services.
- **Built-in Redundancy**: Ensures high availability and reliability through redundant devices in every peering location.

## Azure DNS

Azure DNS offers a hosting service for DNS domains that integrates seamlessly with your other Azure services, using the same billing, support, and management tools.

### Key Features

- **High Availability and Performance**: Utilizes Azure’s global network of DNS servers to ensure quick DNS query responses and high availability.
- **Security Controls**: Features like Azure role-based access control (RBAC) and activity logs enhance security.
- **Ease of Use**: Manage DNS records using familiar Azure tools, with integration for automated management via APIs.
- **Support for Private Domains**: Manage and resolve domain names in your private virtual networks with Azure.
- **Alias Records**: Automatically updates DNS records when the IP address of an Azure resource changes.
