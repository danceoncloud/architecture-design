---
{"dg-publish":true,"permalink":"/aws/organizations/"}
---


## What
AWS Organizations is a service that provides centralized management of multiple AWS accounts, enabling consolidated billing, hierarchical resource organization, and policy-based controls across accounts.

>[!Two Feature Modes]
>**All Features**: default mode, with all permissions. cannot change to Consolidated Billing. \
>**Consolidated Billing**: only for managing accounts' billings centrally. can change to All Feature. 


## Core Components
- **Root**: The top-level container of an organization; the management account is always at this level.
- **Management Account**: The **only** AWS account that can create and manage the organization.
- **Member Accounts**: AWS accounts that are either **created or invited** through the AWS Organizations console.
- **Organizational Units (OUs)**: Sub-level groups used to organize and manage accounts.
- **Delegated Administrator**: Recommended accounts for performing **daily administrative tasks** instead of using the management account.

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

## Service Integration
- **Trusted Access for AWS Services**: Allows specific AWS services to perform tasks across your organization's accounts.
- **IAM Identity Center Integration**: Provides centralized access management for all accounts in your organization.
- **Cross-Account Role Management**: Manages roles in trusted accounts and enforces organization-wide access control.
- **Service Trust Policy**: Grants AWS services permission to perform tasks across the organization.

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
