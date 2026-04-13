# azure-hybrid-identity-lab
Home Lab for understanding and testing Azure Hybrid Identity

## Technologies Used
- On-Premises Active Directory (Windows Server)
- Microsoft Entra ID (Azure AD)
- Entra Connect (Azure AD Connect)
- Windows 11 (Domain-Joined Laptop)
- VMWare Workstation (Domain-Joined Windows 11 VM)

## Authentication Flow
User → Domain-Joined Device → Active Directory → Entra Connect → Entra ID → Cloud Applications

## Implementation

# 1. Active Directory Setup
- Configured a domain controller on Windows Server 2025
- Created users and organizational units (OUs)
- Established domain environment for authentication

# 2. Entra ID Integration
- Configured Microsoft Entra ID tenant
- Installed and configured Entra Connect on the DC
- Enabled Password Hash Synchronization (PHS)

# 3. Directory Synchronization
- Synced on-prem AD users to Entra ID
- Verified synchronization status
- Confirmed user visibility in Entra portal

# 4. Client Configuration
- Joined Windows client to domain
- Validated login using domain credentials
- Tested access to cloud services (office.com)

# 5. Authentication & Testing
- Enforced Multi-Factor Authentication (MFA) across all user accounts
  - Standard users configured with traditional MFA methods
  - Administrative accounts secured using passwordless MFA for enhanced protection

- Disabled legacy authentication protocols
  - Blocked Exchange ActiveSync and other legacy clients
  - Reduced exposure to credential-based attacks (e.g., password spray)

- Validated authentication behavior:
  - Confirmed MFA prompts during cloud sign-in
  - Verified sign-in logs in Entra ID
  - Tested authentication scenarios with domain controller offline

## Key Findings
- Users can authenticate to cloud services when the domain controller is offline when using Password Hash Sync
- On-prem authentication depends on domain controller availability
- Entra ID maintains independent authentication once identities are synchronized
- Hybrid environments introduce dependencies that impact SSO and login behavior

## Screenshots
### Entra ID Users
![Entra Users](https://github.com/arobinson-it/azure-hybrid-identity-lab/blob/90de90a8f4169b8db488be5d0f4dfc79c610fc9b/users.png)

### Sign-in Logs
![Sign-in Logs](https://github.com/arobinson-it/azure-hybrid-identity-lab/blob/90de90a8f4169b8db488be5d0f4dfc79c610fc9b/sign-ins.png)

### Sync Status
![Sync Status](https://github.com/arobinson-it/azure-hybrid-identity-lab/blob/90de90a8f4169b8db488be5d0f4dfc79c610fc9b/sync%20status.png)

### Domain Joined Laptop
![Domain Joined Laptop](https://github.com/arobinson-it/azure-hybrid-identity-lab/blob/90de90a8f4169b8db488be5d0f4dfc79c610fc9b/domain-joined-laptop.png)

## Future Improvements
- Configure Azure RBAC for resource access control
- Deploy Azure Policy for governance and compliance
- Integrate Microsoft Intune for device management

## Lessons Learned
- Understanding authentication flow is critical in hybrid environments
- Cloud identity can remain operational even when on-prem infrastructure fails
- Proper configuration of sync and identity methods impacts availability and security

## Author
Adam Robinson
