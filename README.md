# Infrastructure HomeLab

A virtualized enterprise-style home lab built to develop and demonstrate practical skills across **Windows infrastructure, identity, networking, virtualization, backup and recovery, Linux administration, automation, and cloud integration**.

The lab originally began as a Microsoft Entra hybrid identity project and has evolved into an interconnected infrastructure environment for testing enterprise technologies, troubleshooting realistic infrastructure scenarios, and building hands-on administration experience.

Rather than operating as a collection of isolated virtual machines, the lab is designed around **dependencies between infrastructure services**. Changes to networking, DNS, Active Directory, authentication, or firewall policy can have realistic effects across the environment.

## Environment Overview

| Area | Technologies |
|---|---|
| Virtualization | VMware Workstation Pro |
| Windows Infrastructure | Windows Server 2025, Active Directory, DNS, DHCP |
| Identity | Microsoft Entra ID, Entra Connect, Password Hash Synchronization |
| Networking | pfSense, VMware virtual networks, NAT, routing, segmentation |
| Security | MFA, Conditional Access, privileged identities, legacy authentication controls |
| Backup | Veeam Backup & Replication |
| Linux | Ubuntu Server, Netplan, DNS and network administration |
| Automation | PowerShell |
| CI/CD | Azure DevOps, Azure Repos, Azure Pipelines |

## Lab Architecture

The environment consists of multiple virtualized infrastructure and client systems connected through isolated VMware virtual networks and routed through pfSense.

```text
                               Internet
                                  │
                                  ▼
                           ┌─────────────┐
                           │   pfSense   │
                           │   Firewall  │
                           └──────┬──────┘
                                  │
                    ┌─────────────┴─────────────┐
                    │                           │
                    ▼                           ▼
             Windows Infrastructure       Linux Infrastructure
                    │                           │
              ┌─────┼─────┐                     │
              │     │     │                     │
              ▼     ▼     ▼                     ▼
             DC01  Veeam  Clients             Ubuntu
            AD/DNS Server
```


The network architecture is intentionally segmented to provide practical experience with:

- Routing between isolated networks
- Firewall policies
- DHCP
- DNS
- NAT
- Internet access control
- Infrastructure dependencies
- Windows and Linux connectivity troubleshooting

<details>
<summary><strong>Windows Infrastructure & Active Directory</strong></summary>

The Windows infrastructure provides the foundation for the lab's identity and domain services.

### Active Directory

- Windows Server 2025 domain controller
- Active Directory Domain Services (AD DS)
- Active Directory-integrated DNS
- Organizational Units
- User and group administration
- Domain authentication
- Domain-joined Windows clients
- DHCP authorization
- Windows infrastructure administration

The environment is designed to reproduce common enterprise dependencies between **Active Directory, DNS, DHCP, networking, and client authentication**.

</details>

<details>
<summary><strong>Microsoft Entra Hybrid Identity</strong></summary>

The lab integrates on-premises Active Directory with Microsoft Entra ID using Microsoft Entra Connect.

### Configuration

- Microsoft Entra ID tenant
- Microsoft Entra Connect
- Password Hash Synchronization (PHS)
- On-premises identity synchronization
- Synchronized user accounts
- Cloud authentication
- Authentication testing during infrastructure outages

### Authentication Flow

    On-Premises Active Directory
                |
                v
       Microsoft Entra Connect
                |
                v
         Microsoft Entra ID
                |
                v
         Cloud Applications

The environment is used to explore the distinction between **on-premises identity infrastructure and cloud authentication**, including how synchronized identities behave when on-premises infrastructure is unavailable.

</details>

<details>
<summary><strong>Microsoft Entra Security</strong></summary>

Identity security has been incorporated into the environment to provide practical experience with modern authentication and access-control concepts.

- Multi-Factor Authentication
- Separate standard and administrative identities
- Passwordless authentication for privileged accounts
- Conditional Access policies
- Legacy authentication blocking
- Sign-in log investigation
- Authentication testing during infrastructure outages

These configurations provide hands-on experience with both **identity administration and identity security** rather than treating Entra ID purely as a synchronization target.

</details>

<details>
<summary><strong>Networking & pfSense</strong></summary>

pfSense provides the primary routing and firewall layer for the lab.

### pfSense

Current interfaces include:

- WAN
- LAN
- OPT1

The firewall is used to practice:

- Inter-network routing
- DHCP
- NAT
- DNS
- Firewall rules
- Network aliases
- Internet access control
- Network segmentation

### VMware Networking

VMware Workstation Pro provides the underlying virtual network infrastructure.

Current networks include:

- **VMnet1** — Host-only
- **VMnet2** — Infrastructure network
- **VMnet3** — Additional isolated network
- **VMnet8** — NAT / Internet connectivity

This provides a controlled environment for testing connectivity and the interaction between **virtual networking, routing, firewall policy, DNS, and DHCP**.

</details>

<details>
<summary><strong>Backup & Recovery</strong></summary>

A dedicated Veeam server is used to develop practical backup and recovery experience.

### Veeam

Current work includes:

- Virtual machine backups
- Backup configuration
- Backup verification
- Recovery testing
- Understanding backup infrastructure dependencies
- Testing recovery scenarios

The goal is to treat backup as part of the infrastructure rather than simply configuring a backup job and assuming recovery will work.

</details>

<details>
<summary><strong>Linux Administration</strong></summary>

Ubuntu Server provides a Linux component within the otherwise Microsoft-focused infrastructure environment.

Current work includes:

- Ubuntu Server deployment
- Static and DHCP networking
- Netplan configuration
- DNS troubleshooting
- Connectivity troubleshooting
- Linux server administration
- Integration with segmented lab networks

</details>

<details>
<summary><strong>Automation & CI/CD</strong></summary>

Automation is being incorporated into the lab using PowerShell and Azure DevOps.

### Azure DevOps

Current work includes:

- Azure Repos
- YAML-based Azure Pipelines
- CI/CD pipeline design
- Multi-stage pipelines
- Pipeline approvals and checks
- PowerShell automation
- Repository-based infrastructure tooling

The goal is to move beyond manually administering the environment and begin applying **source control, automation, and repeatable deployment practices**.

</details>

<details>
<summary><strong>Skills Being Practiced</strong></summary>

The lab is used to build practical administration, automation, and troubleshooting experience across:

- Active Directory administration
- Microsoft Entra ID
- Hybrid identity
- Windows Server administration
- Linux administration
- DNS
- DHCP
- TCP/IP networking
- Firewall administration
- Network segmentation
- Virtualization
- Backup and recovery
- PowerShell
- Azure DevOps
- CI/CD
- Authentication and access control
- Infrastructure troubleshooting

</details>

<details>
<summary><strong>Real-World Scenarios</strong></summary>

The lab is intentionally built to support realistic troubleshooting scenarios rather than simply demonstrating successful configurations.

### Identity & Authentication

- Testing authentication when Active Directory infrastructure is unavailable
- Investigating synchronized identities in Microsoft Entra ID
- Testing Conditional Access and MFA policies
- Investigating authentication and sign-in failures

### Networking

- Troubleshooting DNS across network segments
- Testing routing between isolated networks
- Controlling server Internet access through pfSense
- Testing DHCP and NAT behavior
- Investigating connectivity failures between infrastructure components

### Infrastructure

- Backing up and recovering infrastructure VMs
- Troubleshooting Windows and Linux connectivity
- Testing infrastructure dependencies
- Investigating how failures in one service affect dependent systems

The underlying goal is to practice **finding the actual failing layer rather than troubleshooting only the visible symptom**.

</details>

<details>
<summary><strong>Future Development</strong></summary>

Planned additions and improvements include:

- Microsoft Intune / endpoint management
- Azure administration and resource management
- Expanded PowerShell automation
- Ansible
- Terraform
- Kubernetes
- Expanded network segmentation
- Monitoring and centralized logging
- More comprehensive backup and disaster-recovery testing

</details>

<details>
<summary><strong>Lessons Learned</strong></summary>

Building and maintaining the environment has provided practical experience with the dependencies that exist between infrastructure services.

Some of the most important lessons so far:

- **DNS is foundational** to both Windows and network infrastructure.
- **Hybrid identity requires understanding both on-premises and cloud authentication.**
- **Network segmentation introduces additional routing and firewall dependencies.**
- **Backup infrastructure is itself dependent on the underlying network and virtualization environment.**
- **Infrastructure problems are often dependency problems.**
- **Effective troubleshooting starts by identifying which layer is actually failing rather than assuming the visible symptom is the root cause.**

</details>

## Author
Adam Robinson
