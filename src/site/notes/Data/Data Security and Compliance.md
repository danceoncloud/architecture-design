---
{"dg-publish":true,"permalink":"/data/data-security-and-compliance/"}
---

### Principles: 
- Defense in Depth: use layered security (firewalls, encryption, access controls)to reduce single points of failure.
- Least Privilege: always the minimum access to perform tasks.
- Zero Trust: verify every access request.
### Mechanisms:
- Encryption: in transit and at rest
- Access Control: RBAC and ABAC
### Solution:
**HTTPS**: SSL/TLS in transit
**AWS KMS**: encryption at rest
**AWS IAM/Policy**: access control

>[!INFO] RBAC & ABAC
>**RBAC**: assign permissions to roles (`Admin can delete records`) \
  **ABAC**: define roles using attributes (`IF user.department = "Finance" AND resource.sensitivity = "Low" THEN allow access`)


### Principles: 
- Data Classification: categorize data based on sensitivity level with appropriate protection measures.
- Privacy by Design: embed data protection from the start (GDPR compliance)
### Mechanisms:
- **Data Anonymization**: Irreversible removal of identifiers (exempt from GDPR)
	*Generalization*: replace exact values with ranges (age 25 -> "20-30")
	*Perturbation*: add noise to data (salary 50000 -> 50000 * (0.95, 0.05))
	*Hashing*: hash data with SHA-256 with salt
	*Static Masking*: permanently replace data ("Jone Doe" -> "User_123")
- **Data Pseudonymization**: Reversible replacement (GDPR-compliant with safeguards)
	*Tokenization*: replace data with tokens in a secure vault
	*Dynamic Masking*: make data on-the-fly based on user roles ("123-45-6789" → "--6789")	


> [!NOTE] Regulatory Framework: GDPR, PII, HIPAA
> **Tokenization** and **Pseudonymization** are explicitly recommended by GDPR to reduce risks.
> **Anonymized data** falls outside GDPR scope.



### Solutions:
AWS Compliance Tools, Google Cloud Compliance Controls, Microsoft Compliance Manager