# Other AWS Services

#aws/service #aws/directory_service #aws/network_firewall #aws/systems_manager #aws/security

### AWS Directory Service
- **Function:** Provides directory management in the cloud. Can integrate with on-premises Active Directory
- **Benefit:** Reduces management burden by centralizing user management and authentication

### AWS Network Firewall
- **Function:** A fully managed firewall service that provides advanced control of traffic within a VPC
- **Comparison:**
  - **Security Groups:** Perform basic traffic control at the instance level
  - **Network ACLs:** Traffic control at the subnet level
  - **Network Firewall:** Implements advanced security controls at the VPC-wide or subnet level with more detailed rule settings

### Session Manager
- **Function:** Part of AWS Systems Manager, allowing secure access to instances without using SSH or RDP
  - Establishes sessions directly from browser or CLI
  - Enables log management and access control via IAM
- **Disadvantages:**
  - May require internet connection in some cases
  - May take time to transition to new tools if accustomed to existing operational workflows 