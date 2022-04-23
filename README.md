# ApacheDS (Directory Server) for Docker

---
## How to run?
`docker run --name apacheds -p 389:10389 -p 636:10636 inspectorgadget12/apacheds-docker:latest`

## Alternatively, you can use Docker Compose
```
services:
  apacheds:
    image: inspectorgadget12/apacheds-docker:latest
    tty: true
    stdin_open: true
    ports:
     - 389:10389
     - 389:10636
    volumes:
     - apacheds:/opt/apacheds/instances/default

volumes:
  apacheds:
```

OR

```
services:
  apacheds:
    image: inspectorgadget12/apacheds-docker:latest
    tty: true
    stdin_open: true
    ports:
     - 389:10389
     - 389:10636
    volumes:
     - ./data:/opt/apacheds/instances/default

volumes:
  apacheds:
```

## Why?
ApacheDS serves as a Open Directory Service (Free). Hence, with this alternative, we may be able to elimitate the Usage of Azure Active Directory (Which is expensive to have in a long run). 

## Scalability
Attach the ApacheDS Save Directory to an Network File Server (NFS), and run the Container on Amazon ECS or Google Cloud Container Services or even Google Kubenetes Engine (GKE) or Amazon EKS. Which will promote scalability, high availablity and high performance. At the same time, you will save cost and allow auto-scaling to take place. 

## Expandability
Currently, the Server is exposing on a Non-TLS Port. However, if you would like TLS/SSL authentication, you may attach ACME to the ApacheDS Server. ACME will assist you on rotating / generating certificates using Google Cloud DNS, Cloudflare Domain Service, Amazon Route 53, Azure DNS, DNSPod, CloudXNS, GoDaddy, PowerDNS, OVH, LuaDNS, DNSMadeEasy, Aliyun, ISPConfig, Alwaysdata, Linode Domain API, FreeDNS, cyon, Gandi LiveDNS, Knot, DigitalOcean, ClouDNS, VSCALE, Dynu, DNSimple, NS1, DuckDNS, Name, and more.

[You check out more here](https://github.com/acmesh-official/acme.sh/wiki/dnsapi)