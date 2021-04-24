---
title: "AZ 304 | Relational and NoSQL Database Strategy "
date: 2021-04-24T19:50:36.026Z
description: "AZ 304 | Relational and NoSQL Database Strategy "
---
# AZ 304 Relational and NoSQL Database Strategy

## Data Management Strategy 

### Relational and NoSQL Database Strategy

__Relational vs NoSQL__

- Non Relational Databases are referred as NoSQL
- Relational database can be queried with SQL query language where as non-relational databases use different document formats

__Relational Databases (SQL)__

- Primary Key 
- Foreign key setting up relationships b/w data tables 
- Normalization - breakdown large data tables to smaller components 
- Maintenance overhead for INSERT, DELETE 
- SELECTS require JOINS 
- Transactional data, consistency, integrity 
- Supports reporting and analytics 
- Difficult to partition and/or replicate 

__Non Relational Databases (NoSQL)__

Many Kinds 
- Key-value pairs
- Graph stores
- Column stores
- Document stores 

- Highly scalable (billions and trillions of items)
- Fast
- Supports flexible schema
- Not as rigid
- Not as feature rich 

#### Lift and shift migrations 

- Relational Database are good for lift and shift. backup and restore in cloud 

#### OLTP - Online Transaction Processing 

- Relational Database are also good for OLTP - Online Transaction Processing Type applications 
- For a bank Relational database makes sense as Speed is not primary consideration its the integrity of it.

#### Modern databases for Web Applications 

- NoSQL databases are great for Web Apps 


## Database Auditing Strategy 

### Data Auditing and Caching 

- Written to append blobs
  - SQL database tracks events to an audit log, written to append blobs
- Server level vs database level auditing 
  - SQL database has server + Multiple databases running on a single server 

### Azure Monitor 

- Azure Monitor is central dashboard for monitoring and reporting within Azure
- Azure Monitor has hooks into SQL database and can be used for alerting, reporting 

### Also Available as SQL Server system function 
- You can write your own reports and send notification 

### Also Available in PowerBI
- Pull events in PowerBI for reporting monitoring and auditing 


## The concept of DTUs

Different Pricing Options 
- vCore based (CPU and Memory)
- DTU (Performance)

### DTU - Database Transaction Unit 

- No concept of "CPU, RAM, OS disk size, IOPS"
- DTU - A Relative Measure of performance 
  - 100 DTU is expected to be twice as powerful as 50 DTU

## The concept of RU/s

- Cosmos DB is priced based on two factors 
  - Storage (25 cents per GB per Month)
  - Provisioned throughput RU/s
    - you decide in advance the bandwidth/speed for database transactions - Request Unit per second (RU/s)
  - No concept of "CPU, RAM, OS disk size, IOPS"
  - You reserve capacity, You provision a RU in advance and pay for that (in increments of 100) 

## Data Retention Strategy 

- Automatic geo-redundant backups 
- Point in Time Restores
  - Configure for 7 to 35 days 
- Long term retention policy up to 10 years
- Restore deleted database 
- Restore to another region 

## Data Availability, Consistency and Durability 

- Availability involves removing single points of failure 
  - Typically involves having replicated copies in other locations
  - Replication introduces possibility of being out of sync (Consistency levels)
  - Write a record to DB 1, and when you read DB2 it's old version 
- Cosmos DB - you can define consistency levels
  - consistency comes with tradeoffs 
    - Strong consistency then its going to suffer in terms of performance 
    - Strong performance then it can suffer in terms of consistency 
- Durability is the idea that if you write something to the DB, you never ever lose it
  - Committed right should be unlosable

- Availability, Consistency, Durability -- These things must be planned for 
- Azure SQL Database Business Critical Tier 
  - Extra support 
  - Azure SQL Database SLA
    - "Auzre SQL Database Business Critical Tier configured with geo-replication has a guarantee of __Recovery point objective (ROP) of 5 sec for 100% of deployed hours.__"
      - If SQL DB Fails most you gonna (loose Max data loss) is 5 seconds of data
    - "Azure SQL Database Business Critical Tier configured with geo-replication has a guarantee of __Recovery time objective (RTO) of 30 sec for 100% of deployed hours.__"
      - You will be up and running in other region within 30 seconds from the point you declare failure


## Data Warehouse Strategy 

- Used for analytics 
- Not used for transaction
- Does not support updates, deletes 
  - Taking data from different sources and putting it into single large dataset and that is optimized for reporting but its not a transactional database so its not supposed for transactions, once data is imported its not changeable 

- Roll up databases from your OLTPs 
  - If you have got multiple databases around the world and you want to pull them into a single data store for Analytics, Power BI its recommended to use data warehouses

- Data Warehouse leads to Azure Analysis Services, PowerBI, Big Data 




