# Traipoap Hunthong

**DevOps Engineer**

📍 Nonthaburi, Thailand · 📞 +66 80 638 0921 · ✉️ [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
🔗 [GitHub](https://github.com/traipoap) · [LinkedIn](https://www.linkedin.com/in/traipoap-hunthong)

---

## Summary

Network Administrator with 4+ years operating cloud infrastructure for a national telco — 99.99% availability and 92% MTTR reduction (60→5 min) achieved through proactive monitoring and automation.

CKA & CKAD certified.

Currently moving into DevOps, with a self-hosted platform to back it up: design, build, and operate an end-to-end GitOps Kubernetes platform in a personal production environment, across 3 production-structured repositories (infra / app / gitops) — Terraform, Ansible, K3s, Istio, FluxCD, GitHub Actions — zero manual deployment steps, provisioning cut from hours to under an hour.

---

## Skills

| Category | Skills |
|---|---|
| **Linux & Scripting** | Debian, Ubuntu, Bash, Python, Go |
| **CI/CD Pipelines** | GitHub Actions, FluxCD |
| **Containerization & Orchestration** | Docker, Podman, Kubernetes, CCE, Istio |
| **Infrastructure as Code (IaC)** | Terraform, Ansible |
| **Cloud Platforms** | AWS, VMware vSphere, OpenStack, Proxmox VE |
| **Monitoring & Observability** | Zabbix, Prometheus, Grafana, Kiali, Vector, Quickwit |
| **Security (DevSecOps)** | Gitleaks, SonarQube, Trivy |

---

## Certifications

| Certification | Issuer | Valid |
|---|---|---|
| **CKA** — Certified Kubernetes Administrator | Linux Foundation | Mar 2026 – Mar 2028 |
| **CKAD** — Certified Kubernetes Application Developer | Linux Foundation | Jul 2026 – Jul 2028 |

---

## Key Projects — K3s Platform on Proxmox

> **Live:** [app](https://app.traipoap.com) · [flux-web](https://flux-web.traipoap.com) · [grafana](https://grafana.traipoap.com) · [kiali](https://kiali.traipoap.com) · [sonarqube](https://sonarqube.traipoap.com)

### 1. infra — Terraform + Ansible · [github.com/traipoap/infra](https://github.com/traipoap/infra)

- Built an end-to-end automated K3s platform: Terraform (template-clone VMs, count-driven node scaling, HCP remote state — renders the Ansible inventory + HAProxy config from state) → Ansible (6 idempotent playbooks, kernel tuning) → K3s (embedded etcd; HA-capable — extra masters auto-join via shared token; deployed 1 master + 1 worker, sized to a 16 GB lab host) → Istio (ambient profile) + Gateway API → FluxCD bootstrap from GitHub.
- Provisions the full platform from zero in **under an hour** — super-node (HAProxy L7 LB + syslog relay fan-out, NFS, Garage S3) + K3s master + worker — fully repeatable; `terraform destroy` tears it down.
- Multi-runtime container support: crun as default runtime, youki exposed as a Kubernetes `RuntimeClass`.
- Documented **14 architecture decisions** + deployment and troubleshooting runbook.

### 2. app — Go/GIN + Astro · [github.com/traipoap/app](https://github.com/traipoap/app)

- Built and run a log-search platform, **self-hosted in a personal production environment** ([app.traipoap.com](https://app.traipoap.com)) — Go API (JWT auth, Quickwit search, CSV export) + Astro/JS dashboard.
- Built CI/CD pipelines with GitHub Actions: security gate (Gitleaks secret scan + SonarQube SAST) → path-filtered image build → Trivy vulnerability scan (CRITICAL/HIGH gate, SARIF) → push to GHCR → FluxCD auto-deploys.
- **Vulnerability management:** enforced a "no critical/high in production" gate — caught and eliminated **67 critical & high-severity** container vulnerabilities.

### 3. gitops — FluxCD GitOps · [github.com/traipoap/gitops](https://github.com/traipoap/gitops)

- Operate the **GitOps source of truth** for the K3s cluster — all state in Git, continuously reconciled by FluxCD with self-healing configuration drift.
- Designed an ArtifactGenerator-based layout cleanly separating infrastructure controllers (Helm), configs (YAML), and per-environment app overlays (base + staging + production).
- Implemented **External Secrets Operator + AWS SecretsManager** — JWT, registry, and storage credentials synced into the cluster, never stored in Git.
- Set up FluxCD **Image Automation** (ImageRepository + semver ImagePolicy) — new images auto-detected, tags updated, and auto-deployed.
- Added manifest validation (flux-schema), LimitRange defaults across all namespaces, and a **Kyverno** cluster policy injecting missing resource requests/limits.
- Implemented observability: Prometheus, [Grafana](https://grafana.traipoap.com), [Kiali](https://kiali.traipoap.com), and a centralized Vector → Quickwit logging pipeline; deployed Flux Web UI (flux-operator) in server-only mode ([flux-web.traipoap.com](https://flux-web.traipoap.com)).

---

## Experience

### Network Administrator · Jan 2022 – Present
**360 Bizmate Co., Ltd.** — assigned to National Telecom Public Company Limited (NT) Cloud Service

- **Reduced MTTR by 92%** (60 min → 5 min) by implementing proactive ingress traffic monitoring with Zabbix to detect silent failures bypassing traditional node-down alerts.
- **Maintained 99.99% network availability** for cloud service infrastructure through proactive monitoring and systematic troubleshooting.
- Automated multi-node health checks, reducing daily manual inspection by **95%** (20 min → 1 min/day).
- **Resolved IPv6 security policy conflicts** by disabling unintended IPv6 auto-configuration, restoring compliance with firewall security policies.
- Acted as **Tier 2 network support engineer** — resolved escalated incidents and coordinated with L1/L3/vendor teams under SLA.
- Executed Change/Service Requests: VLAN provisioning, network configuration changes, infrastructure updates.
- Maintained device configuration backups and data center diagrams as single source of truth; mentored L1 team; prepared monthly operational reports for management.

---

## Education

**Bachelor of Science in Computer Science** — Rajamangala University of Technology Phranakorn · Aug 2014 – May 2018

---

## Languages

- **Thai** — Native
- **English** — Intermediate

---

## Additional Information

- Hackathon: GATI_Team — received the **"WINNER AWARD"**, AgTech AI Incubation 2023
