<p align="right"><b>English Technical</b> | <a href="./README.md">Main Hiring README</a></p>

<h1 align="center">Sergey Haeniken</h1>
<p align="center"><b>DevOps / DevSecOps / SRE Engineer</b> · Linux Infrastructure · Reliability · Scientific Software</p>

<p align="center">
  <img src="https://img.shields.io/badge/Experience-11%2B%20years-1F8A70?style=for-the-badge" alt="11+ years of experience" />
  <img src="https://img.shields.io/badge/Focus-DevOps%20%7C%20DevSecOps%20%7C%20SRE-0A66C2?style=for-the-badge" alt="DevOps, DevSecOps, SRE" />
  <img src="https://img.shields.io/badge/Environments-Linux%20%7C%20Kubernetes%20%7C%20Docker-3D5A80?style=for-the-badge" alt="Linux, Kubernetes, Docker" />
</p>

## Profile

I have worked with Linux infrastructure for more than 11 years. My work covers distributed-service operations, releases, observability, networking, storage, incident analysis and security controls.

I write code when an existing tool does not cover the task: diagnostics, configuration generation, state reconciliation, safe retries and scientific-data processing. I treat this code as part of DevOps/SRE work rather than as a separate backend specialisation.

## Experience

- **Bank Saint Petersburg — DevOps Engineer, 2024—present.** Operations for internet-banking infrastructure: more than 100 microservices in Docker Swarm, Kubernetes and Helm, GitLab CI/CD, planned and emergency deployments. Monitoring critical integrations and business metrics, L3 incident analysis and participation in 24/7 recovery under a 99.97% SLA.
- **TIPPO Cloud Service — DevOps / DevSecOps / SRE Engineer, 2024—present, project role.** Operations for more than 500 client resources, 7 virtual and 6 physical servers, and over 75 TB of data. WireGuard/IPsec with BGP/BFD, ZFS RAIDZ, MySQL Galera, GitOps-managed Traefik, Restic/S3 backups and recovery tests.
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

Astrosferum is a forecasting system for astronomical observations that I designed and developed. It downloads ICON-EU and ICON Global GRIB2 data, checks model-cycle completeness, extracts atmospheric fields and calculates cloud, wind, stability, transparency and astronomy-specific diagnostics. Every result retains its source model cycle; Telegram, VK and web charts are rendered from stored calculations.

The ordinary forecast processes a reduced vertical profile. Horizon mode separately compares eight directions at a geometric altitude of 10°. Ephemerides are calculated for each forecast term, and the resulting charts keep model estimates distinct from observations.

#### Astrodome

I am now developing a directional forecast for the whole sky from 10° to zenith: 129 directions for each of 72 native hourly terms, or 9,288 node-hours in one dataset. It loads all 74 ICON-EU full levels, 75 geometric half levels and 19 surface fields.

Source meteorological variables are reconstructed along a refracted ray before Cₙ², seeing, atmospheric coherence time τ₀, isoplanatic angle θ₀, PWV, air mass, cloud optical depth, fog, transparency and wind shear are calculated. Derived scores are not interpolated between nodes. A failed cell is marked separately and does not discard the remaining directions and forecast terms.

NASA GEOS-CF is an optional source for aerosol AOD components and total column ozone. Temperature, pressure, humidity and wind still come from ICON. If NASA data is stale or incomplete, only the additional spectral estimate is omitted; the main forecast continues to work.

The calculation core, job queue, server-side authentication and WebGL2/Canvas interfaces are deployed for controlled verification. Work before the public release covers load measurements, regression checks for the ordinary forecast under the same load and coefficient calibration against public DIMM observatory data.

- [Models and calculations in the ordinary forecast](https://haeniken.com/en/articles/astrosferum/)
- [Astrodome architecture](https://haeniken.com/en/articles/astrodome/)

### Seven-node resilient network

I deployed a full-mesh network with stable service addresses for a small production environment. WireGuard carries the primary path, pre-established IPsec/XFRM provides the backup, and FRR selects routes through BGP and BFD. Inbound and outbound prefix lists permit only the expected address for each node.

I wrote the configuration generator and the operational runbook. They cover adding a node without renumbering existing XFRM interfaces, certificate issuance and staged renewal, removal of a compromised node, diagnosis and rollback. I periodically test failover in the live environment by limiting the fault to one peer pair, waiting for the IPsec route, checking ICMP and an application request, and then confirming return to WireGuard. Zabbix records the selected transport, BGP/BFD state, WireGuard handshake freshness and IPsec SAs without emitting mirrored alerts from every peer.

[Network design, failover test and runbook](https://haeniken.com/en/articles/network-ha/)

### GitOps for Traefik

In [GitOps Traefik Panel](https://github.com/Haeniken/gitops-traefik-panel), an operator adds a domain through a checked procedure. The panel normalises Unicode/Punycode, validates A/AAAA and WHOIS data, checks duplicates, opens a GitHub pull request and reports checks, deployment and TLS issuance. The infrastructure change remains in Git and follows the same path as a manually prepared pull request.

### Reconciling PostgreSQL with external systems

In a private control panel, I separated payment recording from applying desired state across several external nodes. PostgreSQL stores balances, the operation ledger, jobs, leases and generations; network calls run after the database transaction has committed. A repeated notification cannot credit the balance twice, while an unavailable node is retried and later reconciled against recorded state. Incoming notifications use HMAC verification, opaque labels and a separate audit log.

[Engineering note on the internal control panel](https://haeniken.com/en/articles/rabbithole-vpn/)

### Observability and architecture decisions

- **Zabbix and PostgreSQL/TimescaleDB performance.** I traced latency across physical disks, ZFS, system RAID, PostgreSQL and container limits. Logically separate workloads shared the same HDDs: `iowait` reached 86–90% and one disk showed 300–440 ms latency. For the current environment I reduced background collection and tuned PostgreSQL and web resources; the long-term fix was defined as dedicated SSD/NVMe storage for PostgreSQL and WAL rather than more tuning on the shared HDD set.
- **Checking whether Docker Swarm was the right next step.** After reconciling seven active nodes, I did not move the whole environment into a stretched cluster. Most services depended on local ZFS pools, bind mounts, databases and separate RabbitMQ queues, while a common private network did not yet exist. I limited the future candidate to the compute service, with local state removal, one queue and multi-replica idempotency as prerequisites.

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
