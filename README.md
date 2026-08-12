# Homelab Infrastructure Lab

A virtualized home lab built to develop and demonstrate practical skills across **Windows infrastructure, identity, networking, backup, Linux administration, and cloud integration**.

The lab started as a Microsoft Entra hybrid identity project and has evolved into a broader infrastructure environment for testing enterprise technologies, troubleshooting real-world infrastructure scenarios, and building hands-on administration experience.

## Technologies

### Virtualization

* VMware Workstation Pro
* Multiple Windows Server and Linux virtual machines
* Isolated virtual networks for infrastructure and client systems

### Identity & Windows Infrastructure

* Windows Server 2025
* Active Directory Domain Services (AD DS)
* Active Directory DNS
* Organizational Units and user management
* Domain-joined Windows clients
* Microsoft Entra ID
* Microsoft Entra Connect
* Password Hash Synchronization (PHS)

### Networking & Security

* pfSense
* Firewall and NAT
* DHCP
* DNS
* Network segmentation
* Isolated VMware virtual networks
* Internet access policies and internal network aliases

### Backup & Recovery

* Veeam Backup & Replication
* Dedicated Veeam server
* Backup testing and recovery scenarios

### Linux

* Ubuntu Server
* Linux networking and Netplan
* DNS troubleshooting
* Linux server administration

## Current Lab Architecture

The environment currently consists of several virtualized infrastructure systems connected through VMware virtual networks.

```text
                         Internet
                            │
                            ▼
                       ┌─────────┐
                       │ pfSense │
                       │ Firewall│
                       └────┬────┘
                            │
              ┌─────────────┴─────────────┐
              │                           │
        Infrastructure                Server Network
           Network                        │
              │                           │
          ┌───┴───┐                  ┌────┴─────┐
          │ DC01  │                  │  Ubuntu  │
          │ AD/DNS│                  │  Server  │
          └───┬───┘                  └──────────┘
              │
        ┌─────┴─────┐
        │           │
     Windows      Other
     Clients       VMs
              
              ┌────────────┐
              │   Veeam    │
              │   Server   │
              └────────────┘
```

## Active Directory

* Deployed Windows Server 2025 as the domain controller
* Configured Active Directory Domain Services
* Configured internal DNS
* Created users and organizational units
* Configured domain authentication
* Joined Windows clients to the domain
* Configured DHCP authorization and domain administration

## Microsoft Entra Hybrid Identity

The lab integrates on-premises Active Directory with Microsoft Entra ID.

* Created Microsoft Entra ID tenant
* Installed and configured Microsoft Entra Connect
* Enabled Password Hash Synchronization
* Synchronize on-premises identities to Entra ID
* Verified synchronization and account visibility
* Tested cloud authentication independently of on-premises availability

### Authentication Flow

```text
On-Prem AD
    │
    │ Microsoft Entra Connect
    ▼
Microsoft Entra ID
    │
    ▼
Cloud Applications
```

The lab demonstrates the distinction between **on-premises authentication** and **cloud authentication**, including the behavior of synchronized identities when the domain controller is unavailable.

## Microsoft Entra Security

Identity security has also been incorporated into the lab environment.

* Multi-Factor Authentication
* Separate standard and administrative identities
* Passwordless authentication for privileged accounts
* Conditional Access policies
* Legacy authentication blocking
* Sign-in log investigation
* Authentication testing during infrastructure outages

## pfSense Networking

pfSense provides the primary routing and firewall layer for the lab.

Current interfaces include:

* WAN
* LAN
* OPT1

VMware virtual networks are used to isolate different portions of the environment.

The firewall configuration is being used to practice:

* Inter-network routing
* DHCP
* NAT
* DNS
* Firewall rules
* Network aliases
* Internet access control
* Segmentation between infrastructure and client/server networks

## VMware Networking

The lab uses VMware Workstation Pro virtual networks to create isolated network segments.

Current virtual networking includes:

* VMnet1 — Host-only
* VMnet2 — Infrastructure network
* VMnet3 — Additional isolated network
* VMnet8 — NAT / Internet connectivity

This provides a controlled environment for testing routing, firewall policies, DHCP, DNS, and connectivity between isolated systems.

## Veeam

A dedicated Veeam server is used to develop practical backup and recovery skills.

Current objectives include:

* Virtual machine backups
* Backup configuration
* Backup verification
* Recovery testing
* Understanding backup infrastructure dependencies

## Ubuntu Server

Ubuntu Server is included as a Linux component of the lab.

Current work includes:

* Server deployment
* Static/DHCP networking
* Netplan configuration
* DNS troubleshooting
* Connectivity troubleshooting
* Integration with the lab's segmented network architecture

## Skills Being Practiced

This lab is primarily used to build practical administration and troubleshooting experience in:

* Active Directory administration
* Microsoft Entra ID
* Hybrid identity
* Windows Server administration
* Linux administration
* DNS
* DHCP
* TCP/IP networking
* Firewall administration
* Network segmentation
* Virtualization
* Backup and recovery
* PowerShell
* Infrastructure troubleshooting
* Authentication and access control

## What This Lab Demonstrates

Rather than being a collection of disconnected VMs, the goal is to maintain an interconnected environment where changes to one component can have realistic effects on the others.

Examples include:

* Testing authentication when AD infrastructure is unavailable
* Troubleshooting DNS across multiple network segments
* Controlling server Internet access through pfSense
* Testing DHCP and routing between isolated networks
* Backing up and recovering infrastructure VMs
* Troubleshooting Windows and Linux connectivity
* Testing identity and authentication policies in Entra ID
* Investigating how infrastructure dependencies affect availability

## Future Development

Planned additions and improvements include:

* Microsoft Intune / endpoint management
* MECM / Configuration Manager
* Azure administration and resource management
* PowerShell automation
* Ansible
* Terraform
* Kubernetes
* Expanded network segmentation
* Additional monitoring and logging
* More comprehensive backup and disaster-recovery testing

## Lessons Learned

Building the environment has provided practical experience with the dependencies that exist between infrastructure services.

In particular:

* DNS is foundational to both Windows and network infrastructure.
* Hybrid identity requires understanding both on-premises and cloud authentication.
* Network segmentation introduces additional routing and firewall dependencies.
* Backup infrastructure is itself dependent on the underlying network and virtualization environment.
* Troubleshooting is often about identifying which layer is actually failing rather than assuming the visible symptom is the root cause.

## Author
Adam Robinson

**Adam Robinson**
