# Azure Governance and Compliance

Microsoft Purview is a family of data governance, risk, and compliance solutions that provides a unified view of your data across on-premises, multicloud, and software-as-a-service environments.

### Key Features:

- **Automated data discovery**
- **Sensitive data classification**
- **End-to-end data lineage**

## Solution Areas:

Microsoft Purview consists of two main solution areas:

### 1. Risk and Compliance:

- Utilizes Microsoft 365 services such as Teams, OneDrive, and Exchange.
- Helps protect sensitive data across clouds, apps, and devices.
- Identifies data risks and manages regulatory compliance requirements.

### 2. Unified Data Governance:

- Manages on-premises, multicloud, and software as a service data.
- Robust data governance capabilities for Azure, SQL, Hive databases, and other clouds like Amazon S3.
- Creates a comprehensive map of the data estate with classification and lineage.
- Identifies storage locations of sensitive data.
- Provides a secure environment for data consumers.
- Generates insights into data storage and usage.
- Manages access to data securely and at scale.

---

## Get Started with Microsoft Purview:

- **Automated Discovery**: Allow Purview to automatically discover your data across various environments.
- **Data Classification**: Utilize Purview's classification tools to identify and label sensitive data.
- **End-to-End Lineage**: Track the lineage of your data to understand its journey and ensure compliance.

## Key Benefits:

- Gain insights into your entire data estate.
- Enhance data security and compliance.
- Improve data governance and management.
- Facilitate regulatory compliance efforts.
- Empower data consumers with secure access to valuable insights.

---

This cheat sheet provides a quick reference for understanding the capabilities and benefits of Microsoft Purview.

## Purpose of Azure Policy:

Azure Policy is a service in Azure that enables you to create, assign, and manage policies to control or audit your resources. Its primary purpose is to ensure that resource configurations remain compliant with corporate standards.

### Key Features:

- **Policy Definition**: Create individual policies or groups of related policies called initiatives.
- **Policy Enforcement**: Evaluate resource configurations and enforce policies to maintain compliance.
- **Inheritance**: Policies can be set at different levels (resource, group, subscription) and are automatically applied to all child resources.
- **Built-in Policies**: Azure Policy comes with predefined policy and initiative definitions for various Azure services.

## How Azure Policy Works:

- **Definition**: Define policies to specify rules for resource configurations.
- **Evaluation**: Azure Policy evaluates resources against defined policies and highlights noncompliant resources.
- **Enforcement**: Prevent noncompliant resources from being created or automatically remediate noncompliant configurations.
- **Integration**: Integrates with Azure DevOps for continuous integration and delivery pipeline policies.

## Azure Policy Initiatives:

- Initiatives group related policies together to track compliance for larger goals.
- Each initiative contains multiple policy definitions aimed at achieving a specific compliance objective.
- Example: "Enable Monitoring in Azure Security Center" initiative includes policies to monitor unencrypted SQL databases, OS vulnerabilities, and missing endpoint protection.

### Benefits of Azure Policy:

- Ensures resource configurations align with organizational standards.
- Provides visibility into compliance status across Azure resources.
- Facilitates automated enforcement and remediation of noncompliant configurations.
- Integrates with Azure DevOps for seamless policy enforcement in CI/CD pipelines.

## Purpose of Resource Locks:

Resource locks in Azure prevent accidental deletion or modification of critical cloud resources. They provide an additional layer of protection on top of Azure role-based access control (Azure RBAC) policies.

### Key Features:

- **Prevention of Deletion or Modification**: Resource locks prevent authorized users from deleting or updating resources, depending on the type of lock applied.
- **Types of Locks**: Two types of locks: Delete and ReadOnly, each offering different levels of protection.
- **Scope**: Resource locks can be applied at the level of individual resources, resource groups, or entire subscriptions.
- **Inheritance**: Resource locks are inherited, so applying a lock at a higher level (e.g., resource group) propagates to all child resources within that scope.

## Types of Resource Locks:

- **Delete Lock**: Prevents users from deleting a resource, but allows them to read and modify it.
- **ReadOnly Lock**: Prevents users from deleting or updating a resource, restricting them to read-only access.

### Managing Resource Locks:

- **Azure Portal**: Resource locks can be managed through the Azure portal, under the Settings section of any resource's Settings pane.
- **PowerShell and Azure CLI**: Resource locks can also be managed using PowerShell or Azure CLI commands.
- **Azure Resource Manager Template**: Resource locks can be defined within Azure Resource Manager templates for automated deployment and management.

### Modifying Locked Resources:

- To make changes to a locked resource, the lock must first be removed.
- Even owners of the resource must remove the lock before performing any blocked activity, regardless of RBAC permissions.

# Service Trust Portal

## Purpose:

The Microsoft Service Trust Portal is a comprehensive platform that offers access to a range of content, tools, and resources related to Microsoft's security, privacy, and compliance practices.

### Key Features:

- **Information Repository**: Contains detailed information about Microsoft's implementation of controls and processes safeguarding cloud services and customer data.
- **Authentication**: Access to certain resources requires authentication with a Microsoft cloud services account (Microsoft Entra organization account).
- **Non-disclosure Agreement**: Review and acceptance of the Microsoft non-disclosure agreement for compliance materials may be required for accessing specific resources.

## Accessing the Service Trust Portal:

- **URL**: https://servicetrust.microsoft.com/
- **Authentication**: Sign in with your Microsoft cloud services account to access restricted content.

### Main Menu Categories:

- **Service Trust Portal**: Quick access link to the portal's home page.
- **My Library**: Save documents for quick access and set up notifications for updates.
- **All Documents**: Single landing place for all documents available on the Service Trust Portal. Documents can be pinned for quick access from My Library.
