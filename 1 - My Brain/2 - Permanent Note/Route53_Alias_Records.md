# Route 53 Alias Records

#aws/service #aws/route53 #aws/networking #dns #domain_name

### Basic Concepts
- **CNAME Records**
  - **Function:** Links one domain name (e.g., `www.example.com`) to another domain name (e.g., `example.com`)
  - **Constraint:** Cannot be used for Zone Apex (the domain itself, e.g., `example.com`)
- **Zone Apex**
  - **Definition:** The top-level (top-level) name of a domain. Not a subdomain, but `example.com` itself
- **Alias Records**
  - **Function:** Works like CNAME while being configurable for Zone Apex
  - **Benefit:** Simplifies DNS configuration by allowing top-level domains to be mapped directly to AWS resources such as CloudFront or ELB 