---
title: "AZ 304 | Design Authorization "
date: 2021-04-18T23:56:13.499Z
description: AZ 304 - Design Authorization Notes
---
# Design Authorization

## Authorization 
- What can a user do after getting authenticated

Person 
Application 
  - Batch jobs 

## Azure AD

Identity Manager in Azure AD has the ability for you to grant people and to grant other applications, level of permissions that they need.

Generally there are following models

### Role Based 

Developer, Manager, Administrator Being part of these roles gets you permission to do certain tasks 

### Claims Based 

You have a token (eg API Key) 

## Approach to Authorization 

Azure AD 
- Register Apps 
  - Applications themselves can be registered with Azure AD 
- Users and Roles 

Azure AD Conditional Access 
- Deny access/ Additional validation based on conditions 
  - Not using regular computer 
  - Not in the country 
  - Enforce MFA per user or Per App basis for additional validation 

Delegating secret holding 
- Not to hold your secrets inside of your application code or even inside the config files.

Azure Key vault
- put your secrets in Key vault, application can request the secret, and it can be returned as a secret.
- Application is running under a service principle and you have given access to that secret.

Principle of Least Privilege 
- Allow permissions to users on only what is needed. Avoid providing additional permissions

Avoid reinventing the wheel take advantage of Azure AD and Azure Key Vault 

## Azure AD Groups and Roles

Access Permissions 
- Groups 
  - Create users groups
  - Azure premium P2 type subscription, you can create dynamic group 
  - Person to manage the groups doesn't has to be global administrator, create a user in azure with user administrator permission (RBAC, granting very granular permissions to users within Azure) 
  - Group Owner (Assigns users to the group)

- Roles 
  - User Administrator is a role 
  - Built-in roles 
    - Owner  
      - Full access to the resource 
      - Can assign permissions to other people 
    - Contributor 
      - Full access to resource 
      - Do not have the ability to give permission to anyone else
    - Reader 
      - Can see the resource 
      - Can perform some readonly type functions
      - Cannot modify the resource like stop, update 

    - Custom Roles 
      
## Just In Time (JIT) Access

- Feature of Azure Security center 
- Requires Azure Defender subscription ($15/server/month)

- Lock Down the inbound traffic to a VM (RDP and SSH ports) 
  - Open RDP and SSH ports are security risks 
  - JIT access locks down the inbound traffic to those relevant ports 
  - First, checks the user's RBAC security settings for that VM 
  - Then, configures the Firewall/NSG to allow inbound traffic for the specific IP address for the relevant ports only for limited time
  - Automatically closes the ports when time expires, connections that are already established are not interrupted 

- JIT minimizes the attack surface

## Azure Resource Graph 

- Allows you to explore your resources in your Azure subscription using a query language 
- Azure Portal > Resource Graph Explorer 
- Azure Resource Graph's query language is based on the Kusto query language used by Azure Data Explorer.
- Resource Graph supports Azure CLI, Azure PowerShell, Azure SDK for Python, and more. The query is structured the same for each language.
