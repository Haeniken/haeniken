<p align="right"><b>English Technical</b> | <a href="./README.md">Main Hiring README</a></p>

<h1 align="center">Sergey Haeniken</h1>
<p align="center"><b>DevOps / DevSecOps / SRE Engineer</b> · Linux Infrastructure · Reliability · Scientific Software</p>

<p align="center">
  <img src="https://img.shields.io/badge/Experience-11%2B%20years-1F8A70?style=for-the-badge" alt="11+ years of experience" />
  <img src="https://img.shields.io/badge/Focus-DevOps%20%7C%20DevSecOps%20%7C%20SRE-0A66C2?style=for-the-badge" alt="DevOps, DevSecOps, SRE" />
  <img src="https://img.shields.io/badge/Environments-Linux%20%7C%20Kubernetes%20%7C%20Docker-3D5A80?style=for-the-badge" alt="Linux, Kubernetes, Docker" />
</p>

## Profile

I have worked with Linux infrastructure for more than 11 years: distributed-service operations, releases, observability, networking, storage, incident analysis and security controls.

I write tools for diagnostics, configuration generation, state reconciliation, safe retries and scientific-data processing.

## Experience

- **Bank Saint Petersburg — DevOps Engineer, 2024—present.** Operations for internet-banking infrastructure: more than 100 microservices in Docker Swarm, Kubernetes and Helm, GitLab CI/CD, planned and emergency deployments. Monitoring critical integrations and business metrics, L3 incident analysis and participation in 24/7 recovery under a 99.97% SLA. I am currently working on introducing AI to analyze application logs and investigate service errors.
- **TIPPO Cloud Service — SRE Engineer, 2024—present, project role.** Operations for more than 500 client resources, 7 virtual and 6 physical servers, and over 75 TB of data. WireGuard/IPsec with BGP/BFD, ZFS RAIDZ, MySQL Galera, GitOps-managed Traefik, Restic/S3 backups and recovery tests.
- **StormWall — Lead Engineer, 2021—2024.** L3–L7 traffic protection, WAF, GRE/IPIP, packet-capture analysis and Splunk/R-Vision security events. Diagnostic automation with Ansible, Bash and Python.
- **ElGracia — Linux infrastructure, 2014—2019.** A platform serving about 1,000 concurrent users: Linux, MySQL/InnoDB, MariaDB Galera, centralised logging, core-dump analysis and fault isolation across infrastructure and a C++ server core.

## Main Responsibilities

- operating Linux, Kubernetes, Helm, Docker Swarm, Nginx and Traefik;
- CI/CD and GitOps: configuration checks, builds, migrations, controlled rollout and rollback;
- observability with Zabbix, Grafana, Prometheus, ELK/Kibana and Splunk;
- incident analysis using metrics, logs, packet captures, request timing and SQL plans;
- network resilience with WireGuard, IPsec/XFRM, BGP, BFD, FRR and CoreDNS;
- storage and databases: ZFS, software RAID, MySQL/MariaDB, PostgreSQL/TimescaleDB and Oracle DB;
- DevSecOps controls: WAF, segmentation, secrets handling, image and configuration scanning, CrowdSec, Trivy and OpenVAS;
- runbooks, backup recovery tests and controlled failover exercises.

## Selected Projects and Engineering Work

### [Astrosferum](https://github.com/Haeniken/bot_astrosferum)

[Project website](https://astrosferum.com) · [ORCID 0009-0005-5804-5011](https://orcid.org/0009-0005-5804-5011)

I developed an astronomy forecast system using ICON-EU and ICON Global: input completeness checks, atmospheric calculations and charts for Telegram, VK and the web. Results retain their source model cycle.

Astrodome extends the forecast to 129 directions over 72 hours. The calculation core, queue and interface are deployed; load testing and comparison with observations remain before public release. Loss of optional NASA GEOS-CF data does not stop the main forecast.

[Calculations](https://haeniken.com/en/articles/astrosferum/) · [Astrodome architecture](https://haeniken.com/en/articles/astrodome/)

### Seven-node resilient network

I deployed a full-mesh network: WireGuard as the primary transport, IPsec/XFRM as backup, and FRR with BGP/BFD for route selection. I wrote the configuration generator and operational runbook, and test failover with application requests. Zabbix records the selected transport and link state.

HTTPS requests fail over between the public path, mesh and an SSH tunnel. Return requires 180 seconds of continuous availability; Zabbix distinguishes backup operation from a complete outage.

[Design and verification](https://haeniken.com/en/articles/network-ha/)

### Conversion service monitoring

I configured Zabbix for a Go service: API, RabbitMQ, workers, queues and external dependencies. A control task checks conversion, previews and storage operations; it detected upload failures while containers passed health checks. HTTP error rates use consistent counter snapshots; trigger dependencies suppress cascading alerts.

### File storage maintenance in Go

I developed tools to restore file records in MySQL and deduplicate through hard links while the application stays running. Streaming reads and external sorting bound memory use; files are checked before atomic replacement, with a recovery journal. In production, I exported and sorted 96.26 million database rows, then started deduplication.

### GitOps for Traefik

I developed a [domain management panel](https://github.com/Haeniken/gitops-traefik-panel): domain validation, GitHub pull requests, configuration checks, deployment and TLS issuance. Infrastructure changes remain in Git.

### Reconciling PostgreSQL with external systems

In a private control panel, I moved network operations out of PostgreSQL transactions into safely retried jobs. Duplicate payment notifications cannot credit a balance twice; background reconciliation restores recorded state on external nodes. HMAC-SHA256 verification, duplicate delivery and conflict handling are covered by tests.

[Engineering note](https://haeniken.com/en/articles/rabbithole-vpn/)

### Multi-stream TURN transport for WireGuard

I developed a [server proxy](https://github.com/Haeniken/rabbithole-turn-proxy) and an [Android client](https://github.com/Haeniken/rabbithole-turn-android): several TURN/DTLS streams form one UDP session with a stable WireGuard socket. The client accounts for latency and loss, uses TCP fallback and prepares connections before changing networks. Third-party client compatibility is preserved.

[Transport design](https://haeniken.com/en/articles/turn-transport/)

### Architecture review across seven nodes

I reviewed seven production hosts: local ZFS state, independent RabbitMQ queues, and single points of failure in monitoring and backups. I prepared a plan to standardize builds, host roles, queues and management networking. Shared orchestration remains a later step after removing local-state dependencies.

### Monitoring performance

I traced Zabbix and PostgreSQL/TimescaleDB latency to shared HDDs: `iowait` reached 86–90% and disk latency 300–440 ms. I reduced background collection and tuned PostgreSQL and web resources. The long-term solution is dedicated SSD/NVMe storage for the database and WAL.

## Tools

| Area | Tools and systems |
|---|---|
| Linux and networking | Linux, systemd, sysctl, iptables, WireGuard, StrongSwan/IPsec, XFRM, FRR, BGP, BFD, CoreDNS |
| Containers | Kubernetes, Helm, Docker, Docker Swarm, Compose, Traefik, Nginx |
| Automation | Ansible, GitLab CI, GitHub Actions, GitOps, Bash, Python, Go, PHP |
| Observability | Zabbix, Grafana, Prometheus, ELK/Kibana, Splunk, R-Vision |
| Data | MySQL/MariaDB Galera, PostgreSQL/TimescaleDB, Oracle DB, ZFS, Restic, S3 |
| DevSecOps | WAF, CrowdSec, Trivy, OpenVAS, Lynis, rkhunter, secrets handling and configuration checks |
| Scientific computation | ICON-EU, ICON Global, GRIB2, GEOS-CF, numerical integration, WebGL2/Canvas |

## Certificates

- [IBM Cybersecurity Analyst Professional Certificate](https://www.coursera.org/account/accomplishments/specialization/certificate/CTF3ZA9TULXG)
- [Security Analyst Fundamentals](https://www.coursera.org/account/accomplishments/specialization/certificate/VFFHAW9QMFZR)
- [IT Fundamentals for Cybersecurity](https://www.coursera.org/account/accomplishments/specialization/certificate/PCRSJGSVCAEH)
- [Cyber Threat Intelligence](https://www.coursera.org/account/accomplishments/certificate/4X9JPCHUZW3P)
- [Network Security & Database Vulnerabilities](https://www.coursera.org/account/accomplishments/certificate/RYBRER3QAF3S)
- [Penetration Testing, Incident Response and Forensics](https://www.coursera.org/account/accomplishments/certificate/8P7UYE98Q8PT)

---

<p align="center"><i>Open to DevOps / DevSecOps / SRE roles.</i></p>
