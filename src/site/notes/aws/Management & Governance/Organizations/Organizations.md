---
{"dg-publish":true,"permalink":"/aws/management-and-governance/organizations/organizations/"}
---


## What
AWS Organizations is a service that provides centralized management of multiple AWS accounts, enabling consolidated billing, hierarchical resource organization, and policy-based controls across accounts.

>[!info] Two Feature Modes
>**All Features**: default mode, with all permissions. cannot change to Consolidated Billing. \
>**Consolidated Billing**: only for managing accounts' billings centrally. can change to All Feature. 

![Organizations_Components.png](/img/user/aws/Management%20&%20Governance/Organizations/excalidraw/Organizations_Components.png)
## Core Components
- **Root**: The top-level container of an organization; the management account is always at this level.
- **Management Account**: The **only** AWS account that can create and manage the organization.
- **Member Accounts**: AWS accounts that are either **created or invited** through the AWS Organizations console.
- **Organizational Units (OUs)**: Sub-level groups used to organize and manage accounts.
- **Delegated Administrator**: Recommended accounts for performing **daily administrative tasks** instead of using the management account.


![Organizations_SCPs.png](/img/user/aws/Management%20&%20Governance/Organizations/excalidraw/Organizations_SCPs.png)
## Policy Types
- **Authorization Policy**: Defines policy boundaries **without assigning permissions**.
    - **Source Control Policy**: Specifies **principal-centric** policies.
    - **Resource Control Policy**: Specifies **resource-centric** policies.
- **Management Policy**: Configures and manages AWS services.
    - **Declarative Policy**: Applies desired configurations to services.
    - **Backup Policy**: Defines backup plans for accounts and OUs.
    - **Tag Policy**: Standardizes tagging across accounts.
    - **Chatbot Policy**: Controls access from chat applications to AWS accounts.
    - **AI Service Opt-out Policy**: Manages data collection settings for AWS AI services.

>[!info] SCP Permission Evaluation
>**ALLOW**: should be explicitly allowed at **ALL** level from top down to account \
>**DENY**: any deny from higher layer will take final effect 

>[!info] RCP Permission Evalution
>`RCPFullAWSAccess` is aws management policy and attached to Root and each OU/account by default and you **cannot** detach it.
>To deny access to a resource, it's enough to configure DENY at desired OU or account and this denial will be inherited.

![Organizations_Integrated_Services.png](/img/user/aws/Management%20&%20Governance/Organizations/excalidraw/Organizations_Integrated_Services.png)
## Service Integration
- **Trusted Access for AWS Services**: Allows specific AWS services to perform tasks across your organization's accounts.
- **IAM Identity Center Integration**: Provides centralized access management for all accounts in your organization.
- **Cross-Account Role Management**: Manages roles in trusted accounts and enforces organization-wide access control.

## When
- When managing more than a handful of AWS accounts
- During company mergers or acquisitions
- When implementing compliance requirements
- While scaling AWS operations
- During cost optimization initiatives

## Where
This is a global service and can manage accounts globally

## Why
- Centralize billing and cost management
- Implement security controls across accounts
- Standardize resource configurations
- Automate account management
- Share resources across accounts
- Simplify compliance implementation

## Related Services/Resources

  
## References

[AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html)
