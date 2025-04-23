# ELB (Elastic Load Balancer) and the Differences Between Types

#aws/service #aws/elb #aws/networking #infrastructure #load_balancer

### Types and Main Uses
- **CLB (Classic Load Balancer)**
  - **Features:** An older type with only basic load balancing functionality
  - **Use Cases:** Usable in simple scenarios but insufficient for modern complex routing
- **ALB (Application Load Balancer)**
  - **Features:** Specialized for HTTP/HTTPS traffic. Enables flexible routing based on URL paths and hostnames
  - **Use Cases:** Mainstream for microservices and complex web applications. In fact, it's the most commonly used today
  - **Point of Confusion:** Why ALB is used instead of CLB → ALB offers advanced routing and flexible traffic management
- **NLB (Network Load Balancer)**
  - **Features:** Achieves high performance and low latency at the network level
  - **Use Cases:** Scenarios requiring high performance
- **GLB (Gateway Load Balancer)**
  - **Features:** The name "Gateway" comes from its function of managing traffic at the network entry point
  - **Use Cases:** Used when distributing traffic to multiple devices such as security appliances and monitoring tools 