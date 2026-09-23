# Traipoap Hunthong

**DevSecOps Engineer**

📍 Nonthaburi, Thailand · 📞 +66 80 638 0921 · ✉️ [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
🔗 [GitHub](https://github.com/traipoap) · [LinkedIn](https://www.linkedin.com/in/traipoap-hunthong)

---

## Summary

Network Administrator with **4+ years** of network administration experience in a national telco cloud environment, now focused on **secure, automated Kubernetes delivery**. **CKA & CKAD certified.**

Design and operate an end-to-end GitOps platform across **3 production-structured repositories (infra / app / gitops)** — Terraform, Ansible, K3s, Istio, FluxCD, GitHub Actions — with **security built into the pipeline**: secret scanning, SAST, container image vulnerability scanning (**67 critical & high-severity vulnerabilities remediated**), TLS automation, Kyverno admission policies, and secrets management.

Running self-hosted in a personal production environment ([app.traipoap.com](https://app.traipoap.com)) — cluster provisioning cut from hours to **under an hour**, with **zero manual deployment steps**.

---

## Skills

| Category | Skills |
|---|---|
| **Security in CI/CD Pipelines** | Gitleaks, SonarQube, Trivy |
| **DevOps & Infrastructure as Code (IaC)** | Docker, Podman, Kubernetes, CCE, Istio, Terraform, Ansible, FluxCD, GitHub Actions, AWS |
| **Coding and Scripting** | Bash, Python, Go |
| **Linux & Monitoring** | Debian, Ubuntu, Zabbix, Prometheus, Grafana |
| **Cybersecurity & Threat Modeling** | WAZUH |

---

## Certifications

| Certification | Issuer | Valid |
|---|---|---|
| **CKA** — Certified Kubernetes Administrator | Linux Foundation | Mar 2026 – Mar 2028 |
| **CKAD** — Certified Kubernetes Application Developer | Linux Foundation | Jul 2026 – Jul 2028 |

---

## Key Projects — K3s Platform on Proxmox (DevSecOps focus)

> **Live:** [app](https://app.traipoap.com) · [flux-web](https://flux-web.traipoap.com) · [grafana](https://grafana.traipoap.com) · [kiali](https://kiali.traipoap.com) · [sonarqube](https://sonarqube.traipoap.com)

### 1. infra — Terraform + Ansible · [github.com/traipoap/infra](https://github.com/traipoap/infra)

- Built an end-to-end automated K3s platform: Terraform (template-clone VMs, count-driven scaling, HCP remote state) → Ansible (6 idempotent playbooks) → K3s (embedded etcd, HA-capable) → Istio (ambient) + Gateway API → FluxCD bootstrap.
- **Secrets never in git:** Terraform reads gitignored `secrets.auto.tfvars`; Ansible reads environment variables.
- **Hardened edge:** Garage S3 admin API bound to loopback only under a sandboxed systemd unit (`ProtectSystem=strict`, `NoNewPrivileges`); **TLS 1.2+ enforced** on HAProxy; narrowly-scoped Flux GitHub token (single repo, read/write).
- Provisions the full platform (super-node: HAProxy L7 + syslog relay, NFS, Garage S3; K3s master; worker) from zero in **under an hour**; `terraform destroy` tears it down. Documented **14 architecture decisions** + troubleshooting runbook.

### 2. app — Go/GIN + Astro · security-first release pipeline · [github.com/traipoap/app](https://github.com/traipoap/app)

- Built and run a log-search platform, **self-hosted in a personal production environment** ([app.traipoap.com](https://app.traipoap.com)) — Go API (JWT auth, Quickwit search, CSV export) + Astro/JS dashboard.
- **Security-first CI/CD pipeline on GitHub Actions:** Gitleaks (secret scan of full history) + SonarQube (SAST) gate → path-filtered image build → **Trivy image scan (CRITICAL/HIGH gate, SARIF to GitHub Security tab)** → push to GHCR → FluxCD auto-deploy.
- **Vulnerability management:** enforced a "no critical/high in production" gate — caught and eliminated **67 critical & high-severity** container vulnerabilities.

### 3. gitops — FluxCD GitOps · secrets, policy, supply chain · [github.com/traipoap/gitops](https://github.com/traipoap/gitops)

- Operate the **GitOps source of truth** for the K3s cluster — all state in Git, continuously reconciled by FluxCD with self-healing configuration drift.
- **Secrets & security:** External Secrets Operator + **AWS SecretsManager** — JWT, registry, and storage credentials synced into the cluster, never stored in Git.
- **Policy & hardening:** Kyverno admission policy injecting missing resource requests/limits + LimitRange defaults across all namespaces.
- **Supply chain:** FluxCD Image Automation (ImageRepository + semver ImagePolicy) — new images auto-detected, tags updated, auto-deployed; manifest validation (flux-schema) before deploy.
- Designed an ArtifactGenerator-based layout cleanly separating infrastructure controllers (Helm), configs (YAML), and per-environment app overlays (base + staging + production).
- **TLS & observability:** cert-manager TLS with a private CA; Prometheus, [Grafana](https://grafana.traipoap.com), [Kiali](https://kiali.traipoap.com), and a Vector → Quickwit centralized logging pipeline; Flux Web UI (flux-operator) in **credential-free server-only mode**.

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
