# Traipoap Hunthong

**Platform Engineer**

📍 Nonthaburi, Thailand · 📞 +66 80 638 0921 · ✉️ [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
🔗 [GitHub](https://github.com/traipoap) · [LinkedIn](https://www.linkedin.com/in/traipoap-hunthong)

---

## Summary

Platform Engineer building an automated self-hosted developer platform — infrastructure as code, GitOps delivery, and a golden path for new workloads — structured like a real platform team across 3 repositories (infra / app / gitops) with fully automated handoff.

4+ years of network and cloud operations at a national telco — 99.99% availability, 92% MTTR reduction (60→5 min). CKA & CKAD certified. Platform provisioned from zero in under an hour; zero manual deployment steps.

---

## Skills

| Category | Skills |
|---|---|
| **Platform & Orchestration** | Kubernetes (K3s), Docker, Podman, Istio, Gateway API, Huawei CCE |
| **Infrastructure as Code (IaC)** | Terraform, Ansible, Proxmox VE, cloud-init |
| **GitOps & CI/CD** | FluxCD, Kustomize, Helm, GitHub Actions, GHCR |
| **Cloud Platforms** | AWS, VMware vSphere, OpenStack |
| **Developer Experience** | Go, Python, Bash, Astro/JS |
| **Observability** | Prometheus, Grafana, Kiali, Vector, Quickwit, Zabbix |
| **Platform Security** | Gitleaks, SonarQube, Trivy, RBAC, NetworkPolicy, Kyverno, External Secrets |
| **Linux & Networking** | Debian, Ubuntu, TCP/IP, DNS, VLAN, IPv4/IPv6, HAProxy, Load Balancing, NFS |

---

## Certifications

| Certification | Issuer | Valid |
|---|---|---|
| **CKA** — Certified Kubernetes Administrator | Linux Foundation | Mar 2026 – Mar 2028 |
| **CKAD** — Certified Kubernetes Application Developer | Linux Foundation | Jul 2026 – Jul 2028 |

---

## Key Projects — Self-Hosted Developer Platform

> **Live:** [app](https://app.traipoap.com) · [flux-web](https://flux-web.traipoap.com) · [grafana](https://grafana.traipoap.com) · [kiali](https://kiali.traipoap.com) · [sonarqube](https://sonarqube.traipoap.com)

### 1. infra — Platform foundation · [github.com/traipoap/infra](https://github.com/traipoap/infra)

- **The platform is the product:** provisions the full foundation — super node (HAProxy L7 LB + syslog relay, NFS, Garage S3) + K3s master + worker — from zero in **under an hour**, fully repeatable; `terraform destroy` tears it down.
- Terraform (template-clone VMs, count-driven node scaling, HCP remote state — renders the Ansible inventory + HAProxy config from state) → Ansible (6 idempotent playbooks, kernel tuning) → K3s (embedded etcd, HA-capable — extra masters auto-join via shared token) → Istio (ambient) + Gateway API → FluxCD bootstrap from GitHub.
- **Multi-runtime container support:** crun as default runtime, youki exposed as a Kubernetes `RuntimeClass`.
- Documented **14 architecture decisions** + deployment and troubleshooting runbook — the platform's operating playbook.

### 2. app — Golden-path application · [github.com/traipoap/app](https://github.com/traipoap/app)

- Built and run a log-search platform — Go API (JWT auth, Quickwit search, CSV export) + Astro/JS dashboard — **self-hosted on the same platform in a personal production environment** ([app.traipoap.com](https://app.traipoap.com)) (dogfooding).
- **Golden-path release pipeline** on GitHub Actions: Gitleaks secret scan + SonarQube SAST gate → path-filtered image build → Trivy vulnerability scan (CRITICAL/HIGH gate, SARIF) → push to GHCR → FluxCD auto-deploy — **zero manual deployment steps**.
- **Platform quality policy:** enforced a "no critical/high in production" gate — caught and eliminated **67 critical & high-severity** container vulnerabilities.

### 3. gitops — Platform control plane · [github.com/traipoap/gitops](https://github.com/traipoap/gitops)

- **GitOps source of truth** for the K3s cluster — all state in Git, continuously reconciled by FluxCD, self-healing from configuration drift.
- **Multi-environment foundation:** base + staging + production overlays for every new workload; **self-service for new services** — 1 Gateway host + 1 cert-manager certificate + 1 HTTPRoute, TLS auto-issued.
- **Secrets never in Git:** External Secrets Operator + AWS SecretsManager — JWT, registry, and storage credentials synced into the cluster.
- **Platform guardrails:** Kyverno admission policies + LimitRange defaults across all namespaces; manifest validation (flux-schema).
- **Supply chain:** FluxCD Image Automation (ImageRepository + semver ImagePolicy) — new images auto-detected, tags updated, auto-deployed.
- **Observability as a service:** Prometheus, [Grafana](https://grafana.traipoap.com), [Kiali](https://kiali.traipoap.com), Vector → Quickwit centralized logging; Flux Web UI in server-only mode ([flux-web.traipoap.com](https://flux-web.traipoap.com)).

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
- **English** — Working proficiency

---

## Additional Information

- Hackathon — **Winner Award**, AgTech AI Incubation 2023 (Team GATI)
