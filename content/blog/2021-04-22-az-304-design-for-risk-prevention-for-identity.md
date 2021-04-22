---
title: "AZ 304 | Design for Risk Prevention for Identity "
date: 2021-04-22T22:41:35.493Z
description: "AZ 304 Design for Risk Prevention for Identity "
---
# AZ 304 Design for Risk Prevention for Identity 

## Risk 

What is Risk ?

- Things that can bring negative effects to the business 
- How likely it will happen?
- How bad is it?

Risk Frequency and Size 

- Very likely to happen or severe consequences - requires immediate action 
- Somewhat likely to happen and serious consequences - unacceptable risk 
- Could happen and not too bad - acceptable risk 
- Very low chance to happen and cosmetic - low risk 

Impossible to have no risk 

- Classify risks
- Accept risks which are acceptable 
- Mitigate risks 

## Identity Risks - What could happen 

Financial Costs 

- UserID and Passwords get hacked
- Elevated privileges of unknown actor 
- you can suffer financial costs 
- you could loose customers

Data Loss 

- Data is financial asset / competitive advantage 

Denial of Service 

- Systems hacked, Ransom for access 

Loss of Trust

- reputation gets suffered 

Customer Confusion 

- Causes confusion on customers

Government and Corporate Compliance 

- laws on data breach 


### Causes of Risk 

Expired Users

Too high permissions on users and service principles 

Physical Access 

## Mitigating Risks with Identity 

### Risk Prevention for Identity 

#### Risk Assessment Strategy 

##### Access Reviews 

- Force people responsible for security of a group to review contents of that group on a regular basis 
- you can setup a policy in Azure Active Directory that every 30 days the group owner must review all of the members of the group and the access review will not only remind them it will nag them to go into the system and review membership of the group that they control
- Implementing access reviews to your groups is one way you're going to ensure that the members of group are all need access and at the right level

##### RBAC Policies 

Azure Governance Architecture 

1. DevOps approach to Infrastructure 
2. Policy-based Control 

- Establish a company policy for access to certain things 
- Use Azure Policy engine to enforce that policy, for example a marketing resource should only be able to create resources in a marketing group not in other groups 
- You could also have report on incompliance of policies 


##### Physical Access 

- Locked computer when away from desk 

##### Azure AD Connect Health 

- AD Connect is critical component (synchronizes on-prem identity to cloud) 

## Risk Mitigation 

### Compliance to standards 

- Quality standards etc. HTTPS 

### Test 

- Automated tests to make sure policy is in force 

### Don't reinvent 

- Use existing systems like Azure AD Industry standards tools 

### Training / phishing 

### Layers of security 

### Multi-Factor Authentication 

### Conditional Access 

### Privileged Identity Management PIM 

### Advanced Threat Protection ATP 

- Can detect hacks 












