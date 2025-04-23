# Amazon CloudFront and Signed URLs

#aws/service #aws/cloudfront #aws/security #content_delivery #authentication

### Basics of Signed URLs(署名付きURL)
- **Purpose:** Used to provide content exclusively to specific users. For example, access restrictions for paid content or member-only sites
- **Mechanism:** Expiration dates and access restriction information are embedded in the URL
  - **Technical Background:** Uses cryptographic technologies such as HMAC (Hash-based Message Authentication Code) to verify the legitimacy of URLs

### My Confusion Points and Supplementary Information
- **Comparison with Other Technologies**
  - Besides signed URLs, there are other methods to implement access control such as token authentication, IP restrictions, and session management
  - The choice of method depends on the usage scenario and security requirements 