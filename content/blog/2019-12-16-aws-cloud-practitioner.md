---
title: AWS Cloud Practitioner
date: 2019-12-16T00:42:26.260Z
description: AWS Certification preparation | AWS Cloud Practitioner
---
# AWS
## AWS Cloud Practitioner
[freeCodeCamp.org YouTube Video Link](https://www.youtube.com/watch?v=3hLmDS179YE)

- 90 Minutes
- 65 Questions
- 70% Passing Score
- Valid for 3 Years

### Exam Guide
- Cloud Concepts        28%
- Security              24%
- Technology            36%
- Billing and Pricing   12%


### Cloud Concepts

#### Cloud Computing
Cloud computing is the practice of using a network of remote servers hosted on the Internet to store, manage, and process data, rather than a local server or a personal computer.

#### Six advantages and Benifits of Cloud Computing
1. Trade capital expense for variable expense
   - No Upfront cost
   - Pay on-Demand
2. Benifit from massive economies of scale 
   - Sharing the cost with other customers to get unbeatable savings
3. Stop guessing capacity 
   - Instead of paying for idle or underutilized servers, you can scale up or down to meet the current need.
4. Increase speed and agility
   - Launch resources within a few clicks in minutes.
5. Stop spending money on runing and maintaining data centers
   - Focus on your own customers
6. Go global in minutes
   - Deploy your app in multiple regions around the world with a few clicks. Provide low latency and a better experience for your customers at minimal cost.

### Types of cloud computing 
- SaaS
  - Software as a Service For Customers
  - A completed product that is run and managed by the service provider
  - Don't worry about how service is maintained. it just works and remains available.
    - Gmail
    - Office 365
    - SalesForce
	  
- PaaS
  - Platform as a Service For Developers
  - Removes the need for your organization to manage the underlying infrastructure. Focus on the deployment and management of your applications.
  - Don't worry about, provisioning, configuring or understanding the hardware or OS
    - AWS Elastic Beanstalk
    - Heroku
    - Google App Engine
- IaaS
  - Infrastructure as a Service For Admins
  - The basic building blocks for Cloud IT. Provides access to networking features, computers and data storage space.
  - Don't worry about IT staff, data centers and hardware
    - AWS
    - Google Cloud Platform
    - Microsoft Azure

#### Cloud Computing Deployment Models
- Cloud
  - Fully utilizing cloud computing
    - Startups 
    - SaaS offerings
      - New projects and companies
  
- Hybrid
  - Using both Cloud and On-Premise
    - Banks
    - Fintech, Investment Management
    - Large Professional Service providers
    - Legacy on-premise
	
- On-Premise
  - Deploying resources on-premise using virtualization and resource management tools, is sometimes called "Private Cloud"
    - Public Sector eg. Government
    - Super Sensitive Data eg. Hospitals
    - Large Enterprise with heavy regulation eg. Insurance companies

### AWS Global Infrastructure
Where does all this Cloud Computing Run?
  - 69 __Availability Zones__ with in 22 __Geographical Regions__ around the world 
  - Way more __Edge Locations__ than AZs!

- AWS serves over a million active customers in more than 190 countries
- Steadilty exanding global infrastructure to help customers achieve lower latency and higher throughput

- __Regions__ - physical location in the world with multiple Availability Zones
- __Availability Zones__ - one or more discrete(individually separate and distinct) data centers own by AWS 
- __Edge Locations__ - datacenter owned by a trusted partner of AWS

#### Regions
- A __geographically distinct__ location which has multiple datacenters (AZs)
- Every region is __physically isolated__ from and independent if every other region in terms of location, power, water supply
- Each region has at least two AZs
- AWS Largest region is __US-EAST__
- New services almost always become available first in __US-EAST__
- Not all services are available in all regions 
- __US-EAST-1__ is the region where you see all your billing information
- https://aws.amazon.com/about-aws/global-infrastructure/

#### Availability Zones
- An AZ is a datacenter owned and operated by AWS in which AWS services run
- Each region has atleast two AZs
- AZs are represented by a Region Code, followed by a letter identifier eg. __us-east-1a__
- __Multi-AZ__ distributing your instances across multiple AZs allows failover configuration for handling requests when one goes down.
- <10ms latency between AZs

#### Edge Locations 
Get Data Fast or Upload Data Fast to AWS
- An Edge location is a datacenter owned by a trusted owner by a trusted partner of AWS which has __direct connection__ to the AWS network.
- These location serve requests for __CloudFront__ and __Route53__. Requests going to either of these services will be routed to the nearest edge location automatically.
- __S3 Transfer Acceleration__ traffic and __API Gateway__ endpoint traffic also use the AWS Edge Network.
- This allows for __low latency__ no matter where the end user is geographically located.

#### GovCloud  Regions
- AWS GovCloud Regions allow customers to host sensitive __Controlled Unclassified Information__ and other types of regulated workloads.
- GovCloud Regions are only operated by employees who are U.S. citizens, on U.S. soil.
- They are only accessible to U.S. entities and root account holders who pass a screening process.
- Customers can architect secure cloud solutions that comply with:
  - FedRAMP High baseline
  - DOJ's Criminal Justice Information Systems (CJIS) Security Policy
  - U.S. International Traffic in Arms Regulations (ITAR)
  - Export Administration Regulations (EAR)
  - Department of Defence (DoD) Cloud Computing Security Requirements Guide


### Getting Started

#### Create an AWS Account (https://aws.amazon.com/)

#### Billig Preferences, Budgets and Alarms
- My Billing Dashboard
- AWS Budgets
- Billing Ararm in Cloud Watch

#### Change IAM Users Sign-in Link
- Services > IAM
- https://mechdevelopers.signin.aws.amazon.com/console

#### Activate MFA on Root Account
- Setup MFA, Android Authy applications
- Create Individual IAM User

#### Set a password policy
IAM > Account Settings


### Hands On

#### Intro and Regions
#### EC2 
#### Sessions Manager
#### AMI
#### Auto Scaling Groups
#### Elastic Load Balancer
#### S3
#### CloudFront
#### RDS
#### Lambda





### EC2 Pricing Models

#### Introduction
#### On-Demand
#### Reserved
#### Spot
#### Dedicated
#### EC2 Pricing Sheet


### Billing and Pricing

#### Free Services
#### AWS Support Plans
#### Follow Along - Lets create a support case
#### AWS Marketplace
#### Follow Along - Marketplace subscription
#### AWS Trusted Advisor
#### Consolidated Biling
#### Consolidated Billing Volume Discounts
#### AWS Cost Explorer
#### AWS Cost Explorer Follow Along
#### AWS Budgets 
#### AWS Budgets Follow Along
#### TCO Calculator
#### RCO Calculator Follow Along
#### AWS Landing Zone
#### Resource Groups and Tagging
#### Resource Groups Follow Along
#### AWS QuickStart
#### AWS Cost and Usage Report
#### Cost and Usage Follow Along


### Technology Overview

#### AWS Organizations and Accounts
#### AWS Organizations Follow Along
#### AWS Networking
#### Database Services
#### Provisioning Services 
#### Computing Services 
#### Storage Services
#### Business Centric Services 
#### Enterprise Integration
#### Logging Services 
#### Know your Intitialisms

### Security

#### Shared Responsibility Model
#### AWS Compliance programs
#### AWS Artifact
#### AWS Artifact Follow Along
#### Amazon Inspector
#### AWS WAF
#### AWS Shield
#### Penetration Testing 
#### Guard Duty
#### Key Management Service
#### Amazon Macie
#### Security Groups vs NACLs
#### AWS VPN

### Variation Study

#### Cloud* Service
#### *Connect Service
#### Elastic Transcoder vs Media Convert
#### SNS vs SQS
#### Inspector vs Trusted Advisor
#### ALB vs NLB vs CLB
#### SNS vs SES
#### Artifact vs Inspector

### Summary
#### Journey's End
#### Booking your Exam

