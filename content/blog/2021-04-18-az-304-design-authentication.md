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



## Design Authentication 

## Authentication vs Authorization 

Authentication
- __Authentication is who you are__
  - User Id and password
    - Strength of the password, policies
  - Multi-Factor Authentication 
    - Access to your email account, text message, etc
  - Federation of identity to external services
    - You trust someone else to authenticate someone for you

Authorization 
- __Authorization is you are allowed to perform an action__
  - What level of access do you have?
    - Read only
      - Unable to change the resource only view access 
    - Contributor
      - you have full rights to start, stop, delete, create within that resource
      - You cannot grant rights to other people
    - Owner 
      - Grant rights to other people
      - Can create other owners and other contributors 
  - Something else?
  - How fine grained is that access?

Azure Active Directory (Azure AD) is Azure's authentication service 
  - Instead of building your own user and password management you can allow Azure AD to manage your users and passwords and you do not have to have that code.

Key Features of Azure AD
- Enforce sophisticated password complexity policies
- Synchronizes with corporate Active Directory
- Supports single sign on 
- Multi-factor authentication options
- Role-Based Access Control 
- Can work with social media accounts for sign in (e.g. Facebook Connect)
- Can support external partners access 


## AD Synchronization 

Single Sign On 

Can synchronize with on-prem AD using "AD Connect"

If the password changes, it supports the new password within minutes (every 15 minutes or so)

If access is revoked, it's revoked everywhere


## Protecting Authentication 

Authentication Security 

Internet Protocol Security - IPSec 
- Security protocol that runs within the network stack 
- Provides security at the IP Layer
- Encrypting data packets 
- Authentication Header (AH) - signing 
- Lower level on the networking stack compared to application encryption or even TLS/SSL
- Usually for VPNs

Site-to-Site VPN 
- Site-to-Site VPN is what you end up with when you have two network gateways connected to each other in a secure fashion

Azure Virtual Network 
  - VPN Gateway 
    - Connects to On-Premises Network Gateway 

Point to Site VPNs
  - VPN Software to connect your laptop or remote device into corporate network 

Site to Site VPNs
  - Connect your entire networks together 
  - Usually requires separate devices so the gateway on your on-premises is usually a physical hardware that you've purchased that supports it.

MFA - Multi Factor Authentication 
- MFA is a way of ensuring that somebody is who they say they are 
- User Id and password in not enough for a secure system 
- In Azure, when you use MFA users is going to approve/respond to  the signin via email, SMS, Notification on phone.