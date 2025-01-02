---
created: 2025-01-02
tags:
  - technology
  - job_interview
  - network
  - http
  - 25_1Q
description: 
reference: https://arc.net/l/quote/brggjmem
---
Answer:
Through [[DNS]], client (the browser) will resolve hostname of the URL to an IP address of the destination server. Then it establishes a [[TCP connection]] through a [[three-way handshake]]. On top of TCP connection, it establishes [[TLS connection]] though TLS handshake, so that only encrypted data is sent over the network. The client uses HTTP Protocol to send a request which contains headers and request payload to the destination server. The server responds with a status code, headers and response payload.
```mermaid
sequenceDiagram
    participant Client
    participant DNS
    participant Server

    Client->>DNS: DNS Query
    activate DNS
    DNS-->>Client: IP Address
    deactivate DNS

    Client->>Server: SYN
    activate Server
    Server-->>Client: SYN-ACK
    Client->>Server: ACK
    deactivate Server
    note right of Client: TCP Handshake

    Client->>Server: Client Hello
    activate Server
    Server-->>Client: Server Hello, Cert
    Client->>Server: Key Exchange
    Server-->>Client: Encrypted Handshake
    deactivate Server
    note right of Client: TLS Handshake

    Client->>Server: HTTP Request
    activate Server
    Server-->>Client: HTTP Response
    deactivate Server
```