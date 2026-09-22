# Traipoap Hunthong

**DevSecOps Engineer**

📍 Nonthaburi, Thailand · 📞 +66 80 638 0921 · ✉️ [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
🔗 [GitHub](https://github.com/traipoap) · [LinkedIn](https://www.linkedin.com/in/traipoap-hunthong)

---

## About Me

DevSecOps engineer with **4+ years** of Network administration (IaaS/PaaS) experience in a national telco cloud environment, now focused on **secure, automated Kubernetes delivery**. **CKA & CKAD certified.** Designed and operate an end-to-end GitOps platform across **3 production-structured repositories (infra / app / gitops)** — Terraform, Ansible, K3s, Istio, FluxCD, GitHub Actions — with **security built into the pipeline** (secret scanning, SAST, container image vulnerability scanning — **67 critical & high-severity vulnerabilities remediated** — TLS automation, RBAC, Kyverno admission policies, secrets management), running in production ([app.traipoap.com](https://app.traipoap.com)), cutting cluster provisioning from hours to **under an hour** with **zero manual deployment steps**.

---

## Technical Skills

| Category | Skills |
|---|---|
| **Cloud & IaaS** | IaaS/PaaS cloud operations (national telco), OpenStack (VPC, Subnet, ELB, NAT, VPN Gateway, Security Groups, ACL), VMware vSphere, AWS (EC2, IAM, Secrets Manager), Proxmox VE |
| **Cloud Native & Orchestration** | Kubernetes (K3s, embedded etcd, HA-capable), Docker, Helm, Kustomize, Istio (ambient profile / Gateway API), cert-manager, container runtimes (crun, youki RuntimeClass) |
| **CI/CD & GitOps** | GitHub Actions, FluxCD (GitRepository, Kustomization, ImageAutomation, ArtifactGenerator), GHCR |
| **DevSecOps & Compliance** | Vulnerability management, SAST (SonarQube), Trivy (image scanning, CRITICAL/HIGH gate), Gitleaks (secret scanning), External Secrets Operator + AWS SecretsManager, Kyverno (admission policies), RBAC, NetworkPolicy, TLS / private-CA encryption, secrets management, security policy & change management |
| **IaC & Automation** | Terraform (HCP remote state), Ansible, Go, Bash, Python |
| **Monitoring & Logging** | Prometheus, Grafana, Kiali, Vector, Quickwit, Zabbix |
| **Networking & Security** | TCP/IP, BGP, DNS, HAProxy (L7 LB, sticky sessions, syslog relay), Nginx, firewall policy |

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

- Built and run a log-search platform **in production** ([app.traipoap.com](https://app.traipoap.com)) — Go API (JWT auth, Quickwit search, CSV export) + Astro/JS dashboard.
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

### Network Administrator (IaaS/PaaS Support) · Jan 2022 – Present
**360 Bizmate Co., Ltd.** — assigned to National Telecom Public Company Limited (NT) Cloud Service

- **Reduced MTTR by 92%** (60 min → 5 min) by implementing proactive ingress traffic monitoring with Zabbix to detect silent failures bypassing traditional node-down alerts.
- **Maintained 99.99% network availability** for cloud service infrastructure through proactive monitoring and systematic troubleshooting.
- Automated multi-node health checks, reducing daily manual inspection by **95%** (20 min → 1 min/day).
- Eliminated IPv6 security policy conflicts by disabling automatic configuration, achieving **100% firewall policy compliance**.
- Acted as **Tier 2 network support engineer** — resolved escalated incidents and coordinated with L1/L3/vendor teams under SLA.
- Executed Change/Service Requests: VLAN provisioning, network configuration changes, infrastructure updates.
- Maintained device configuration backups and data center diagrams as single source of truth; mentored L1 team; prepared monthly operational reports for management.

---

## Education

**Bachelor of Science in Computer Science** — Rajamangala University of Technology Pranakorn · Aug 2014 – May 2018

---

## Languages

- **Thai** — Native
- **English** — Intermediate

---

## Additional Information

- Hackathon: GATI_Team — received the **"WINNER AWARD"**, AgTech AI Incubation 2023
