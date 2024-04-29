# Cloud Computing Essentials

## What is Cloud Computing?

- **Definition**: The delivery of computing services over the internet, including virtual machines, storage, databases, networking, IoT, ML, and AI.
- **Advantages**: Enables rapid scaling of IT infrastructure without the constraints of physical data centers.

### Shared Responsibility Model

- **Traditional Datacenter**: Complete organizational responsibility for physical and software management.
- **Cloud Computing**: Responsibilities are shared:
  - **Cloud Provider**: Manages physical security, power, cooling, and network connectivity.
  - **Consumer**: Responsible for data, access security, and managing application settings.
  - **Service-Specific**: Responsibility varies by service model (IaaS, PaaS, SaaS):
    - **IaaS**: Consumers manage applications, data, runtime, middleware, and OS.
    - **PaaS**: Consumers manage applications and data.
    - **SaaS**: Most responsibilities are handled by the cloud provider.

### Cloud Models

- **Private Cloud**: Operated solely for a single organization, offering control over data and security but at higher costs.
- **Public Cloud**: Maintained by third-party providers, accessible to anyone, offering cost efficiency and scalability.
- **Hybrid Cloud**: Combines private and public clouds, offering flexibility and scalability.
- **Multi-Cloud**: Uses multiple public cloud services, allowing for diverse and resilient deployments.

### Cloud Technologies

- **Azure Arc**: Manages and governs resources across multiple clouds.
- **Azure VMware Solution**: Integrates VMware workloads with Azure services, facilitating migration to hybrid and public clouds.

### Consumption-Based Model

- **Financial Aspects**:
  - **CapEx**: Upfront spending on physical infrastructure.
  - **OpEx**: Operational spending, including cloud services which are consumption-based.
- **Benefits**:
  - Flexible and efficient resource utilization.
  - Pay only for resources used.
  - Scalable according to business needs.

### Pricing Models

- **Pay-as-you-go**: Charges based on actual usage, offering flexibility and operational cost management.

This overview provides a foundational understanding of cloud computing, highlighting how resources are managed, deployed, and charged in the cloud environment.

## Cloud Concepts

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
