---
date: "2020-09-08T22:11:57.883Z"
description: first page
title: AMS4
weight: 1

---

# 1. **AMS** (*Asset Management Server*) for **ThinC-AUTH** Biometric Security Keys

As the Enterprises procuring the FIDO2 Security Keys and are sharing them with their Users & other stakeholders to ensure secure passwordless authentication, Ensurity has developed AMS for its’ ThinC-AUTH Biometric Security Keys. The AMS helps enterprises in managing the inventory of the Security Keys and assigning them with enterprise Users. 

<table><tr><td>Ensurity provides complete life-cycle for its' FIDO2 Biometric Security Key, which helps Enterprise to meet their authentication requirements.</td></tr></table>

## 1.a  AMS Features:

- Easy Inventory Management of ThinC-AUTH Biometric Security Keys
- Identity/User syncing with Enterprise's AzureAD
- Assign Roles to the AAD Users (Admin / Service Desk / Generic User)
- Send an automatic eMail to the User about the Device assignment status
- Provision for Enterprise Admin to Assign/Unassign the ThinC-AUTH Security Key to the User
- Remotely Reset the ThinC-AUTH for removing the Fingerprint Data of previous User
- Provision to set a choice of maximum fingerprints for the enrolment
- Device Log (fingerprint enrolment status on the Security Key)
- Event & Audit Logs (who logged in to the AMS portal and what they performed)
- Export the filtered Logs to Excel files
- Dashboard with a GUI to display the following in a line chart 
  - Total Number of Users
  - Total Number of Security Keys
  - Number of Security Keys assigned to Users
  - Number of Security Keys enrolled with User fingerprints (including the number fingerprints)
  - Number of Security Keys assigned to Users, but not enrolled


# 2.  Deployment Procedure

Ensurity shall deploy AMS within Enterprise Datacenter/Cloud. The recommended server hardware & software are explained below.

##  2.1  Prerequisites

AMS portal contains the following modules. Both these modules will be hosted at Enterprise datacenter or private/public cloud.
- AMS Application Portal
- AMS Database Module

###  2.1.A.  Server H/W configuration:

The following hardware configuration is recommended for both 'AMS Application' and 'AMS Database' modules. Both the AMS modules can be hosted in a single hardware server platform, and Enterprises should plan for scalability and high-availability, according to their requirements.
- Intel i7 / Xeon CPU, 16GB RAM, Hard Disk 
- 1Gbps Network Interface

###  2.1.B.  Server S/W for AMS Application & Database Modules:

The following software modules are recommended to host the AMS in enterprise datacenter.

|<p align="center">AMS Application Module</p>       |<p align="center">AMS Database Module</p>        |
|---------------------------------------------------|-------------------------------------------------|
|- MS Windows Server 2016+ (IIS with ARR facility)  |- MS SQL Database Server 2016+                   |
|- dotNet Hosting 3.1.5                             |- DB User Access with respective user permission |
|- dotNet Core 3.1.0                                |- Notepad++ zip                                  |
|- IIS website creation and manage permissions      |                                                 |
|- IIS URL Rewrite executable                       |                                                 |
|- Chrome standalone installer                      |                                                 |
|- Notepad++ zip                                    |                                                 |
|- Self-signed SSL certificate<sup>$</sup>          |                                                 | 

> *<sup>$</sup>(recommended to use Organizations’s SSL certificate and if unable to provide, a self-signed SSL will be used).*

###  2.1.C.  SMTP Relay Servers

As the AMS portal automatically sends an eMail to the User about the `Security Key` assignment status, Enterprise should provide a `SMTP Relay Server`, with support for sending bulk eMails.

> Please note that generic Gmail and Outlook based SMTP servers do not support for sending bulk eMails. The proposed SMTP Relay Server must support sending bulk eMail. 

###  2.1.D.  Network & Firewall Settings

The AMS portal uses the following network ports for the secure communication. Enterprise Admin must configure their network & firewalls accordingly.

- `Port # 443` *(for accessing AMS portal)*
- `Port # 8443` *(for the secure communication between `AMS Portal` (Server) and `AUTH Manager Tool` (user-side))*
- `Port # 1443` *(for accessing/connecting AMS Database Server)*
- **_Optional_** RDP Ports # `3389` & `3390` for both AMS Application & Database Servers *(for the remote management by Ensurity, if required)* 


##  2.2  Integrating AMS with AzureAD for User Identities

To sync the Identity/Users of AzureAD, Enterprise Admin must configure the AAD to generate a `Tenant ID`, `ClientID`, and `Client Secret`. These values must be configured to the AMS portal to sync the AAD Users. For reference, the configuration settings *(dummy)* are depicted below: 

###  2.2.A.  Process to Sync Users

i. 