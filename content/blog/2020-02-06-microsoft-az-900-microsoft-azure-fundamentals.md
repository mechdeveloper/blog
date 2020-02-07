---
title: >-
  Microsoft: AZ-900 | Microsoft Azure Fundamentals | Cloud Concepts | Module 1
  of 4
date: 2020-02-06T22:15:18.623Z
description: >-
  Microsoft: AZ-900 | Microsoft Azure Fundamentals | Cloud Concepts | Module 1
  of 4
---
# Microsoft Azure Fundamentals

References

[Microsoft Azure HomePage](https://azure.microsoft.com/en-us/)

[Microsoft Azure Documentation site](https://docs.microsoft.com/en-us/azure/)

## Module 1 | Cloud Concepts

### Lesson 1 - Learning Objectives

- Cloud services and their benifits
- key terms
- public private and hybrid cloud models
- IaaS Infrastructre as a service
- PaaS Platform as a service
- SaaS Software as a service

### Lesson 2 - Why Cloud Services?

- Characteristics of Cloud Services
  - High Availabiltiy
  - Scalability
  - Elasticity
  - Agility
  - Disaster Recovery
  - Global Reach
  - Security

- Consumption based model
  - You only pay for the resources you use !

#### Key Concepts and terms

##### What is cloud computing?

Cloud computing is the delivery of computing services—servers, storage, databases, networking, software, analytics, intelligence and more—over the internet (the cloud), enabling faster innovation, flexible resources, and economies of scale. You typically pay only for cloud services you use, helping lower your operating costs, run your infrastructure more efficiently, and scale as your business needs change.

- Characteristics of Cloud Services
  - High Availabiltiy

    The ability to keep services up and running for long periods of time, with very little downtime, depending on the service in question.

  - Scalability

    The ability to increase or decrease resources for any given workload. You can add additional resources to service a workload (known as scaling out), or add additional capabilities to manage an increase in demand to the existing resource (known as scaling up). Scalability doesn't have to be done automatically

  - Elasticity

    The ability to automatically or dynamically increase or decrease resources as needed. Elastic resources match the current needs, and resources are added or removed automatically to meet future needs when it’s needed, and from the most advantageous geographic location. A distinction between scalability and elasticity is that elasticity is done automatically

  - Agility

    The ability to react quickly. Cloud services can allocate and deallocate resources quickly. They are provided on-demand via self-service, so vast amounts of computing resources can be provisioned in minutes. There is no manual intervention in provisioning or deprovisioning services.
  
  - Fault tolerance

    The ability to remain up and running even in the event of a component or service no longer functioning. Typically, redundancy is built into cloud services architecture so if one component fails, a backup component takes its place. The type of service is said to be tolerant of faults.

  - Disaster Recovery

    The ability to recover from an event which has taken down a cloud service. Cloud services disaster recovery can happen very quickly with automation and services being readily available to use.

  - Global Reach

    The ability reach audiences around the globe. Cloud services can have presence in various regions across the globe which you can access, giving you a presence in those regions even though you may not have any infrastructure in that region.

  - Customer latency capabilities

    If customers are experiencing slowness with a particular cloud service, they are said to be experiencing some latency. Even though modern fiber optics are fast, it can still take time for services to react to customer actions if the service is not local to the customer. Cloud services have the ability deploy resources in datacenters around the globe, thus addressing customer latency issues.

  - Predictive cost considerations

    The ability for users to predict what costs they will incur for a particular cloud service. Costs for individual services are made available, and tools are provided to allow you predict what costs a service will incur. You can also perform analysis based on future growth.

  - Technical skill requirements and considerations

    Cloud services can provide and manage hardware and software for workloads. Therefore, getting a workload up and running with cloud services demands less technical resources than having IT teams build and maintain physical infrastructure for handling the same workload. A user can be expert in the application they want to run without having to need skills to build and maintain the underlying hardware and software infrastructure.

  - Increased productivity

    On-site datacenters typically require a lot of hardware setup (otherwise known as racking and stacking), software patching, and other time-consuming IT management chores. Cloud computing eliminates the need for many of these tasks, so IT teams can spend time on achieving more important business goals.

  - Security

    Cloud providers offer a broad set of policies, technologies, controls, and expert technology skills that can provide better security than most organizations can otherwise achieve. The result is strengthened security, which helps to protect data, apps, and infrastructure from potential threats.

  Resources

  [What is Cloud Computing?](https://azure.microsoft.com/en-us/overview/what-is-cloud-computing/)

  [Cloud computing Terms](https://azure.microsoft.com/en-us/overview/cloud-computing-dictionary/)

#### Economies of scale

The concept of economies of scale is the ability to do things more cheaply and more efficiently when operating at a larger scale in comparison to operating at a smaller scale.

Cloud providers such as Microsoft, Google, and AWS are very large businesses, and are able to leverage the benefits of economies of scale, and then pass those benefits on to their customers.

This is apparent to end users in a number of ways, one of which is the ability to acquire hardware at a lower cost than if a single user or smaller business were purchasing it.

Storage costs, for example, have decreased significantly over the last decade due in part to cloud providers' ability to purchase larger amounts of storage at significant discounts. They are then able to use that storage more efficiently, and pass on those benefits to end users in the form of lower prices.

There are limits to the benefits large organizations can realize through economies of scale. A product will inevitably have an underlying core cost, as it becomes more of a commodity, based on what it costs to produce . Competition is also another factor which has an effect on costs of cloud services.

#### CapEx Vs OpEx

Capital expenditure (CapEx) versus operational expenditure (OpEx)

In previous years, startup companies needed to acquire a physical premises and infrastructure to start their business and begin trading. Large amounts of money were need to get a new business up and running, or to grow an existing company. They would have to buy new datacenters or new servers to allow them build out new services, which they could then deliver to their customers. That is no longer the case.

Today, organizations can sign up for a service from a cloud provider to get up and running. This enables them to begin selling or providing services to their customers more quickly, without the need for significant upfront costs.

These two approaches to investment are referred to as:

- **Capital Expenditure (CapEx):** This is the spending of money on physical infrastructure up front, and then deducting that expense from your tax bill over time. CapEx is an upfront cost which has a value that reduces over time.

- **Operational Expenditure (OpEx):** This is spending money on services or products now and being billed for them now. You can deduct this expense from your tax bill in the same year. There is no upfront cost, you pay for a service or product as you use it.

Companies wanting to start a new business or grow their business do not have to incur upfront costs to try out a new product or service for customers. Instead, they can get into a market immediately and pay as much or as little for the infrastructure as the business requires. They also can terminate that cost if and when they need to.

If your service is busy and you consume a lot of resources in a month, then you receive a large bill. If those services are minimal and don't use a lot of resources, then you will receive a smaller bill.

A business can still use the CapEx expenditure strategy if they wish, but it is no longer a requirement that they do so.

#### Consumption-based model

Cloud service providers operate on a consumption-based model, which means that end users only pay for the resources that they use. Whatever they use is what they pay for.

This consumption-based model brings with it many benefits, including:

- No upfront costs
- No need to purchase and manage costly infrastructure that they may or may not use to its fullest
- The ability to pay for additional resources if and when they are needed
- The ability to stop paying for resources that are no longer needed



### Lesson 3 - Types of Cloud models

- Public cloud
  - Owned and operated by the cloud service provider
  - Provides resources and services to multiple organizations and users
  - connected over the internet
  - Public cloud characteristics include:
    - Resources are owned by the cloud service provider
    - Cloud Provider resposible for purchase, maintenance and management of cloud hardware
    - Made available to multiple organizations and users
    - Typically connected over the internet via a web browser
    - Accessible to the public
    - Doesnot require deep technical knowledge to start using public cloud
- Private cloud
  - Owned and operated by the organization that uses the resources
  - Organization using the services, is responsible for the operation of the cloud services
  - Private cloud characteristics
    - Owner and User of cloud services are the same
    - Owner is responsible for purchase, maintenance and management of cloud hardware
    - Operates in one organization and services typically used by a single organization
    - Connection is typically using a private network and is highly secure
    - Not accessible to the public
    - Requires deep technical knowledge to setup manage and maintain a private cloud
- Hybrid cloud
  - Combies the use of both Public and Private Clouds
  - Ability to run your applications in the most appropriate location
  - Hybrid Cloud characteristics include:
    - Ownership is split
    - Specific resources are run in the private cloud and others are run in the public cloud
    - Can access benefits of public cloud, such as cost, efficiency and scale
    - Can still maintain management control that comes with a private cloud model
    - Technical skills are still required to maintain the private cloud to ensure both models can inter-operate

#### Public Cloud

A public cloud is owned by the cloud services provider (also known as a hosting provider). It provides resources and services to multiple organizations and users, who connect to the cloud service via a secure network connection, typically over the internet.

Public cloud models have the following characteristics:

- **Ownership.** This is the resources that an organization or end user uses. Examples include storage and processing power. Resources do not belong to the organization that is utilizing them, but rather they are owned and operated by a third party such as the cloud service provider.
- **Multiple End Users.** Public cloud modes may make their resources available to multiple organizations.
- **Public Access.** This provides access to the public.
- **Availability.** This is the most common cloud-type deployment model.
- **Connectivity.** Users and organizations are typically connected to the public cloud over the internet using a web browser.
- **Skills.** Public clouds do not require deep technical knowledge to set up and use its resources.

With a public cloud, there is no local hardware to manage or keep up to date; everything runs on the cloud provider’s hardware. In some cases, cloud users can save additional costs by sharing computing resources with other cloud users.

A common use case scenario is deploying a web application or a blog site on hardware and resources that are owned by a cloud provider. Using a public cloud in this scenario allows cloud users to get their website or blog up quickly, and then focus on maintaining the site without having to worry about purchasing, managing or maintaining the hardware on which it runs.

Businesses can use multiple public cloud service provider companies of varying scale. Microsoft Azure is an example of a public cloud provider.

#### Private cloud

A private cloud is owned and operated by the organization that uses the resources from that cloud. They create a cloud environment in their own datacenter, and provide self-service access to compute resources to users within their organization. The organization remains the owner, entirely responsible for the operation of the services they provide.

Private cloud models have the following characteristics:

- **Ownership.** The owner and user of the cloud services are the same.
- **Hardware.** The owner is entirely responsible for the purchase, maintenance, and management of the cloud hardware.
- **Users.** A private cloud operates only within one organization and cloud computing resources are used exclusively by a single business or organization.
- **Connectivity.** A connection to a private cloud is typically made over a private network that is highly secure.
- **Public access.** Does not provide access to the public.
- **Skills.** Requires deep technical knowledge to set up, manage, and maintain.

A use case scenario for a private cloud would be when an organization has data that cannot be put in the public cloud, perhaps for legal reasons. For example, they may have medical data that cannot be exposed publicly.

Another scenario may be where government policy requires specific data to be kept in-country or privately.

A private cloud can provide cloud functionality to external customers as well, or to specific internal departments such as Accounting or Human Resources.

#### Hybrid cloud

A hybrid cloud combines both public and private clouds, allowing you to run your applications in the most appropriate location.

Hybrid cloud models have the following characteristics:

- **Resource location.** Specific resources run or are used in a public cloud, and others run or are used in a private cloud.
- **Cost and efficiency.** Hybrid cloud models allow an organization to leverage some of the benefits of cost, efficiency, and scale that are available with a public cloud model.
- **Control.** Organizations retain management control in private clouds.
- **Skills.** Technical skills are still required to maintain the private cloud and ensure both cloud models can operate together.

An example of a hybrid cloud usage scenario would be hosting a website in the public cloud and linking it to a highly secure database hosted in a private cloud.

Hybrid cloud scenarios can be useful when organizations have some things that cannot be put in a public cloud, possibly for legal reasons. For example, you may have medical data that cannot be exposed publicly.

Another example is one or more applications that run on old hardware that can’t be updated. In this case, you can keep the old system running locally in your private cloud, and connect it to the public cloud for authorization or storage.

Note: You can read more about Microsoft Azure Hybrid cloud options from the page [The only consistent and comprehensive hybrid cloud](https://azure.microsoft.com/en-us/overview/hybrid-cloud/)

#### Cloud model comparison

Below is an outline of some of the advantages and disadvantages for public, private, and hybrid clouds.

##### Public cloud

- Advantages:
  - **No CapEx.** You don’t have to buy a new server in order to scale.
  - **Agility.** Applications can be made accessible quickly, and deprovisioned whenever needed.
  - **Consumption-based model.** Organizations pay only for what they use, and operate under an OpEx model.
  - **Maintenance.** Organizations have no responsibility for hardware maintenance or updates.
  - **Skills.** No deep technical skills are required to deploy, use, and gain the benefits of a public cloud. Organizations can leverage the skills and expertise of the cloud provider to ensure workloads are secure, safe, and highly available.

- Disadvantages:
  - **Security.** There may be specific security requirements that cannot be met by using public cloud.
  - **Compliance.** There may be government policies, industry standards, or legal requirements which public clouds cannot meet.
  - **Ownership.** Organizations don't own the hardware or services and cannot manage them as they may wish.
  - **Specific scenarios.** If organizations have a unique business requirement, such as having to maintain a legacy application, it may be hard to meet that requirement with public cloud services.

##### Private cloud

- Advantages:
  - **Control.** Organizations have complete control over the resources.
  - **Security.** Organizations have complete control over security.
  - **Compliance.** If organizations have very strict security, compliance, or legal requirements, a private cloud may be the only viable option.
  - **Specific scenarios.** If an organization has a specific scenario not easily supported by a public cloud provider (such as having to maintain a legacy application), it may be preferable to run the application locally.

- Disadvantages:
  - **Upfront CapEx.** Hardware must be purchased for start-up and maintenance.
  - **Agility.** Private clouds are not as agile as public clouds, because you need to purchase and set up all the underlying infrastructure before they can be leveraged.
  - **Maintenance.** Organizations have the responsibility for hardware maintenance and updates.
  - **Skills.** Private clouds requires in-house IT skills and expertise that may be hard to get or be costly.

##### Hybrid cloud

- Advantages:

  - **Flexibility.** The most flexible scenario; with a hybrid cloud setup, an organization can decide to run their applications either in a private cloud or in a public cloud.
  - **Costs.** Organizations can take advantage of economies of scale from public cloud providers for services and resources as they wish. This allows them to access cheaper storage than they can provide themselves.
  - **Control.** Organizations can still access resources over which they have total control.
  - **Security.** Organizations can still access resources for which they are responsible for security.
  - **Compliance.** Organizations maintain the ability to comply with strict security, compliance, or legal requirements as needed.
  - **Specific scenarios.** Organizations maintain the ability to support specific scenarios not easily supported by a public cloud provider, such as running legacy applications. In this case, they can keep the old system running locally, and connect it to the public cloud for authorization or storage. Additionally, they could host a website in the public cloud, and link it to a highly secure database hosted in their private cloud.

- Disadvantages:
  - **Upfront CapEx.** Upfront CapEx is still required before organizations can leverage a private cloud.
  - **Costs.** Purchasing and maintaining a private cloud to use alongside the public cloud can be more expensive than selecting a single deployment model.
  - **Skills.** Deep technical skills are still required to be able to set up a private cloud.
  - **Ease of management.** Organizations need to ensure there are clear guidelines to avoid confusion, complications or misuse.




### Lesson 4 - Types of Cloud Services

#### Infrastructure-as-a-Service (IaaS)

IaaS is the most basic category of cloud computing services. With IaaS, you rent IT infrastructure servers and virtual machines (VMs), storage, networks, and operating systems from a cloud provider on a pay-as-you-go basis. It's an instant computing infrastructure, provisioned and managed over the internet.

IaaS has the following characteristics:

- **Upfront costs.** IaaS has no upfront costs. Users pay only for what they consume.
- **User ownership.** The user is responsible for the purchase, installation, configuration, and management of their own software operating systems, middleware, and applications.
- **Cloud provider ownership.** The cloud provider is responsible for ensuring that the underlying cloud infrastructure (such as virtual machines, storage and networking) is available for the user.

    Note: When using IaaS, ensuring that a service is up and running is a shared responsibility: the cloud provider is responsible for ensuring the cloud infrastructure is functioning correctly; the cloud customer is responsible for ensuring the service they are using is configured correctly, is up to date, and is available to their customers. This is referred to as the shared responsibility model.

Common usage scenarios:

- **Migrating workloads.** Typically, IaaS facilities are managed in a similar way as on-premises infrastructure, and provide an easy migration path for moving existing applications to the cloud.

- **Test and development.** Teams can quickly set up and dismantle test and development environments, bringing new applications to market faster. IaaS makes scaling development testing environments up and down fast and economical.

- **Website hosting.** Running websites using IaaS can be less expensive than traditional web hosting.

- **Storage, backup, and recovery.** Organizations avoid the capital outlay and complexity of storage management, which typically requires a skilled staff to manage data and meet legal and compliance requirements. IaaS is useful for managing unpredictable demand and steadily growing storage needs. It can also simplify the planning and management of backup and recovery systems.

    Note: For more information on IaaS see the page [What is IaaS?](https://azure.microsoft.com/en-us/overview/what-is-iaas/)

#### Platform-as-a-Service (PaaS)

PaaS provides an environment for building, testing, and deploying software applications. The goal of PaaS is to help create an application as quickly as possible without having to worry about managing the underlying infrastructure. For example, when deploying a web application using PaaS, you don't have to install an operating system, web server, or even system updates. PaaS is a complete development and deployment environment in the cloud, with resources that enable organizations to deliver everything from simple cloud-based apps to sophisticated cloud-enabled enterprise applications.

Resources are purchased from a cloud service provider on a pay-as-you-go basis and accessed over a secure Internet connection.

PaaS has the following characteristics:

- **Upfront costs.** There are no upfront costs, and users pay only for what they consume.
- **User ownership.** The user is responsible for the development of their own applications. However, they are not responsible for managing the server or infrastructure. This allows the user to focus on the application or workload they want to run.
- **Cloud provider ownership.** The cloud provider is responsible for operating system management, and network and service configuration. Cloud providers are typically responsible for everything apart from the application that a user wants to run. They provide a complete managed platform on which to run an application.

Common usage scenarios:

- **Development framework.** PaaS provides a framework that developers can build upon to develop or customize cloud-based applications. Similar to the way you create a Microsoft Excel macro, PaaS lets developers create applications using built-in software components. Cloud features such as scalability, high-availability, and multi-tenant capability are included, reducing the amount of coding that developers must do.
- **Analytics or business intelligence.** Tools provided as a service with PaaS allow organizations to analyze and mine their data. They can find insights and patterns, and predict outcomes to improve business decisions such as forecasting, product design, and investment returns.

    Note: For more information on PaaS see the page [What is PaaS?](https://azure.microsoft.com/en-us/overview/what-is-paas/)

#### Software-as-a-Service (SaaS)

SaaS is software that is centrally hosted and managed for the end customer. It allows users to connect to and use cloud-based apps over the internet. Common examples are email, calendars, and office tools such as Microsoft Office 365.

SaaS is typically licensed through a monthly or annual subscription, and Office 365 is an example of SaaS software.

SaaS has the following characteristics:

- **Upfront costs.** Users have no upfront costs; they pay a subscription, typically on a monthly or annual basis.
- **User ownership.** Users just use the application software; they are not responsible for any maintenance or management of that software.
- **Cloud provider ownership.** The cloud provider is responsible for the provision, management, and maintenance of the application software.

Common usage scenarios:

- Examples of Microsoft SaaS services include Office 365, Skype, and Microsoft Dynamics CRM Online.

    Note: For more information on SaaS see the page [What is SaaS?](https://azure.microsoft.com/en-us/overview/what-is-saas/)

#### Cloud service comparison

There are both advantages and disadvantages for IaaS, PaaS, and SaaS cloud services.

##### IaaS

Infrastructure as a Service is the most flexible category of cloud services. It aims to give you complete control over the hardware that runs your application. Instead of buying hardware, with IaaS, you rent it.

- Advantages

  - **No CapEx.** Users have no upfront costs.
  - **Agility.** Applications can be made accessible quickly, and deprovisioned whenever needed.
  - **Consumption-based model.** Organizations pay only for what they use, and operate under an OpEx model.
  - **Skills.** No deep technical skills are required to deploy, use, and gain the benefits of a public cloud. Organizations can leverage the skills and expertise of the cloud provider to ensure workloads are secure, safe, and highly available.
  - **Cloud benefits.** Organizations can leverage the skills and expertise of the cloud provider to ensure workloads are made secure and highly available.
  - **Flexibility:** IaaS is the most flexible cloud service as you have control to configure and manage the hardware running your application.

- Disadvantages

  - **Management.** The shared responsibility model applies; the user manages and maintains the services they have provisioned, and the cloud provider manages and maintains the cloud infrastructure.

##### PaaS

PaaS provides the same benefits and considerations as IaaS, but there some additional benefits.

- Advantages

  - **No CapEx.** Users have no upfront costs.
  - **Agility.** PaaS is more agile than IaaS, and users do not need to configure servers for running applications.
  - **Consumption-based model.** Users pay only for what they use, and operate on an OpEx model.
  - **Skills.** No deep technical skills are required to deploy, use, and gain the benefits of PaaS.
  - **Cloud benefits.** Users can leverage the skills and expertise of the cloud provider to ensure their workloads are made secure and highly available. In addition, users can gain access to more cutting-edge development tools and toolsets. They then can apply these tools and toolsets across an application's lifecycle.
  - **Productivity.** Users can focus on application development only, as all platform management is handled by the cloud provider. Working with distributed teams as services is easier, as the platform is accessed over the internet and can be made globally available more easily.

- Disadvantages

  - **Platform limitations.** There may be some limitations to a particular cloud platform that could affect how an application runs. Any limitations should be taken into consideration when considering which PaaS platform is best suited for a particular workload.

##### SaaS

SaaS is software that is centrally hosted and managed for the end customer. It is usually based on an architecture where one version of the application is used for all customers, and licensed through a monthly or annual subscription

SaaS provides the same benefits as IaaS, but again there some additional benefits.

- Advantages
  - **No CapEx.** Users don’t have any upfront costs.
  - **Agility.** Users can provide staff with access to the latest software quickly and easily.
  - **Pay-as-you-go pricing model**: Users pay for the software they use on a subscription model, typically monthly or yearly, regardless of how much they use the software.
  - **Flexibililty.** Users can access the same application data from anywhere.

- Disadvantages
  - **Software limitations.** There may be some limitations to a particular software application that might affect how users work. Any limitations should be taken into consideration when considering which PaaS platform is best suited for a particular workload.

##### Summary

IaaS, PaaS, and SaaS each contain different levels of managed services. You may easily use a combination of these types of infrastructure. You could use Office 365 on your company’s computers (SaaS), and in Azure you could host your VMs (IaaS) and use Azure SQL Database (PaaS) to store your data. With the cloud’s flexibility, you can use any combination that provides you with the maximum result.

#### Management responsibilities

The following list of cloud service types describes the management responsibilities for the user and the cloud provider as compared to on-premises systems:

- IaaS requires the most user management of all the cloud services. The user is responsible for managing the operating systems, data, and applications.
- PaaS requires less user management. The cloud provider manages the operating systems, and the user is responsible for the applications and data they run and store.
- SaaS requires the least amount of management. The cloud provider is responsible for managing everything, and the end user just uses the software.

Note: It is important that users understand what they are responsible for, when using cloud services, to ensure their workloads are managed correctly and don't suffer any down time. There is a shared responsibility model for ensuring cloud workloads are run securely and in a well-managed way. Depending on the service you are using: the cloud provider is responsible for some aspects of the workload management, and the end user is responsible for other aspects of the workload management.



### Lesson 5 - Module 1 Review Questions

Review Question 1
(Choose three)
What terms from the list below would be viewed as benefits of using cloud services?

- [x] Elasticity
- [ ] Un-predictable costs
- [ ] Local reach only
- [x] Agility
- [x] Economies of Scale

Explanation

Elasticity, Agility and Economies of scale are the correct answers, and would be seen as benefits that you can gain from using cloud services.
All other answers are incorrect.
Un-predictable costs and local reach only would not be benefits of using cloud services because cloud services does provide predictable costs and global reach.

Review Question 2
When looking at using a cloud service, what expenditure type are cloud services based on?

- [ ] Capital Expenditure (CapEx)
- [ ] Friendly expenditure
- [ ] Maximun expense
- [x] Operation Expenditure (OpEx)

Explanation

Operational Expenditure (OpEx) is the correct answer. Cloud services operate on an Operational Expenditure model. It is regular, repeated expenditure that you pay for using cloud services.
Capital Expenditure (CapEx) is not the correct answer. Capital Expenditure (CapEx) is not required to be paid upfront when looking to start using a cloud services. There are no up front costs to use cloud services. You pay for what you consume, under a consumption based model.
Friendly expenditure and Maximum expense are not defined expenditure types.

Review Question 3
Which of the following terms relate to making a service available with no downtime for an extended period of time?

- [ ] Performance
- [x] High Availabilty
- [ ] Fault Tolerance
- [ ] Agility

Explanation

High Availability is the correct answer. The other answers, while they may be related, are not correct.
Performance is the ability to provide quick and efficient response times to requests.
Fault Tolerance is the ability to survive a failure of a component.
Agility is the ability to react quickly.

Review Question 4
(choose two)
Which cloud models provide services that can be accessed by the public?

- [x] Public
- [ ] Private
- [x] Hybrid
- [ ] Global

Explanation

Public and Hybrid cloud models use services that can be accessed by the public.
Hybrid cloud has a public and private element, hence the public part is accessible by the public.
Private cloud models is run and owned by an organization for use exclusively for that organization and access is not provided to the public. It may be made available to other 3rd parties depending on the business requirements.
Global is not a valid cloud model.

Review Question 5
Which cloud model provides the greatest degree of ownership and control?

- [ ] Public
- [x] Private
- [ ] Hybrid

Explanation

Private cloud models is the correct answer.
Both public and hybrid clouds have an infrastructure that is managed by another party. As such, there is less control over the infrastructure.

Review Question 6
Which cloud model provides the greatest degree of flexibility?

- [ ] Public
- [ ] Private
- [x] Hybrid

Explanation

Hybrid cloud model provides the greatest degree of flexibility, as you have the option to choose either public or private depending on your requirements.
Public cloud means you will not have full ownership over all aspects of the service.
Private cloud means there is upfront costs associated with creating, managing and maintaining your private cloud.

Review Question 7
You are running a virtual machine in a public cloud using IaaS. Which model correctly reflects how that resource is managed?

- [ ] user management model
- [ ] cloud user management model
- [ ] no resposibility model
- [x] shared responsibility model

Explanation

The shared responsibility model is the correct answer. Under the shared responsibility model, management of the resource is shared between the cloud provider and the end user. The cloud provider being responsible for the cloud services infrastructure and the end user being responsible for the service being configured and managed correctly.
The user management model, cloud user management model and no responsibility management model are not valid defined management models.

Review Question 8
Which term best describes PaaS?

- [x] Users can create and deploy an application as quickly as possible without having to worry about managing the underlying infrastructure
- [ ] Users are responsible for purchasing, installing, configuring and managing their own software - Operating Systems, middleware, and applications
- [ ] Users pay an annual or monthly subscription

Explanation

The correct answer is that the users can create and deploy an application as quickly as possible without having to worry about managing the underlying infrastructure
Users are responsible for purchasing, installing, configuring, and managing their own software—operating systems, middleware, and applicationsapplies to IaaS.
Users pay an annual or monthly subscriptionis applicable to SaaS services.

Review Question 9
You have two types of applications which you need to run: legacy applications that require specialized mainframe hardware and newer applications that can run on commodity hardware. Which cloud deployment model would be best for you?"

- [ ] Public cloud
- [ ] Private cloud
- [ ] Hybrid cloud
- [ ] On-Premises

Hybrid cloud is the correct answer.
A hybrid cloud is a public and private cloud combined. You can run your new applications on commodity hardware you rent from the public cloud and maintain your specialized mainframe hardware on-premises

### Lesson 6 - Module 1 Summary

In this module you've learned about cloud computing, what it is and what its key characteristics are. You learned about the different types of cloud models that are available and the considerations of using those different models. You also learned about the different cloud services available, the benefits of using the different types, and the management responsibilities under each service type.

#### Why cloud services?

In this lesson you have learned about what cloud computing is, and why you should consider using cloud services. You've learned what some of the key terms and concepts are, such as high availability, agility, elasticity, fault tolerance, global reach, CapEx versus OpEX in the context of cloud computing, economies of scale, and the consumption-based cost model.

#### Types of cloud models

In this lesson you have learned about public cloud, private cloud, and hybrid cloud models, and what the key characteristics of each model are. You've also learned how they compare, what considerations you need to take into account when using them, and when you might use them.

#### Types of cloud services

In this lesson you have learned about the different types of cloud service available, IaaS, PaaS, and SaaS. You've learned what the key characteristics of each service are, how they compare, what considerations you need to take into account when using them, and when you might use them.
