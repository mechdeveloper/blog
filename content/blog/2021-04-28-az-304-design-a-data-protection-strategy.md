---
title: "AZ 304 | Design a Data Protection Strategy "
date: 2021-04-25T18:28:11.407Z
description: "AZ 304 | Design a Data Protection Strategy "
---
# AZ 304 Design a Data Protection Strategy

## Data Geo-Replication

* One of the big advantages of cloud computing is the global nature of it 
* When you create a virtual machine you can create it in any region of the world 
* You can create multiple virtual machines in multiple regions of the world and you can get global distribution for your applications and even your storage files and other things

### Geographic Data Storage

* One of the challenges of being global - application is having data (your databases) are located globally and replicated globally. This is the concept of geographic data storage 

### Geo-redundant storage (GRS)

* Storage accounts give you the option of having your files globally replicated 
* Advantage of this is if there's a regional outage let's say there's a massive storm, with geo-redundant storage your files are located in another region of the world which you can get running and your applications will work in new region while your primary region comes back online
* The same ability of doing geo redundant storage for storage accounts is available for Azure SQL database and Cosmos DB as well.
* With Azure SQL database you can choose a second third or fourth or even more region of the world where azure will keep a copy of your full database, Azure will also replicate that data from your primary location to these backup locations.
* Same is with Cosmos DB, you choose your primary location, you can choose secondary location and azure takes care of synchronization. You can do this in multi master configuration where you know the North American Cosmos DB receives data inserts and stores the table and the European Cosmos DB also does that and Azure takes care of making sure that all data is replicated everywhere and takes care of handling conflicts if that happen

![App Design with HA Data Configuration](/img/azuredataha.png "App Design with HA")

* Database have Geo-Replication 

## Data Encryption

* Encryption Strategy 
* Azure SQL Database and Cosmos DB - Data is encrypted on the disk already. This is called Transparent Data Encryption (TDE) . Data files are encrypted on disk natively.
* You can also control the encryption keys for data at rest using Azure Key Vault 
* Data encrypted in transit using SSL, Force SSL connection - only allow SSL connection
* Always Encrypted - requires a special client to read data from SQL database. Data is never decrypted untill it gets onto your computer. 
* Dynamic Data Masking - never show for example email address except for admin purposes - you can setup dynamic data masking on that field (never store credit card in data table in a plain text - a bad practice) 

## Data Scaling

### Scalability Strategy

![Azure Data Scalability Strategy ](/img/azuredatascalabilitystrategy.png "Azure Data Scalability Strategy ")

## Data Security

### Secure Access to Data 
- Network level security 
- Virtual Network Service Endpoints - Restricting Azure SQL database and Cosmos DB to a specific virtual network 
- SQL Database Firewall - Both at server and database level 
- SQL authentication vs Azure AD
  - you can create application with a managed service identity with in Azure AD to authenticate with SQL Database in Azure
- Row Level Security is also available
- Threat Protection - ATP - Additional (Not Free), checks the traffic coming through against some known patterns of bad behavior 
- Azure Monitor access to logs 
- Encrypted in transit (TLS/SSL) 
- Dynamic Data masking to protect sensitive field

## Data Loss Prevention (DLP)

- Policies designed to prevent data loss 
- Identify sensitive data 
- Standards 
  - PII - Personally Identified Information 
  - PCI - Payment Card Industry Data Standard PCI DSS
    - Dealing with credit cards - look into PCI standard
- Do-not store what you don't need
- Don't store passwords in plain text, Hide the encryption key !
- Hash it, encrypt it
- Principle of Least Privilege, Don't give too many permissions 
- Access Review to review the permissions of existing users
- Enable a temporary access 
- Azure Information Protection - DRM - Digital Rights Management system for your information for your documents and for data.
- GDPR - has data controller and processor 