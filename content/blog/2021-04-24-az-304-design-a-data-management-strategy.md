---
title: "AZ 304 | Design a Data Management Strategy "
date: 2021-04-24T19:04:58.715Z
description: "AZ 304 | Design a Data Management Strategy "
---
# AZ 304 Design a Data Management Strategy 

## Managed and Unmanaged Data solutions

- Why would you choose one vs the other ?

__Unmanaged Data (Unmanaged Storage Account)__

- Table Storage
- Blob Storage
- SQL Server in a VM 
- Oracle DB in a VM 

Aprrox. 5 Petabytes of data storage. There are some limits in terms of operations per second 

Even if we have a VM Running on a managed storage account but if we have an application installed in a VM and it has its own filesystem, data file format and logging files you will also be subjected to limits of those.

SQL Server in a VM has limits that need to be managed around, even if the VM is running in a managed storage account. Its like putting a filesystem on top of a managed file system.

__Managed Data (Managed Store)__

- VM Data Disk 
- Azure SQL Database
- Cosmos DB
- Azure Database for MySQL / PostgreSQL / Maria DB
- Managed SQL Server 
- Redis Cache 

Advantages of using Managed Storage option compared to that of unmanaged storage account -

Why choose Azure SQL database over SQL server in a VM 

- Built in High availability 
  - A single VM SQL server needs reboot or a server suffering hardware failure which is not a HA solution. High-Availability is an intentional effort that you make an intentional expense additional components to your solution designed to add resilience.
  - For using VM based SQL Server for High Availability you need multiple VMs, Availability Sets, Availability Zones, Cross region, Azure traffic manager etc
  - Azure SQL database has high availability built into it. Microsoft keeps Azure SQL database up as they manage it for us.

- Auto Scaling

  - For managed databases like Azure SQL and Azure Cosmos db you can define when you need higher performance tier during a day 

- Threat Detection 

  - Azure SQL database has built-in threat detection to detect malicious / strange activity 

- Auto tuning
  - Auto tuning is available in managed Azure Databases 


