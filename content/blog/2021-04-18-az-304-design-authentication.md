---
title: AZ 304 | Design Authentication
date: 2021-04-18T22:14:10.900Z
description: AZ 304 | Design Authentication Notes
---
# Design Authentication 

## Azure Active Directory 
- For Identity Management 

### Self Service Password Reset 

- Not enabled by default 
- Not available for free account, upgrade to a premium account 
- Enterprise Mobility and Security E5
- Azure AD Premium P2 
- Once activated then you are able to allow end users to manage their own passwords 
- Recover passwords through SMS, email 
- A way of reducing cost by allowing users to reset their own password instead of reaching out to helpdesk

#### Enable Password reset

- None
- Selected (Select Group)
- All

Authentication Methods

Number of methods required to resets
- One (1) 
- Two (2)

Methods available to users (Multiple Selection)
- Mobile App notification
- Mobile app code
- Email (Default) 
- Mobile phone (SMS only) (Default) 
- Office phone
- Security Questions 

Registration 
- Require users to register when signing in ?
  - Yes (default)
  - No

Number of days before users are asked to re-confirm their authentication information 
- 180 --> can be changed 

Notifications
Notify users on password reset? 
Users will be notified that password has been modified?
- Yes (default)
- No

Notify all admins when other admins reset their password?
- Yes (default)
- No

Customization 

Customize helpdesk link 
- Yes 
- No (default)

Custom helpdesk email or URL 
- can be set 

On-premises integration

Write back passwords to your on-premises directory?

Allow users to unlock accounts without resetting their password?