## 1-Cloud computing

---

---

| Term                            | Description                                                                                                                        |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Cloud Computing**             | The delivery of computing services over the internet, including virtual machines, storage, databases, networking, IoT, ML, and AI. |
| **Advantages**                  | Enables rapid scaling of IT infrastructure without the constraints of physical data centers.                                       |
| **Shared Responsibility Model** |                                                                                                                                    |
| Traditional Datacenter          | Complete organizational responsibility for physical and software management.                                                       |
| Cloud Computing                 | Responsibilities are shared:                                                                                                       |
|                                 | - Cloud Provider: Manages physical security, power, cooling, and network connectivity.                                             |
|                                 | - Consumer: Responsible for data, access security, and managing application settings.                                              |
|                                 | - Service-Specific: Responsibility varies by service model (IaaS, PaaS, SaaS):                                                     |
|                                 | - IaaS: Consumers manage applications, data, runtime, middleware, and OS.                                                          |
|                                 | - PaaS: Consumers manage applications and data.                                                                                    |
|                                 | - SaaS: Most responsibilities are handled by the cloud provider.                                                                   |
| **Cloud Models**                |                                                                                                                                    |
| Private Cloud                   | Operated solely for a single organization, offering control over data and security but at higher costs.                            |
| Public Cloud                    | Maintained by third-party providers, accessible to anyone, offering cost efficiency and scalability.                               |
| Hybrid Cloud                    | Combines private and public clouds, offering flexibility and scalability.                                                          |
| Multi-Cloud                     | Uses multiple public cloud services, allowing for diverse and resilient deployments.                                               |
| **Cloud Technologies**          |                                                                                                                                    |
| Azure Arc                       | Manages and governs resources across multiple clouds.                                                                              |
| Azure VMware Solution           | Integrates VMware workloads with Azure services, facilitating migration to hybrid and public clouds.                               |
| **Consumption-Based Model**     |                                                                                                                                    |
| **Financial Aspects**           |                                                                                                                                    |
| CapEx                           | Upfront spending on physical infrastructure.                                                                                       |
| OpEx                            | Operational spending, including cloud services which are consumption-based.                                                        |
| **Benefits**                    |                                                                                                                                    |
|                                 | - Flexible and efficient resource utilization.                                                                                     |
|                                 | - Pay only for resources used.                                                                                                     |
|                                 | - Scalable according to business needs.                                                                                            |
| **Pricing Models**              |                                                                                                                                    |
| Pay-as-you-go                   | Charges based on actual usage, offering flexibility and operational cost management.                                               |

---

---

# Cloud Concepts

| Concept           | Description                                                                                                                                                                                                           |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Agility           | Refers to the ability of cloud systems to quickly adapt to changes in technology and business requirements, enabling rapid development and deployment of new applications.                                            |
| Scalability       | The capability of a system to handle a growing amount of work, or its potential to accommodate growth. Both vertical (adding resources) and horizontal (adding instances).                                            |
| Elasticity        | The ability of a system to dynamically scale resources both up and down as needed. Elastic systems can automatically adjust to temporary changes in usage without human intervention.                                 |
| Fault Tolerance   | The ability of a system to continue operating properly in the event of the failure of some of its components. This is often achieved through redundancy.                                                              |
| High Availability | The ability of a system to remain operational and accessible for a very high percentage of time, minimizing downtime even during failures or maintenance periods.                                                     |
| Disaster Recovery | Involves policies, tools, and procedures to enable the recovery or continuation of vital technology infrastructure and systems following a natural or human-induced disaster.                                         |
| Data Redundancy   | The duplication of data, or the ability to store data in multiple locations to ensure reliability and availability during instances of hardware failure or other issues.                                              |
| Multi-Tenancy     | The ability of a cloud service to serve multiple customers (tenants) using the same infrastructure without tenants being able to access each other's data.                                                            |
| Resource Pooling  | The provider's computing resources are pooled to serve multiple consumers using a multi-tenant model, with different physical and virtual resources dynamically assigned and reassigned according to consumer demand. |

---

---

## 3-Cloud service types

| Service Model                          | Description                                                                                                                      | Responsibilities                                                                                                                                       | Common Scenarios                                                                                                                                                                |
| -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **IaaS** (Infrastructure as a Service) | Provides high control over cloud resources by offering the hardware infrastructure such as servers, storage, and networking.     | **Provider**: Manages physical infrastructure and basic networking.<br>**You**: Manage operating systems, applications, runtime, data, and middleware. | - Lift-and-shift migration: Migrate existing on-prem applications without modifications.<br>- Testing and Development: Quickly set up and dismantle environments.               |
| **PaaS** (Platform as a Service)       | Offers a managed hosting environment where users can create and run applications without managing the underlying infrastructure. | **Provider**: Manages infrastructure, operating systems, and platform-level middleware.<br>**You**: Handle applications and data.                      | - Development Framework: Build applications using built-in software components.<br>- Analytics/Business Intelligence: Use tools to analyze data and predict outcomes.           |
| **SaaS** (Software as a Service)       | Provides fully functional applications on a subscription basis.                                                                  | **Provider**: Manages everything from infrastructure to applications.<br>**You**: Responsible for data, user management, and device access.            | - Email and Messaging: Use cloud-based systems.<br>- Business Productivity: Applications for document creation, etc.<br>- Finance and Expense Tracking: Manage financial tasks. |

This table provides a concise and comparative view of the three main cloud service models, helping to clarify the distinctions and applications of each.

| Aspect                          | Description                                                                                                                                                     |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**                  | The delivery of computing services over the internet, including virtual machines, storage, databases, networking, IoT, ML, and AI.                              |
| **Advantages**                  | Enables rapid scaling of IT infrastructure without the constraints of physical data centers.                                                                    |
| **Shared Responsibility Model** |                                                                                                                                                                 |
| Traditional Datacenter          | Complete organizational responsibility for physical and software management.                                                                                    |
| Cloud Computing                 | Responsibilities are shared:                                                                                                                                    |
|                                 | - Cloud Provider: Manages physical security, power, cooling, and network connectivity.                                                                          |
|                                 | - Consumer: Responsible for data, access security, and managing application settings.                                                                           |
| **Service-Specific**            | Responsibility varies by service model (IaaS, PaaS, SaaS):                                                                                                      |
| IaaS                            | Consumers manage applications, data, runtime, middleware, and OS.                                                                                               |
| PaaS                            | Consumers manage applications and data.                                                                                                                         |
| SaaS                            | Most responsibilities are handled by the cloud provider.                                                                                                        |
| **Cloud Models**                |                                                                                                                                                                 |
| Private Cloud                   | Operated solely for a single organization, offering control over data and security but at higher costs.                                                         |
| Public Cloud                    | Maintained by third-party providers, accessible to anyone, offering cost efficiency and scalability.                                                            |
| Hybrid Cloud                    | Combines private and public clouds, offering flexibility and scalability.                                                                                       |
| Multi-Cloud                     | Uses multiple public cloud services, allowing for diverse and resilient deployments.                                                                            |
| **Cloud Technologies**          |                                                                                                                                                                 |
| Azure Arc                       | Manages and governs resources across multiple clouds.                                                                                                           |
| Azure VMware Solution           | Integrates VMware workloads with Azure services, facilitating migration to hybrid and public clouds.                                                            |
| **Consumption-Based Model**     |                                                                                                                                                                 |
| **Financial Aspects:**          |                                                                                                                                                                 |
| CapEx                           | Upfront spending on physical infrastructure.                                                                                                                    |
| OpEx                            | Operational spending, including cloud services which are consumption-based.                                                                                     |
| **Benefits:**                   |                                                                                                                                                                 |
|                                 | - Flexible and efficient resource utilization.                                                                                                                  |
|                                 | - Pay only for resources used.                                                                                                                                  |
|                                 | - Scalable according to business needs.                                                                                                                         |
| **Pricing Models**              |                                                                                                                                                                 |
| Pay-as-you-go                   | Charges based on actual usage, offering flexibility and operational cost management.                                                                            |
| **Overview**                    | This overview provides a foundational understanding of cloud computing, highlighting how resources are managed, deployed, and charged in the cloud environment. |

---

---

## 4-Core architectural components of Azure

| Section                                          | Description                                                                                                                                                                                  | Details                                                                                                                                                                                                                                                         |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **What is Microsoft Azure?**                     | A comprehensive cloud platform for building, managing, and deploying applications globally.                                                                                                  | Provides tools and frameworks for AI, machine learning, and more, addressing both current and future business challenges.                                                                                                                                       |
| **Key Offerings**                                | - **Limitless Innovation**: Advanced applications with AI.<br>- **Unified Management**: Integrated management of infrastructure.<br>- **Trusted Platform**: Secure and responsible platform. | Enables businesses to innovate with a focus on security and comprehensive management capabilities.                                                                                                                                                              |
| **Capabilities of Azure**                        | Diverse services including AI, machine learning, virtual machines, and dynamic storage solutions.                                                                                            | Over 100 versatile services aimed at enhancing user interaction through natural communication methods and managing large-scale data.                                                                                                                            |
| **Getting Started with Azure**                   | Necessary steps for using Azure, including accounts and free service options.                                                                                                                | - **Azure Accounts and Subscriptions**: Manage resources effectively.<br>- **Free Accounts**: Access to free services and credits.                                                                                                                              |
| **Azure Physical and Management Infrastructure** | Organized network of datacenters with robust support for resilience and redundancy.                                                                                                          | - **Datacenters and Regions**: Ensure global coverage and operational continuity.<br>- **Availability Zones and Region Pairs**: Enhance disaster recovery capabilities.                                                                                         |
| **Azure Hierarchical Structure**                 | Detailed breakdown from Azure account to individual resources.                                                                                                                               | - **Management Groups**: Manage policy across subscriptions.<br>- **Subscriptions**: Contain resource groups for billing and policy application.<br>- **Resource Groups**: Manage related resources together.<br>- **Resources**: Individual service instances. |
| **Usage Scenarios**                              | Demonstrates Azure's flexibility in supporting various operational needs.                                                                                                                    | Suitable for isolated environments for development, testing, security, and compliance across different organizational structures.                                                                                                                               |

---

---

## 5-Azure compute and networking services

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

---

---

## 6-Azure storage Services

| Azure Storage Service                            | Explanation                                                                                                          | Durability in Nines                                                                                                 |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Locally Redundant Storage (LRS)                  | Stores data within a single physical location in the data center to protect against hardware failures.               | 11 nines (suitable for non-critical data)                                                                           |
| Zone-Redundant Storage (ZRS)                     | Spreads data across multiple storage units in one or more data centers within a region.                              | 12 nines (good for critical regional data)                                                                          |
| Geo-Redundant Storage (GRS)                      | Replicates data to a secondary region that is hundreds of miles away from the primary region.                        | 16 nines (recommended for essential data needing geographic redundancy)                                             |
| Read-Access Geo-Redundant Storage (RA-GRS)       | Same as GRS, but provides read-only access to the data in the secondary location.                                    | 16 nines (plus read access from secondary, ideal for applications needing fast read access during regional outages) |
| Geo-Zone-Redundant Storage (GZRS)                | Combines the features of GRS and ZRS, replicating data across zones in the primary region and to a secondary region. | 16 nines (enhanced durability across zones and regions)                                                             |
| Read-Access Geo-Zone-Redundant Storage (RA-GZRS) | Same as GZRS, but with read-only access to the data in the secondary location.                                       | 16 nines (plus read access from secondary, best for critical applications requiring maximum availability)           |

---

---

### Storage Type

| Storage Type       | Description                                                                                                                                                               |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Blob Storage       | Ideal for storing large amounts of unstructured data such as text or binary data, often used for images, videos, documents, backups, and application data.                |
| File Storage       | Offers fully managed file shares in the cloud that can be accessed via the industry standard Server Message Block (SMB) protocol, suitable for enterprise applications.   |
| Queue Storage      | Provides cloud messaging between application components, enabling scalable and loosely coupled communication, often used for building decoupled architectures.            |
| Table Storage      | NoSQL datastore for structured data, capable of storing massive amounts of data for web applications, capable of handling flexible datasets with dynamic schemas.         |
| Disk Storage       | Persistent, high-performance managed block storage for Azure Virtual Machines, available in SSD and HDD formats, used as the OS disk or data disk for VMs.                |
| Azure Data Lake    | Scalable data lake storage for big data analytics solutions, capable of storing and analyzing massive amounts of structured and unstructured data with high throughput.   |
| Azure Backup       | Offers scalable, secure, and cost-effective offsite data protection for on-premises data and workloads, ensuring data resilience and disaster recovery capabilities.      |
| Azure Archive Blob | Provides ultra-low-cost, secure, and durable storage for rarely accessed data, suitable for long-term retention of backup data, archival data, and regulatory compliance. |

---

---

### Blob Storage Tier

| Storage Tier | Description                                                          |
| ------------ | -------------------------------------------------------------------- |
| Hot          | Optimized for frequently accessed data.                              |
| Cool         | Suitable for infrequently accessed data stored for at least 30 days. |
| Cold         | Designed for infrequently accessed data stored for at least 90 days. |
| Archive      | Intended for rarely accessed data stored for at least 180 days.      |

---

---

### Azure Migration Services

| Migration Service                | Description                                                                                                                                                                                   |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Azure Migrate                    | Offers a centralized hub to assess and migrate on-premises servers, databases, and applications to Azure, providing insights, right-sizing recommendations, and migration guidance.           |
| Azure Site Recovery              | Provides disaster recovery and migration capabilities for on-premises VMware, Hyper-V, and physical servers, enabling replication and failover to Azure with minimal downtime.                |
| Azure Database Migration Service | Simplifies database migration to Azure, supporting heterogeneous migrations of on-premises databases to Azure data platforms like Azure SQL Database and Azure Database for MySQL/PostgreSQL. |
| Azure Data Box                   | Offers secure and efficient data transfer to Azure, allowing large amounts of data to be shipped physically using ruggedized appliances, ideal for offline or limited-bandwidth scenarios.    |
| Azure Data Box Disk              | Provides a portable, SSD-based solution for offline data transfer to Azure, suitable for smaller data volumes with faster turnaround times compared to traditional data shipping methods.     |
| Azure Data Box Heavy             | Enables high-volume, offline data transfer to Azure using ruggedized, high-capacity storage appliances, offering a reliable and efficient method for migrating large datasets to the cloud.   |
| Azure Data Box Edge              | Combines edge compute capabilities with offline data transfer, allowing data preprocessing and analytics at the edge before securely transferring data to Azure for further processing.       |

---

---

### Azure Databox Use cases

| Use Case                                  | Description                                                                                                                                                                                                           |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Large-scale Data Migration                | Azure Data Box facilitates the migration of large volumes of data to Azure by providing ruggedized appliances for offline data transfer, offering a faster and more efficient method than online transfers.           |
| Limited Bandwidth Environments            | In scenarios where internet bandwidth is limited or unreliable, Azure Data Box provides a reliable solution for transferring data to Azure, allowing organizations to overcome connectivity challenges.               |
| Datacenter Migration                      | Organizations can use Azure Data Box to migrate data from on-premises datacenters to Azure, streamlining the transition to the cloud and minimizing downtime associated with online data transfers.                   |
| Offline Data Transfer                     | For environments with strict security or compliance requirements that restrict online data transfers, Azure Data Box offers an offline method for securely transferring data to Azure without internet access.        |
| Data Preprocessing at the Edge            | Azure Data Box Edge enables edge compute capabilities, allowing organizations to preprocess and analyze data at the edge before transferring it to Azure, optimizing data processing workflows.                       |
| Temporary Data Storage                    | Organizations can leverage Azure Data Box for temporary data storage during migration projects, providing a secure and scalable solution for storing data before it is transferred to Azure storage services.         |
| Media and Entertainment Workflows         | Azure Data Box is suitable for media and entertainment workflows that involve large video files, graphics, or other multimedia assets, enabling efficient transfer of content to Azure for processing and analysis.   |
| Backup and Disaster Recovery              | Using Azure Data Box for backup and disaster recovery purposes allows organizations to create offline backups of critical data, ensuring data availability and resilience against data loss or disasters.             |
| Remote or Offshore Locations              | In remote or offshore locations with limited connectivity to the Azure cloud, Azure Data Box offers a practical solution for transferring data, enabling organizations to overcome geographic and network challenges. |
| Data Migration for IoT and Edge Computing | Azure Data Box supports data migration for IoT and edge computing environments, facilitating the transfer of sensor data, telemetry, and other IoT-generated data to Azure for analysis and insights.                 |

---

---

### Azure File Movement Options

| Movement Option             | Description                                                                                                                                                                                           |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Azure Data Factory          | Azure Data Factory provides data integration and orchestration service for automating data movement and transformation. It supports various data sources and destinations, including Azure storage.   |
| Azure Data Box              | Azure Data Box offers ruggedized appliances for offline data transfer, allowing organizations to transfer large volumes of data securely to Azure storage, overcoming bandwidth limitations.          |
| AzCopy                      | AzCopy is a command-line utility for copying data to and from Azure storage. It supports high-performance data transfer with features like parallelism, resuming, and encryption.                     |
| Azure Storage Sync          | Azure Storage Sync enables bi-directional synchronization of files between on-premises servers and Azure storage, providing a seamless way to keep files in sync across distributed environments.     |
| Azure File Sync             | Azure File Sync synchronizes files between on-premises file servers and Azure file shares, allowing organizations to centralize file storage in Azure while maintaining local access and performance. |
| Azure Import/Export Service | Azure Import/Export Service allows organizations to securely ship large volumes of data on physical storage devices to Azure datacenters for offline data transfer and ingestion into Azure storage.  |
| Azure Logic Apps            | Azure Logic Apps provides workflow automation and integration capabilities, allowing users to create automated workflows for file movement and processing across various cloud services.              |
| Azure Storage Explorer      | Azure Storage Explorer is a graphical tool for managing Azure storage accounts and files. It provides an intuitive interface for uploading, downloading, and managing files within Azure storage.     |

---

---

## 7-Azure identity, access, and security

| Category                            | Feature                                        | Description                                                                                                                                                               |
| ----------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **General**                         | **Microsoft Entra ID**                         | Cloud-based identity and access management service that allows signing into Microsoft and developed cloud applications. Also helps maintain on-premises Active Directory. |
|                                     | **Active Directory on Windows Server**         | Provides identity and access management, managed by the organization for on-premises environments.                                                                        |
| **Features of Microsoft Entra ID**  | **Authentication**                             | Verification of identity to access applications, includes self-service password reset, multifactor authentication (MFA), and more.                                        |
|                                     | **Single Sign-On (SSO)**                       | Simplifies access by using one identity across multiple applications.                                                                                                     |
|                                     | **Application Management**                     | Manage both cloud and on-premises apps.                                                                                                                                   |
|                                     | **Device Management**                          | Supports device registration and management through Microsoft Intune.                                                                                                     |
| **Integration**                     | **Microsoft Entra Connect**                    | Synchronizes user identities between on-premises Active Directory and Microsoft Entra ID.                                                                                 |
| **Microsoft Entra Domain Services** | **Managed Domain Services**                    | Provides domain join, group policy, LDAP, Kerberos/NTLM authentication. Managed by Azure, reducing the need for on-premises domain controller maintenance.                |
|                                     | **Synchronization**                            | One-way synchronization from Microsoft Entra ID to Microsoft Entra Domain Services.                                                                                       |
| **Azure Authentication Methods**    | **Standard Passwords, SSO, MFA, Passwordless** | Includes various authentication methods such as standard passwords, single sign-on, multifactor authentication, and passwordless options.                                 |
|                                     | **Windows Hello for Business**                 | Biometric and PIN credentials for secure access.                                                                                                                          |
|                                     | **Microsoft Authenticator App**                | Turns a mobile phone into a strong, passwordless credential.                                                                                                              |
|                                     | **FIDO2 Security Keys**                        | Unphishable, standards-based passwordless authentication method.                                                                                                          |
| **Azure External Identities**       | **External Identity**                          | Identity outside your organization used to securely interact.                                                                                                             |
|                                     | **B2B Collaboration**                          | Use preferred identity to sign in to enterprise applications.                                                                                                             |
|                                     | **B2B Direct Connect**                         | Two-way trust with another Microsoft Entra organization.                                                                                                                  |
|                                     | **Azure AD B2C**                               | Identity and access management for consumer-facing applications.                                                                                                          |

---

---

## 8-Cost Management in Azure

| Cost Factor           | Description                                                | Impact Details                                                                                          | Examples                                                                                                                        |
| --------------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Resource Type**     | The specific Azure services used (VMs, storage, etc.).     | Costs vary based on the type and settings of each resource, as well as the region they are deployed in. | - VM pricing varies by size, region, and OS.<br>- Storage accounts differ in cost based on access tiers and redundancy options. |
| **Consumption**       | The amount of resources consumed.                          | Pay-as-you-go pricing model, with optional reserved capacity for discounts.                             | - Higher compute usage increases costs.<br>- Reserved instances provide up to 72% discount.                                     |
| **Maintenance**       | Management of Azure resources.                             | Proper resource management can prevent unnecessary costs from idle or unoptimized resources.            | - Regularly reviewing and shutting down unused VMs can reduce costs.                                                            |
| **Geography**         | The region where resources are deployed.                   | Costs vary due to regional differences in electricity, labor, taxes, and data transfer fees.            | - Deploying services in regions with lower costs.<br>- Data transfer costs are lower when kept within the same region.          |
| **Subscription Type** | The type of Azure subscription used.                       | Different subscriptions can include various pricing structures and discounts.                           | - Azure Free accounts offer limited free resources.<br>- Enterprise agreements may include different cost structures.           |
| **Azure Marketplace** | Third-party services and products purchased through Azure. | Costs include Azure services and third-party vendor charges.                                            | - Purchasing pre-configured VMs or specialized services from third-party vendors.                                               |
| **Network Traffic**   | Data transfer volumes and locations.                       | Costs associated with data moving in and out of Azure datacenters, especially across regions.           | - Inbound data to Azure is generally free, but outbound data incurs charges based on the amount and destination.                |

---

---

## 9-Features and tools in Azure for governance and compliance

| Content                               | Keywords                                                                | Definitions & Descriptions                                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Purpose of Microsoft Purview          | Microsoft Purview, Data Governance, Compliance                          | - **Microsoft Purview**: Family of data governance, risk, and compliance solutions providing unified view into data across on-premises, multicloud, and software-as-a-service environments. - **Data Governance**: Managing and protecting data assets. - **Compliance**: Ensuring adherence to regulatory standards.                                       |
| Purview Risk and Compliance Solutions | Risk, Compliance, Microsoft 365, Security, Monitoring                   | - **Risk and Compliance Solutions**: Utilize Microsoft 365 services for managing and monitoring data to protect against threats, identify risks, and comply with regulations. - **Microsoft 365 Services**: Includes Teams, OneDrive, Exchange, etc. - **Security Monitoring**: Helps protect sensitive data and manage regulatory compliance requirements. |
| Unified Data Governance               | Data Governance, Azure, SQL, Hive, Multicloud                           | - **Unified Data Governance**: Manage on-premises, multicloud, and SaaS data with robust governance capabilities. - **Azure, SQL, Hive**: Data stored in Azure, SQL databases, and Hive. - **Multicloud**: Extending governance to non-Azure clouds like AWS.                                                                                               |
| Purpose of Azure Policy               | Azure Policy, Compliance, Rules, Azure RBAC                             | - **Azure Policy**: Service enabling creation, assignment, and management of policies for controlling or auditing resources. - **Compliance**: Ensuring resources conform to corporate standards. - **Rules**: Policies defining configurations to enforce across resources. - **Azure RBAC**: Role-based access control managing user permissions.         |
| Defining Policies                     | Policies, Initiatives, Scope, Inheritance                               | - **Policies**: Rules controlling or auditing resource configurations. - **Initiatives**: Groups of related policies. - **Scope**: Level at which policies are applied (e.g., resource, group, subscription). - **Inheritance**: Policies applied to parent resources propagate to child resources.                                                         |
| Built-in Definitions                  | Built-in Policies, Azure Services, Compliance, Azure Policy Initiatives | - **Built-in Policies**: Pre-defined policies for Storage, Networking, Compute, etc. - **Azure Services**: Resources subject to Azure Policy enforcement. - **Compliance**: Ensuring adherence to regulatory requirements. - **Azure Policy Initiatives**: Grouping of built-in policies for larger compliance goals.                                       |
| Purpose of Azure Policy               | Azure Policy, Compliance, Resource                                      | - **Azure Policy**: Service in Azure for creating, assigning, and managing policies controlling or auditing resources. - **Compliance**: Ensuring adherence to corporate standards. - **Resource**: Azure cloud resources.                                                                                                                                  |
| Purpose of Resource Locks             | Resource Locks, Prevent, Delete, ReadOnly                               | - **Resource Locks**: Prevent accidental deletion or changes to Azure resources. - **Prevent (Delete)**: Stop authorized users from deleting resources. - **ReadOnly**: Stop deletion or updates; akin to Reader role.                                                                                                                                      |
| Purpose of Service Trust Portal       | Service Trust Portal, Security, Privacy, Compliance                     | - **Service Trust Portal**: Microsoft's platform offering access to security, privacy, and compliance resources. - **Authentication**: Sign-in required with Microsoft Entra organization account. - **Non-disclosure Agreement**: Review and acceptance needed for compliance materials.                                                                   |

---

---

## 10-Feature & Tools for Managing and Deploying Azure Resources

| Feature               | Description                                                              | Example Code Snippet                                                                                                       |
| --------------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| **Azure Portal**      | Web-based UI for managing Azure resources.                               | GUI-based, no code snippet.                                                                                                |
| **Azure Cloud Shell** | Browser-based shell experience, supports Azure PowerShell and Azure CLI. | `# Access Cloud Shell in Azure Portal`                                                                                     |
| **Azure PowerShell**  | Manages Azure resources using PowerShell cmdlets.                        | `powershell\nConnect-AzAccount\nNew-AzVm -ResourceGroupName 'MyResourceGroup' -Name 'MyVm' -Location 'East US'\n`          |
| **Azure CLI**         | Command-line tool that uses Bash commands for Azure management.          | `bash\naz login\naz group create --name MyResourceGroup --location "East US"\n`                                            |
| **Azure Arc**         | Extends Azure management to hybrid and multicloud environments.          | `bash\naz connectedmachine connect --resource-group MyResourceGroup --name MyServer --location "East US"\n`                |
| **ARM Templates**     | Declarative JSON format for deploying Azure resources.                   | `json\n{"type": "Microsoft.Compute/virtualMachines", "apiVersion": "2019-12-01", "name": "MyVm", "location": "East US"}\n` |
| **Bicep**             | Language for deploying Azure resources, simpler than ARM Templates.      | `bicep\nresource myVm 'Microsoft.Compute/virtualMachines@2020-06-01' = { name: 'MyVm', location: 'East US' }\n`            |

---

---

## 11-Monitoring Tools in Azure

| Service                  | Purpose                                                                                             | Features / Capabilities                                                                                 |
| ------------------------ | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Azure Advisor**        | Optimizes Azure resources for reliability, security, performance, operational excellence, and cost. | Provides actionable recommendations, available via Azure portal and API.                                |
| **Azure Service Health** | Tracks the health and status of Azure services and resources.                                       | Includes Azure Status, Service Health, and Resource Health for comprehensive monitoring.                |
| **Azure Monitor**        | Collects, analyzes, and acts on telemetry data from Azure and other environments.                   | Features Azure Log Analytics, Alerts, and Application Insights for detailed monitoring and diagnostics. |

## 11-Availablity

| Availability (Nines) | Minimum VMs Required | Availability Zones Required | Downtime per Year | Description                                                         |
|----------------------|----------------------|-----------------------------|-------------------|---------------------------------------------------------------------|
| 99% (Two Nines)      | 2                    | 1                           | 3.65 days         | VMs can be in the same Zone; less focus on high availability.       |
| 99.9% (Three Nines)  | 2                    | 1+                          | 8.76 hours        | VMs should ideally be in separate Fault Domains within a Zone.      |
| 99.99% (Four Nines)  | 2+                   | 2+                          | 52.56 minutes     | VMs must be across multiple Availability Zones to ensure high availability and fault tolerance. |
| 99.999% (Five Nines) | 3+                   | 3+                          | 5.26 minutes      | Multiple VMs across all available Availability Zones in a region are recommended for maximum resilience. |

### Key Considerations:
- **VMs Count:** Increasing the number of VMs can enhance fault tolerance and load distribution, which is crucial for maintaining high availability.
- **Availability Zones:** Distributing VMs across multiple Availability Zones protects against zone-level failures. Each zone contains one or more data centers equipped with independent power, cooling, and networking.
- **SLA Calculation:** Azure provides an SLA for Virtual Machines that have two or more instances deployed in the same Availability Set or Virtual Machine Scale Set in at least two Availability Zones. The SLA for a single instance VM with premium storage is lower but can be enhanced with additional instances and proper configuration.
- **Additional Resources:** Utilizing Azure services like Azure Site Recovery and Azure Backup, along with strategic placement of VMs, helps in achieving higher SLAs.

