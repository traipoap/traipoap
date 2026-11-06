# Traipoap Hunthong

**DevOps Engineer**

📍 Nonthaburi, Thailand · 📞 +66 80 638 0921 · ✉️ [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
🔗 [GitHub](https://github.com/traipoap) · [LinkedIn](https://www.linkedin.com/in/traipoap-hunthong)

---

## Summary

Network Administrator (CKA & CKAD certified) with 4+ years operating a national telco cloud.

Design, build, and operate an end-to-end GitOps Kubernetes platform in a personal production environment — Terraform, Ansible, K3s, Istio, Argo CD, GitHub Actions — with a multi-region failover DR layer on AWS (CloudFront, Lambda, S3). Zero manual deployment steps; provisioning cut from hours to under an hour.

---

## Skills

| Category | Skills |
|---|---|
| **Linux & Scripting** | Debian, Ubuntu, Bash, Python, Go |
| **CI/CD Pipelines** | GitHub Actions, Argo CD, FluxCD |
| **Containerization & Orchestration** | Docker, ECR, Kubernetes, Huawei CCE, Istio |
| **Infrastructure as Code (IaC)** | Terraform, Ansible |
| **Cloud Platforms** | AWS, VMware vSphere, OpenStack, Proxmox VE |
| **Monitoring & Observability** | Zabbix, Prometheus, Grafana, Kiali, OpenTelemetry, Loki |
| **Security (DevSecOps)** | Gitleaks, SonarQube, Trivy |

---

## Certifications

| Certification | Issuer | Valid |
|---|---|---|
| **CKA** — Certified Kubernetes Administrator | Linux Foundation | Mar 2026 – Mar 2028 |
| **CKAD** — Certified Kubernetes Application Developer | Linux Foundation | Jul 2026 – Jul 2028 |

---

## Key Projects — K3s Platform on Proxmox

> **Live:** [app](https://app.traipoap.com) · [argocd](https://argocd.traipoap.com) · [grafana](https://grafana.traipoap.com) · [kiali](https://kiali.traipoap.com) · [sonarqube](https://sonarqube.traipoap.com)

### 1. infra — Terraform + Ansible · [github.com/traipoap/infra](https://github.com/traipoap/infra)

- Built an automated K3s platform: Terraform (template-clone VMs, count-driven node scaling, HCP remote state — renders the Ansible inventory + HAProxy config from state) → Ansible (6 idempotent playbooks, kernel tuning) → K3s (embedded etcd; HA-capable — extra masters auto-join via shared token; deployed 1 master + 1 worker, sized to a 16 GB lab host) → Istio (ambient profile) + Gateway API → Argo CD bootstrap from GitHub.
- Provisions the full platform from zero in **under an hour** — super-node (HAProxy L7 LB + syslog relay fan-out, NFS, Garage S3) + K3s master + worker — fully repeatable; `terraform destroy` tears it down.
- Multi-runtime container support: crun as default runtime, youki exposed as a Kubernetes `RuntimeClass`.
- Documented **14 architecture decisions** + deployment and troubleshooting runbook.
- Extended the platform with a multi-region failover DR layer on AWS — see project 4

### 2. app — Go/GIN + Astro · [github.com/traipoap/app](https://github.com/traipoap/app)

- Built and run a log-search platform, **self-hosted in a personal production environment** ([app.traipoap.com](https://app.traipoap.com)) — Go API (JWT auth, Loki log search, CSV export) + Astro/JS dashboard.
- Built CI/CD pipelines with GitHub Actions: security gate (Gitleaks secret scan + SonarQube SAST) → path-filtered image build → Trivy vulnerability scan (CRITICAL/HIGH gate, SARIF) → push to GHCR → Argo CD auto-deploys.

### 3. FluxCD GitOps · [github.com/traipoap/gitops](https://github.com/traipoap/gitops)

- Operated the **GitOps source of truth** for the K3s cluster on **FluxCD** — all state in Git, continuously reconciled with self-healing configuration drift.
- **FluxCD Image Automation** (ImageRepository + semver ImagePolicy) — new images auto-detected, tags updated, and auto-deployed.
- **flux-web UI** (flux-operator) deployed in server-only mode for cluster visibility.
- **External Secrets Operator + AWS SecretsManager** — credentials synced into the cluster, never stored in Git.

### 4. Argo CD GitOps · [github.com/traipoap/argocd-bootstrap](https://github.com/traipoap/argocd-bootstrap)

- The current generation of the platform's GitOps layer on **Argo CD** — continuous reconciliation, self-healing drift; **Argo CD Image Updater** (semver policy) for automated image rollouts.
- Designed a layered layout cleanly separating infrastructure controllers (Helm), configs (YAML), and per-environment app overlays (base + staging + production).
- Added manifest validation and **LimitRange defaults** across all namespaces — every Pod declares CPU/memory requests & limits.
- Observability: Prometheus, [Grafana](https://grafana.traipoap.com), [Kiali](https://kiali.traipoap.com), centralized **OpenTelemetry → Loki** logging; **Argo CD UI** in server-only mode ([argocd.traipoap.com](https://argocd.traipoap.com)).
- **Both GitOps controllers — FluxCD and Argo CD — operated in real environments.**

### 5. aws — Multi-region failover DR · [github.com/traipoap/infra/tree/main/aws](https://github.com/traipoap/infra/tree/main/aws)
- Designed a multi-region disaster-recovery architecture: K3s primary origin behind AWS CloudFront origin groups, with automatic failover on 4xx and 5xx to a Lambda (Go/Gin, ECR container) API and an S3 static build in separate regions (ap-southeast-1/7, us-east-1) — cross-provider, cross-region continuity for app.traipoap.com
- Terraform modules (CloudFront, ECR, IAM, S3, ACM) with CloudFront Function for Astro clean-URL routing and OAC/SigV4 for private S3 access

---

## Experience

### Network Administrator · Jan 2022 – Present
**360 Bizmate Co., Ltd.** — assigned to National Telecom Public Company Limited (NT)

#### Responsibilities:
1. Serve as Level-2 (Tier-2) Network Support, coordinating with Level-1 Support and related teams (e.g., Level-3 Support / 3rd-party vendors) to ensure all tasks are completed within the service SLA
2. Resolve issues escalated from Level-1 Support, including problem analysis and gathering network-related diagnostic data
3. Execute assigned Change Requests or Service Requests, e.g., adding or modifying VLANs
4. Ensure accurate and up-to-date configuration backups of network devices
5. Collaborate with other teams to train and upskill Level-1 staff to improve overall efficiency
6. Collect required data and produce weekly reports within the assigned scope
7. Perform other duties as assigned

#### Achievements:
- **Reduced MTTR** by implementing proactive ingress traffic monitoring with Zabbix to detect silent failures bypassing traditional node-down alerts to Telegram.
- **Maintained network availability** for cloud service infrastructure through proactive monitoring and systematic troubleshooting.
- Automated multi-node health checks, reducing daily manual inspection.
- **Resolved IPv6 security policy conflicts** by disabling unintended IPv6 auto-configuration, restoring compliance with firewall security policies.
- Acted as **Tier 2 network support engineer** — resolved escalated incidents and coordinated with L1/L3/vendor teams under SLA.
---

## Education

**Bachelor of Science in Computer Science** — Rajamangala University of Technology Phranakorn · Aug 2014 – May 2018

---

## Languages

- **Thai** — Native
- **English** — Working proficiency

---

## Additional Information

- Hackathon: GATI_Team — received the **"WINNER AWARD"**, AgTech AI Incubation 2023
