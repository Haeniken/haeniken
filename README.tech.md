<p align="right"><b>English Technical</b> | <a href="./README.md">Main Hiring README</a></p>

<h1 align="center">Sergey Haeniken</h1>
<p align="center"><b>DevOps / DevSecOps / SRE Engineer</b> · Backend & Infrastructure Engineer (Go/PHP) · Reliability & Automation</p>

<p align="center">
  <img src="https://img.shields.io/badge/Experience-11%2B%20years-1F8A70?style=for-the-badge" alt="11+ years" />
  <img src="https://img.shields.io/badge/Focus-DevOps%20%7C%20DevSecOps%20%7C%20SRE-0A66C2?style=for-the-badge" alt="Focus" />
  <img src="https://img.shields.io/badge/Backend-Go%20%26%20PHP-3D5A80?style=for-the-badge" alt="Backend" />
</p>

## About

I am a hands-on DevOps/DevSecOps/SRE engineer with 11+ years in Linux infrastructure, high-load operations, and production troubleshooting.

I combine operations ownership with backend development experience, especially where platform reliability and product logic meet.

## What I Do

- run and improve production infrastructure with strong SLA/SLO focus;
- automate incident detection, mitigation, and operational playbooks;
- design CI/CD and GitOps flows for safer deployments;
- build observability (metrics, logs, alerting) with actionable signals;
- apply security hardening and practical DevSecOps controls.

## Go & PHP Engineering Experience

### Go (backend, workers, Telegram integration)

Production-oriented Go development in a multi-service Telegram product:
- service split into `bot-api`, `app-core`, `worker-scheduler`, `worker-notify`, `worker-export`;
- internal API boundaries with service-token protection;
- idempotency patterns (duplicate update protection via `processed_updates`, conflict-safe inserts);
- async export pipeline (`csv/json/ics`) with S3 upload and expiring download links;
- analytics and referral flows integrated into domain logic.

Project reference: private Go Telegram bot repository (Go 1.22, Chi, pgx, AWS SDK v2).

Recent public/private Go projects:
- **[vk_chat_digest_bot](https://github.com/Haeniken/vk_chat_digest_bot)**: VK bot on Go with PostgreSQL and LLM-based chat summaries, per-chat state, batch-triggered digests, and production-minded long-poll processing.
- **bot-vpn** (private): Telegram VPN sales bot on Go with PostgreSQL, 3x-ui and YooMoney integrations, worker-based lifecycle handling, admin flows, and production operations focus.

### PHP (platform tooling and API services)

Practical PHP backend work across operational products:
- **[GitOps Traefik Panel](https://github.com/Haeniken/gitops-traefik-panel)**: layered architecture (`Action` + `Service` + `DTO`), DNS/WHOIS validation, GitHub PR automation, deploy-status polling, CSRF/rate-limit/remember-token security controls;
- **Internal Static Asset Storage API** (private project): upload/copy/delete API for static files, request-id correlation, path normalization/validation, hardlink dedup by MD5, MySQL-backed metadata, Dockerized runtime with hardening.

## Selected Architecture Decisions

- Telegram-first product design to minimize user friction and support cost;
- thin transport layer + separate core domain service;
- asynchronous workers for long operations and predictable bot latency;
- idempotent state transitions and conflict-safe DB writes;
- infrastructure-as-code mindset for config changes (PR-driven GitOps).

## Skills Matrix

| Domain | Stack | Level |
|---|---|---|
| Linux & Networking | Linux, sysctl, iptables, WireGuard | Advanced |
| Containers & Orchestration | Docker, Docker Swarm, Compose, Traefik, Nginx | Advanced |
| CI/CD & GitOps | GitLab CI, GitHub Actions, PR-driven workflows | Advanced |
| Go Development | Go, services/workers, internal APIs | Middle |
| PHP Development | PHP, platform tooling, API services | Middle |
| Backend Development | Python, REST APIs | Advanced |
| Databases | MySQL/MariaDB, PostgreSQL, Oracle DB | Middle |
| Observability | Zabbix, Grafana, Prometheus, ELK/Kibana | Advanced |
| Security / DevSecOps | CrowdSec, OpenVAS, Trivy, Lynis, rkhunter, hardening | Upper-Intermediate |

Level order used in this matrix: `Middle -> Upper-Intermediate -> Advanced`.

## Experience Snapshot

- ⭐ **Bank Saint Petersburg** — *DevOps Engineer*  
  Reliability and operational support for distributed internet banking systems and microservices.
- ⭐ **TIPPO Cloud Service** — *DevOps / DevSecOps / SRE Engineer*  
  Single infrastructure owner for SaaS workloads (500+ client resources; hybrid VDS + bare metal).
- ⭐ **StormWall** — *Lead Engineer*  
  Cybersecurity-focused infrastructure operations, including WAF engineering and L3-L7 (OSI) traffic filtering/tuning, plus troubleshooting and automation.
- ⭐ **ElGracia** — *Linux System Administrator / Project Curator*  
  Owned infrastructure and stability for a high-load TrinityCore project: team coordination, C++ core patching, MySQL/InnoDB + Galera tuning, and production security/observability improvements (ModSecurity, SEnginx, Grafana, Graylog).

## Recent Hands-on Themes

- production security audit of a Go Telegram VPN bot: secrets exposure, fail-open webhook auth, idempotency gaps, DoS-related timeout/body-limit issues, and runtime hardening;
- production rollout of a Go VK bot: Docker Compose + PostgreSQL, VK long poll, LLM integration, per-chat batching, advisory-lock based publish flow, and retry/rate-limit handling;
- live incident-style debugging of external integrations: permission-related event delivery failures, long-poll/session issues, upstream timeout tuning, and transport error recovery;
- safe public release prep for an active service: secret scrub, `.env`/logs/data exclusion, config cleanup, and isolated GitHub repo bootstrap from a server-side copy;
- GitOps delivery design for Traefik-based infrastructure: PR validation, auto-merge, and deploy wrappers;
- MySQL and web-tier troubleshooting: connection pressure, timeout patterns, upstream failures, and request tracing;
- Linux / network / security operations: iptables review, Fail2ban and Lynis checks, traffic-source investigation, and host hardening;
- observability and capacity work: ZFS/ARC analysis, Grafana/Zabbix-oriented telemetry, and multi-server reliability reviews.

---

<p align="center"><i>Open to DevOps / DevSecOps / SRE Engineer roles where reliability, security, and engineering discipline are first-class priorities.</i></p>
