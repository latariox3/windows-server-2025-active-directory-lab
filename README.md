# Windows Server 2025 — Active Directory Domain Controller Lab

**Project Status:** In Progress — DNS troubleshooting and final validation pending

## 1. Project Overview

This project documents the deployment and configuration of a Windows Server 2025 domain controller in a virtualized lab environment using Oracle VirtualBox.

The lab simulates a small business IT infrastructure for a fictional company named Caribbean Technology Solutions (CTS).

The purpose of this project is to develop hands-on experience in Windows Server administration, Active Directory Domain Services (AD DS), DNS, network configuration, and infrastructure troubleshooting.

## 2. Technologies Used

- Windows Server 2025 Standard Evaluation
- Oracle VirtualBox
- Active Directory Domain Services (AD DS)
- Windows DNS Server
- Windows PowerShell
- Windows Server Manager
- Windows Event Viewer

## 3. Virtual Lab Configuration

| Component | Configuration |
|---|---|
| Virtual machine | SERVER01 |
| Operating system | Windows Server 2025 Standard Evaluation |
| Memory | 4 GB RAM |
| Processors | 2 virtual CPUs |
| Virtual storage | 80 GB dynamically allocated |
| Domain | cts.test |
| NetBIOS name | CTS |
| Domain controller | SERVER01 |
| NAT IP address | 10.0.2.15 |
| Host-only IP address | 192.168.56.10 |
| DNS server | 192.168.56.10 |

## 4. Implementation

### Windows Server Installation

Created a virtual machine in Oracle VirtualBox, attached the Windows Server 2025 installation ISO, and installed the Desktop Experience edition.

### Network Configuration

Configured two virtual network adapters:

- NAT for external connectivity.
- Host-only networking for the private Active Directory lab.

Assigned the host-only interface a static IPv4 address of 192.168.56.10.

### Active Directory Deployment

Installed the Active Directory Domain Services role and promoted SERVER01 to the first domain controller in a new forest named `cts.test`.

### DNS Configuration

Configured Windows DNS Server and verified the presence of the `cts.test` and `_msdcs.cts.test` zones.

## 5. Troubleshooting and Diagnostics

Investigated DNS name-resolution problems affecting Active Directory domain-controller discovery.

Diagnostic activities included:

- Reviewing DNS Server Event Viewer warnings 4013 and 4017.
- Running `dcdiag /test:DNS /v`.
- Correcting the DNS client configuration on the NAT network adapter.
- Checking DNS zone status and resource records using PowerShell.
- Successfully resolving the SOA record for `_msdcs.cts.test`.
- Verifying that the LDAP SRV record exists and targets `server01.cts.test` on port 389.

**Outstanding issue:** DNS queries for `_ldap._tcp.dc._msdcs.cts.test` continue to return NXDOMAIN despite the record appearing in the DNS database.

## 6. Current Results

Successfully deployed a Windows Server 2025 domain controller and established the Active Directory domain `cts.test`.

Verified several DNS configuration components, including zone availability and SOA resolution.

Full domain-controller DNS validation remains pending.

## 7. Skills Practiced

- Virtual machine deployment
- Windows Server installation
- Static IP addressing
- Active Directory Domain Services deployment
- Domain controller promotion
- DNS administration
- PowerShell diagnostics
- Windows Event Viewer troubleshooting
- Technical documentation

## 8. Next Steps

- Resolve the LDAP SRV DNS lookup issue.
- Complete domain-controller health validation.
- Organize and publish supporting screenshots.
- Begin Active Directory user, group, organizational unit, and Group Policy administration.

---

*This project was completed in a personal virtual lab for educational and professional development purposes.*
