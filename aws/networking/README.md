# AWS Networking

The syllabus. Which AWS networking services you should know, and how deep depends on
the role you're playing.

## The three tiers

The roles are cumulative — DevOps needs everything a Developer needs plus its own tier,
a Network Admin needs all three.

| Tier | Role | Scope |
| --- | --- | --- |
| 1 | Developer | The VPC building blocks and the services you put in front of an app |
| 2 | DevOps | Tier 1, plus automating and observing the network |
| 3 | Network Admin | Tier 2, plus performance, hybrid connectivity and deep security |

## Services

### Tier 1 — Developer

- VPC Basics
- ELB / CloudFront
- Route 53 (DNS)
- VPC Endpoint
- PrivateLink
- VPC Peering

### Tier 2 — DevOps

- Transit VPC
- Transit Gateway
- Site-to-Site VPN
- Client VPN

### Tier 3 — Network Admin

- Direct Connect
- VPC Advanced

## Concepts

### Tier 1 — the building blocks

Know these cold; everything else is built on them.

- CIDR
- Internet Gateway
- Subnets
- Route Tables
- NAT
- IP addressing — public, private, Elastic
- Security Groups
- Network ACLs

### Tier 2 — operating the network

- Network automation (CloudFormation, CLI)
- Logging and monitoring

### Tier 3 — running the network

- Enhanced networking
- Hybrid connectivity
- Network performance
- Network security (Layer 3, Layer 7)

---

Source: awstrainingcenter.com course outline.
