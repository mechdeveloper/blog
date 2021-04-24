---
title: "AZ 304 | Design a Monitoring Strategy for Identity and Security "
date: 2021-04-24T18:43:37.542Z
description: "AZ 304 | Design a Monitoring Strategy for Identity and Security "
---
# AZ 304 Design a Monitoring Strategy for Identity and Security

- Monitoring Strategy 
- Alert Notifications 

## Azure AD Privileged Identity Management (PIM) 
- Azure AD Privileged Identity Management (PIM) has an alert feature 
- Five pre-defined alerts (predefined set of potential policy violations) 
  - Roles are being assigned outside of PIM 
  - Admins not using their privileged roles 
  - Too many global admins 
  - Roles don't require multi-factor authentication for activation 
  - Potential stale accounts in a privileged role (Preview) 
- We can customize values that trigger alerts 

## Other ways to monitor the security of identity 

- Alerts and Metrics strategy 
- Identity is the secure doorway into your application 

- Start from Very beginning 
- On premises Active Directory 
- AD Connect - Synchronization tool b/w on-prem AD to Azure AD
- AD Connect health -- to make sure that it is working and secure
- Getting various reports about AD Connect about how sync is going 

## Log Analytics 

- Log Analytics allows access to various security logs 

## Patching, Anti-Virus, Firewall etc.

- Making sure you are running firewalls antivirus
- Making sure all of the software's you are using is upto date in terms of the latest patches 