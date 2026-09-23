# Traipoap Hunthong

**Cloud / Infrastructure Engineer**

📍 Nonthaburi, Thailand · 📞 +66 80 638 0921 · ✉️ [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
🔗 [GitHub](https://github.com/traipoap) · [LinkedIn](https://www.linkedin.com/in/traipoap-hunthong)

---

## Summary

Network Administrator with 4+ years supporting cloud in a national telecommunications environment — networking, monitoring, incident response, and automation.

CKA & CKAD certified.

Design, build, and operate a self-hosted end-to-end cloud-native stack — Terraform, Ansible, K3s, Istio, FluxCD, GitHub Actions — across 3 production-structured repositories (infra / app / gitops), HA-capable by design, with zero manual deployment steps. Track record: 99.99% availability, 92% MTTR reduction, 95% less daily manual inspection.

---

## Skills

| Category | Skills |
|---|---|
| **Cloud Platforms** | AWS, VMware vSphere, OpenStack, Proxmox VE |
| **Infrastructure as Code (IaC)** | Terraform, Ansible |
| **Containers & Orchestration** | Docker, Podman, Kubernetes, CCE, Istio |
| **Linux & Networking** | Debian, Ubuntu, TCP/IP, DNS, Load Balancing, VLAN, IPv4/IPv6, VPC, Subnet, Routing, VPC Peering, ELB, NAT Gateway, VPN Gateway |
| **Automation & CI/CD** | Python, Bash, Go, GitHub Actions, FluxCD |
| **Monitoring & Observability** | Zabbix, Prometheus, Grafana, Kiali, Vector, Quickwit |
| **Security & IAM** | Security Group, ACL, AWS Secrets Manager |

---

## Experience

### Network Administrator · Jan 2022 – Present
**360 Bizmate Co., Ltd.** — assigned to National Telecom Public Company Limited (NT) · Thailand

Support and operate network and infrastructure services within a national telecommunications cloud environment, working across infrastructure, network operations, incident response, troubleshooting, and infrastructure changes.

- Support network infrastructure for cloud services, including network configuration, troubleshooting, incident response, and infrastructure changes.
- **Maintain 99.99% network availability** through proactive monitoring, systematic troubleshooting, and incident prevention.
- Automate multi-node health checks, reducing daily manual inspection effort by **95%** (from ~20 minutes to ~1 minute per day).
- Troubleshoot network and infrastructure incidents involving routing, DNS, VLAN, load balancing, and IPv4/IPv6 connectivity.
- Act as **Tier 2 network support**, resolving escalated incidents and coordinating with L1/L3 engineers and vendors under SLA requirements.
- Execute service requests, including VLAN provisioning, network configuration, and load balancing.
- Maintain network device configuration backups, infrastructure documentation, and network diagrams as operational sources of truth.
- Mentor L1 support engineers and prepare monthly operational reports for management.

**Key Achievements:**

- **Reduced MTTR by 92%** (from ~60 minutes to ~5 minutes) by implementing proactive ingress traffic monitoring with Zabbix to detect silent failures that traditional node-down monitoring missed.
- **Resolved IPv6 security policy conflicts** by disabling unintended IPv6 auto-configuration, restoring compliance with firewall security policies.

---

## Projects

> **Live:** [app](https://app.traipoap.com) · [flux-web](https://flux-web.traipoap.com) · [grafana](https://grafana.traipoap.com) · [kiali](https://kiali.traipoap.com) · [sonarqube](https://sonarqube.traipoap.com)


### 1. K3s Platform on Proxmox (Infra) · [github.com/traipoap/infra](https://github.com/traipoap/infra)
**Stack:** Proxmox VE · Terraform · Ansible · K3s · Istio · FluxCD · HAProxy · NFS · Garage (S3)

- Built and operate a multi-VM Kubernetes infrastructure — super node (HAProxy LB, NFS, Garage S3), K3s master, worker — **provisioned from zero in under an hour** with zero manual deployment steps.
- Provisioned VMs with Terraform from optimized templates with cloud-init; **count-driven node scaling — HA-ready by design** (additional masters auto-join via etcd token), sized to a 16 GB lab host.
- Automated the cluster lifecycle with Ansible: OS prerequisites, kernel tuning, K3s install/HA join, service mesh, storage, and GitOps bootstrap — all idempotent and repeatable.
- Delivered load balancing, NFS persistent storage, and Garage S3 object storage.
- Documented **14 architecture decisions** (K3s vs kubeadm, GitOps vs kubectl, two-tier storage) plus backup/restore design (etcd snapshots, PVCs, S3 data).

### 2. Log-Search Platform (App) · [github.com/traipoap/app](https://github.com/traipoap/app)
  **Stack:** Go (Gin) · Astro/JS · Docker · GitHub Actions · Gitleaks · SonarQube · Trivy · GHCR

- Built and run a log-search platform, **self-hosted in a personal production environment** — Go API (JWT auth, Quickwit search, CSV export) + Astro/JS dashboard.
- Implemented a **security-first CI/CD pipeline**: Gitleaks + SonarQube SAST gates → build → Trivy image scan (CRITICAL/HIGH gate, SARIF) → GHCR — **caught and eliminated 67 critical/high-severity container vulnerabilities**.
- Verified images are promoted to the cluster automatically via FluxCD Image Automation — **no manual deployment step**.

### 3. GitOps Repository · [github.com/traipoap/gitops](https://github.com/traipoap/gitops)
**Stack:** FluxCD · Kustomize · Helm · Istio Gateway API · cert-manager · External Secrets · AWS Secrets Manager · Kyverno · Vector · Quickwit

- Operate the **GitOps source of truth** for the K3s cluster — all cluster state in Git, continuously reconciled by FluxCD, self-healing configuration drift.
- Built a **multi-environment foundation**: shared base + staging/production overlays, per-cluster Flux bootstrapping, ArtifactGenerator packaging, and manifest validation (flux-schema).
- Manage secrets securely with **External Secrets Operator + AWS Secrets Manager** — registry credentials, application JWTs, and storage endpoints kept out of Git.
- Enforce Kubernetes policy and hardening with **Kyverno policies and LimitRange defaults across all namespaces**.
- Automate TLS with cert-manager.
- Deploy and operate the Go API + Astro frontend behind an Istio Gateway (TLS, path-based routing), with Flux Web UI ([flux-web.traipoap.com](https://flux-web.traipoap.com)), Vector → Quickwit centralized logging, and Grafana dashboards ([grafana.traipoap.com](https://grafana.traipoap.com)) for operational visibility.

---

## Certifications

| Certification | Issuer | Valid |
|---|---|---|
| **CKA** — Certified Kubernetes Administrator | Linux Foundation | Mar 2026 – Mar 2028 |
| **CKAD** — Certified Kubernetes Application Developer | Linux Foundation | Jul 2026 – Jul 2028 |

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
