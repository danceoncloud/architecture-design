---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/cloud-front/content-and-service-security/"}
---

![CloudFront Security.png](/img/user/AWS/Networking-Content-Delivery/CloudFront/CloudFront%20Security.png)
## Content Security from Viewer to CloudFront
This focus on protecting content as it moves between viewers and CloudFront.

### **Access Control**
> [!NOTE] **Signed URLs and Cookies through Trusted Key Group**
> Control access to specific content for authenticated users.
>1. Content owner create a pair of public/private key, upload public key to cloudfront to configure trust key group
>2. User must authenticate to obtain signed URL or cookies encrypted by private key.
>3. Content owner offers application that can respond to authenticated user with signed URL or cookies
> ![Signed URL or Cookies.png](/img/user/AWS/Networking-Content-Delivery/CloudFront/Signed%20URL%20or%20Cookies.png)

- **Geo-Restriction:** Block access based on the user's location.
- **AWS WAF:** Filter malicious traffic, block bots, and set rate limits. Applied at Edge Location for evaluation.

### **Encryption and Data Integrity:**
- **HTTPS (TLS):** Enforce HTTPS for viewers to protect data in transit.

> [!NOTE] **Field-Level Encryption**
> Encrypt sensitive fields like PII at the edge before reaching your origin.
> ![Field Level Encryption.png](/img/user/AWS/Networking-Content-Delivery/CloudFront/Field%20Level%20Encryption.png)

- **Cache-Control Headers:** Prevent caching of private or sensitive data.

### **Content Monitoring:**
- **Access Logs:** Enable CloudFront logs for detailed user activity.
- **CloudWatch Alarms:** Monitor abnormal traffic patterns.


## Server Security from CloudFront to Origin 
This protects contents between CloudFront and backend origin(S3, API Gateway, VPC, etc)
### **Origin Access Control (OAC) / Origin Access Identity (OAI):**
- Restrict CloudFront access to private S3 buckets without making them public.
- Prefer OAC for new setups, as it offers enhanced security features.

### **TLS and Custom Headers:**
- **Origin Protocol Policy:** Enforce HTTPS between CloudFront and your origin.
- **Custom Headers:** Add headers to verify requests originate from CloudFront.

### **Access Control and IAM:**
- **IAM Roles and Policies:** Apply least-privilege permissions for CloudFront and origin access.
- **AWS WAF at Origin:** Protect the backend from attacks by filtering malicious requests.

### **Monitoring and Threat Detection:**
- **CloudTrail:** Track changes to CloudFront and origin settings.
- **Shield Standard/Advanced:** Protect against DDoS attacks.



> [!NOTE] HTTPS session and Symmetric Session Key
> when using HTTPS, it's crucial to understand the creation of **Symmetric Session Key** on both side, this is the key element to transform **HTTP** to **HTTPS**.
> 
> ![Symmetric Session Key.png](/img/user/AWS/Networking-Content-Delivery/CloudFront/Symmetric%20Session%20Key.png)

  