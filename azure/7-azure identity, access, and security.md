# Azure Identity, Access, and Security

## Microsoft Entra ID

Microsoft Entra ID is Microsoft's cloud-based identity and access management service, which integrates with on-premises Active Directory. It offers global service availability while allowing you to manage identity accounts.

### Key Features:

- **Authentication:** Verifies identity to access applications, with options for self-service password reset, multifactor authentication, and more.
- **Single Sign-On (SSO):** Allows a single set of credentials to access multiple applications, enhancing convenience and security.
- **Application Management:** Manages both cloud and on-premises applications with features like Application Proxy and SaaS app integrations.
- **Device Management:** Supports device registration for managed access, integrating with tools like Microsoft Intune.

### User Groups:

- IT administrators
- App developers
- End-users
- Online service subscribers

### Connectivity with On-Premises AD:

- **Microsoft Entra Connect:** Synchronizes identities between on-premises AD and Microsoft Entra ID, supporting features across both environments.

## Microsoft Entra Domain Services

Provides managed domain services like domain join, LDAP, and Kerberos/NTLM authentication without the need to manage domain controllers in the cloud.

### How It Works:

- Define a namespace for the domain.
- Deploy two Windows Server domain controllers in Azure.
- Manage domain features without the need to configure or update the domain controllers manually.

### Synchronization:

- Performs one-way synchronization from Microsoft Entra ID to Microsoft Entra Domain Services.
- Supports common features such as domain join and group policy.

## Azure Authentication Methods

### Methods:

- **Standard Passwords**
- **Single Sign-On (SSO)**
- **Multifactor Authentication (MFA)**
- **Passwordless**

### Single Sign-On (SSO):

- Allows access to multiple resources and applications with one set of credentials.

### Multifactor Authentication (MFA):

- Adds a layer of security by requiring multiple forms of verification.

### Passwordless Authentication:

- Removes the need for passwords, using biometrics, PINs, or security keys instead.

#### Options for Passwordless Authentication:

- **Windows Hello for Business**
- **Microsoft Authenticator App**
- **FIDO2 Security Keys**

## Azure External Identities

### Overview:

Enables secure interactions with users outside of your organization using their own identities.

### Capabilities:

- **B2B Collaboration:** Lets external users sign in with their preferred identities to access your applications.
- **B2B Direct Connect:** Establishes mutual trust with another Microsoft Entra organization.
- **Azure AD B2C:** Manages identities for consumer-facing applications.

### Integration:

- Supports seamless collaboration and secure access management across organizational boundaries.

# Azure Conditional Access Overview

Azure Conditional Access is a tool within Microsoft Entra ID that enables organizations to enforce access controls on cloud resources based on dynamic conditions. It enhances security by evaluating the context of a user's login attempt and applying appropriate access policies.

## Key Features

- **Contextual Access Control**: Decisions are made based on the user's identity, location, device security status, and application sensitivity.
- **Dynamic Policies**: Administrators can configure policies that adapt to the user's context, enhancing security without compromising on user convenience.
- **Granular Control**: Conditions can be set to target specific scenarios like requiring multifactor authentication (MFA) if the user is accessing from an untrusted location.

## How It Works

1. **Signal Collection**: During the login attempt, Conditional Access collects signals like location, device compliance, and application being accessed.
2. **Decision Making**: Based on the gathered signals and predefined policies, the system decides whether to allow access, deny access, or require additional verification.
3. **Enforcement**: The decision is enforced by either granting access, blocking access, or challenging the user for additional credentials (e.g., MFA).

## Use Cases

- **Secure Remote Work**: Allows users to access applications securely from anywhere, adjusting authentication requirements based on their location and device security.
- **Compliance Enforcement**: Ensures that access to sensitive applications is only granted from compliant devices and trusted locations.
- **Tailored Authentication**: Minimizes authentication challenges in trusted scenarios while enforcing stricter controls when needed to secure access.

Conditional Access is essential for organizations looking to secure their applications and data against unauthorized access and potential security threats, adapting in real-time to various login contexts.

# Azure Role-Based Access Control (RBAC) Overview

Azure Role-Based Access Control (RBAC) is a system that allows organizations to manage who has access to Azure resources, ensuring that users have only the permissions they need to perform their jobs.

## Key Features

- **Least Privilege Security**: Ensures users have only the access they need, which minimizes potential abuse of excess permissions.
- **Built-in and Custom Roles**: Azure provides many predefined roles that cover common use cases and allows the creation of custom roles tailored to specific needs.
- **Scope-Based Access Control**: Access permissions can be applied at various levels like management groups, subscriptions, resource groups, or individual resources.

## How It Works

1. **Role Assignments**: Users or groups are assigned roles that define their permissions.
2. **Scope**: Defines where permissions are applied. Can be a resource, resource group, subscription, or management group.
3. **Inheritance**: Permissions granted at a higher scope automatically apply to lower levels within that scope.

## Use Cases

- **Managing Multiple Teams**: Simplifies permission management across different teams and departments, ensuring each team has appropriate access.
- **Dynamic Access Needs**: As resources or team structures change, Azure RBAC allows for flexible adjustments to access permissions without the need to individually update each user's permissions.
- **Regulatory Compliance**: Helps ensure that access controls meet compliance requirements by enforcing strict access to sensitive resources.

## Enforcing Azure RBAC

Azure RBAC is enforced through Azure Resource Manager, which handles all requests to Azure resources. Whether accessing resources via Azure Portal, Azure CLI, or Azure PowerShell, RBAC policies are applied to ensure users can only perform actions allowed by their assigned roles.

Azure RBAC uses an "allow" model, where users are permitted to perform specific actions defined by their roles within the scope of their role assignments.

## Example Diagram: Scopes and Roles

Imagine a diagram showing the hierarchy:

- Top Level: Management Group (Owner role)
- Second Level: Subscription (Reader role)
- Third Level: Resource Group (Contributor role)

This structure helps visualize how permissions are structured and inherited in Azure environments.

Azure RBAC is crucial for maintaining security and operational efficiency in Azure cloud environments by ensuring users have the appropriate level of access to resources.

# Zero Trust Security Model

Zero Trust is a security model that assumes the worst-case scenario and protects resources with that expectation. It operates under the assumption of a breach from the outset and verifies each request as though it originated from an uncontrolled network.

## Guiding Principles

1. **Verify Explicitly**: Always authenticate and authorize based on all available data points.
2. **Use Least Privilege Access**: Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.
3. **Assume Breach**: Minimize blast radius and segment access. Verify end-to-end encryption. Use analytics to get visibility, drive threat detection, and improve defenses.

## Adapting to Zero Trust

Traditionally, corporate networks were restricted and assumed safe, with only managed devices allowed to join, tightly controlled VPN access, and restrictions on personal devices.

The Zero Trust model flips this approach. It requires authentication for everyone, regardless of device or location, and grants access based on authentication rather than network location.

This modern security model is essential for adapting to the complexity of the modern environment, embracing the mobile workforce, and protecting people, devices, applications, and data wherever they're located.

# Defense-in-Depth

Defense-in-depth is a security strategy aimed at protecting information and preventing unauthorized access to it. It employs a series of layers or mechanisms to slow down the advance of an attack and prevent further exposure if one layer is breached.

## Layers of Defense-in-Depth

Defense-in-depth can be visualized as a set of layers, with the central data to be secured surrounded by protective layers:

1. **Physical Security**: Protects computing hardware in the datacenter, ensuring physical safeguards against access to assets.
2. **Identity and Access**: Controls access to infrastructure, ensures secure identities, grants access only as needed, and logs sign-in events and changes.
3. **Perimeter**: Uses DDoS protection and perimeter firewalls to filter and identify network-based attacks against resources.
4. **Network**: Limits communication between resources, restricts inbound internet access, and implements secure connectivity to on-premises networks.
5. **Compute**: Secures access to virtual machines, implements endpoint protection, and ensures systems are patched and current.
6. **Application**: Integrates security into the application development lifecycle, ensures applications are secure and free of vulnerabilities, and stores sensitive application secrets securely.
7. **Data**: Controls access to business and customer data, ensures confidentiality, integrity, and availability, and protects data stored in databases, virtual machines, SaaS applications, and cloud storage.

## Azure's Approach to Defense-in-Depth

Azure provides security tools and features at every layer of the defense-in-depth concept:

- **Physical Security**: Microsoft employs various physical security mechanisms in its cloud datacenters.
- **Identity and Access**: Azure offers single sign-on (SSO), multifactor authentication, and auditing of events and changes.
- **Perimeter**: DDoS protection and perimeter firewalls are available to filter and identify attacks.
- **Network**: Azure enables limiting communication between resources, secure connectivity, and inbound/outbound access control.
- **Compute**: Secure access to virtual machines and endpoint protection are available.
- **Application**: Azure emphasizes integrating security into the development lifecycle and provides tools to ensure applications are secure.
- **Data**: Azure offers controls and processes to ensure the confidentiality, integrity, and availability of data stored in various services.

# Microsoft Defender for Cloud

Microsoft Defender for Cloud is a comprehensive security solution designed to monitor and protect your cloud, on-premises, hybrid, and multi-cloud environments. It offers a range of capabilities for security posture management and threat protection, helping organizations strengthen their security defenses. Here's an overview of its key features and functionalities:

## Protection Everywhere You're Deployed

- Defender for Cloud is natively integrated into Azure, offering monitoring and protection for Azure services without requiring additional deployment.
- It extends its protection capabilities to on-premises datacenters and other cloud environments, ensuring comprehensive security coverage regardless of deployment location.
- Azure Arc enables the extension of Defender for Cloud's capabilities to non-Azure machines, facilitating easy deployment and management in hybrid and multi-cloud environments.

## Azure-Native Protections

- Detects threats across various Azure Platform-as-a-Service (PaaS) services, including Azure App Service, Azure SQL, Azure Storage Account, and more.
- Automatically classifies data in Azure SQL and provides vulnerability assessments for Azure SQL and Storage services.
- Helps secure networks by limiting exposure to brute force attacks and implementing secure access policies.

## Defend Your Hybrid Resources

- Extends protection to non-Azure servers in hybrid cloud environments, providing customized threat intelligence and prioritized alerts.
- Deploying Azure Arc and enabling Defender for Cloud's enhanced security features helps secure on-premises machines effectively.

## Defend Resources Running on Other Clouds

- Offers protection for resources in other clouds, such as AWS and GCP, by extending Defender for Cloud's capabilities.
- Features like Cloud Security Posture Management (CSPM) and threat detection are extended to AWS resources, providing comprehensive security coverage.

## Assess, Secure, and Defend

- **Continuously Assess**: Provides vulnerability assessment solutions for virtual machines, container registries, and SQL servers, ensuring regular scans and identification of vulnerabilities.
- **Secure**: Implements security policies based on Azure Policy controls, ensuring secure configurations across resources and adherence to security best practices.
- **Defend**: Generates security alerts, provides advanced threat protection features, and correlates alerts based on cyber kill-chain analysis to detect and respond to threats effectively.

Microsoft Defender for Cloud plays a crucial role in helping organizations assess their security posture, implement robust security measures, and defend against evolving threats across various deployment environments.
