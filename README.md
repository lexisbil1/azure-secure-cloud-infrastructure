# Azure Secure Cloud Infrastructure for ApexLearn Services

![Azure](https://img.shields.io/badge/Microsoft%20Azure-Cloud-blue)
![Security](https://img.shields.io/badge/Focus-Cloud%20Security-red)
![Status](https://img.shields.io/badge/Status-Completed-success)

## Overview

This project demonstrates the design, deployment, security hardening, monitoring, validation, and operational management of a secure Microsoft Azure cloud environment for ApexLearn Services.

The project was completed as part of the ICDFA Cloud Security Engineering Program and focuses on applying practical Azure security and cloud engineering principles.

## Objectives

* Implement secure Azure networking
* Apply identity and access management using Microsoft Entra ID and Azure RBAC
* Deploy and harden an Ubuntu Linux workload
* Implement passwordless authentication using Managed Identity
* Secure secrets with Azure Key Vault
* Protect business data using Azure Storage
* Implement monitoring and auditing
* Validate security controls
* Apply cost optimization and operational governance

## Architecture

The solution uses a layered security architecture consisting of:

```text
Internet
   |
   | SSH - Restricted to Administrator IP
   |
Network Security Group
   |
Azure Virtual Network
   |
   +-----------------------+
   |                       |
Management Subnet     Workload Subnet
                           |
                     Ubuntu VM
                           |
                    Managed Identity
                      /         \
                     /           \
              Key Vault       Storage
                     \           /
                      \         /
                    Azure Monitor
                         |
                    Activity Log
```

## Azure Resources

| Resource          | Name                 |
| ------------------ | -------------------- |
| Resource Group     | `rg-apexlearn-devv`  |
| Region              | Spain Central         |
| Virtual Network     | `vnet-apexlearn`     |
| Management Subnet  | `snet-management`    |
| Workload Subnet    | `snet-workload`      |
| Management NSG     | `nsg-management`     |
| Workload NSG        | `nsg-workload`       |
| Virtual Machine     | `vm-apex-admin01`    |
| VM OS               | Ubuntu 24.04 LTS      |
| VM Size             | Standard D2s v3       |
| Storage Account     | `stapexlearnalex01`  |
| Key Vault           | `kv-apexlearn`       |
| Managed Identity    | `mi-apexlearn`       |

## Security Controls

### Identity

* Microsoft Entra ID
* Azure RBAC
* User-assigned Managed Identity
* Least-privilege access

### Network

* Azure Virtual Network
* Subnet segmentation
* Network Security Groups
* SSH restricted to administrator IP

### Data Protection

* Private Blob Container
* Anonymous access disabled
* Secure transfer required
* TLS 1.2
* Azure Key Vault

### Monitoring

* Azure Monitor
* Activity Log
* Alert rules
* Microsoft Defender for Cloud recommendations

## Security Validation

The following controls were validated:

| Control                          | Result   |
| --------------------------------- | -------- |
| SSH restriction                   | Passed   |
| RBAC configuration                | Passed   |
| Storage privacy                   | Passed   |
| Managed Identity authentication   | Passed   |
| Key Vault secret retrieval        | Passed   |
| Activity Log auditing             | Verified |
| Azure Monitor alerting            | Verified |

## Troubleshooting Experience

Several issues were encountered and successfully resolved during implementation:

### SSH Connection Timeout

SSH access initially failed because port 22 was unreachable. Network Security Group configuration and connectivity settings were reviewed and corrected.

### Key Vault Secret Not Found

Secret retrieval initially failed. Key Vault and secret configuration were reviewed and corrected.

### Key Vault Not Visible Through Azure CLI

The `az keyvault list` command initially returned no resources. Azure CLI subscription context, authentication, and permissions were reviewed.

### Storage Authorization Failure

The VM's Managed Identity initially lacked the required permissions to access Storage. Appropriate RBAC permissions were configured and access was subsequently validated.

Microsoft documentation was used throughout the troubleshooting process.

## Cost Optimization

The project was deployed using an Azure for Students subscription.

Cost-conscious design decisions included:

* Standard LRS storage
* Single VM deployment
* VM auto-shutdown
* Free Defender for Cloud recommendations
* Avoidance of unnecessary premium services
* Resource cleanup after project completion

## Lessons Learned

This project provided practical experience in:

* Azure cloud architecture
* Cloud security
* Azure networking
* Microsoft Entra ID
* Azure RBAC
* Managed Identities
* Azure Key Vault
* Azure Storage
* Azure Monitor
* Cloud troubleshooting
* Security validation
* Cost optimization

The most important lesson was that cloud security requires a layered approach. Identity, network, workload, data, monitoring, and operational controls must work together to provide effective protection.

## Documentation

Additional project documentation is available in the `documentation/` directory.

* Executive Project Report
* Resource Cost Sheet
* RBAC Permission Matrix
* Network Rule Matrix
* Risk Register
* Test Register
* Incident Response Action Card

## Evidence

Security validation screenshots and supporting evidence are organized in the `evidence/` directory.

Sensitive information such as credentials, private keys, secrets, and other confidential values must not be committed to this repository.

## Project Status

**Completed and Operational**

Built as part of the ICDFA Cloud Security Engineering Program.
