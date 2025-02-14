---
{"dg-publish":true,"permalink":"/aws/organizations/","title":"Organizations"}
---


## What
AWS Organizations is a service that provides centralized management of multiple AWS accounts, enabling consolidated billing, hierarchical resource organization, and policy-based controls across accounts.

>[!Two Feature Modes]
>**All Features**: default mode, with all permissions. cannot change to Consolidated Billing. \
>**Consolidated Billing**: only for managing accounts' billings centrally. can change to All Feature. 


| **Core Components**     |                                                                                     |     |
| ----------------------- | ----------------------------------------------------------------------------------- | --- |
| root                    | the top-level container of organization, management account is always at this level |     |
| management accounts     | the ONLY aws account to create/manage Organization                                  |     |
| member accounts         | aws accounts created or invited through Organization console                        |     |
| organizational units    | sub level to group accounts                                                         |     |
| delegated administrator | recommended accounts for daily tasks normally done through management account       |     |

| **Policy Types**     |                                                         |                                                      |
| -------------------- | ------------------------------------------------------- | ---------------------------------------------------- |
| Authorization Policy | to set policy boundary **without assigning permission** |                                                      |
|                      | Source Control Policy                                   | to specify principal-centric policies                |
|                      | Resource Control Policy                                 | to specify resource-centric policies                 |
| Management Policy    | to configure and manage AWS services                    |                                                      |
|                      | Declarative Policy                                      | to apply desired policy to services                  |
|                      | Backup Policy                                           | to apply backup plans to accounts/OU                 |
|                      | Tag Policy                                              | to standardize tags across accounts                  |
|                      | Chatbot Policy                                          | to control access from chat applications to accounts |
|                      | AI Service Opt-out Policy                               | to control data collection for AWS AI services       |

| **Service Integration**         |                                                                                   |
| ------------------------------- | --------------------------------------------------------------------------------- |
| Trusted Access for AWS Services | allows specific AWS services to perform tasks across your organization's accounts |
| IAM Identity Center Integration | provides centralized access management for all accounts in your organization      |
| Cross-Account Role Management   | role management in trusted account and organization-wide access control           |
| Service Trust Policy            | allows AWS services to perform tasks on organization wide                         |


| Security                        |     |
| ------------------------------- | --- |
| Service Trust Policy            |     |
| Cross-Account Access Management |     |
| Organizations CloudTrail        |     |


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
