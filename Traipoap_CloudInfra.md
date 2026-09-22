TRAIPOAP HUNTHONG
Cloud / Infrastructure Engineer | DevOps | Kubernetes
Tel: +66 80 638 0921 | E-mail: traipoap@hotmail.com | Location: Nonthaburi, Thailand
GitHub: https://github.com/traipoap | LinkedIn: https://www.linkedin.com/in/traipoap-hunthong

PROFESSIONAL SUMMARY
Cloud Infrastructure Engineer with 4+ years of experience supporting IaaS/PaaS cloud infrastructure in a national telecommunications environment (OpenStack-based), with a strong background in networking, infrastructure operations, automation, and Kubernetes.

Hands-on experience designing and operating a complete platform stack — Terraform, Ansible, K3s, FluxCD, GitHub Actions, Istio, Helm — from VM provisioning through GitOps-based application delivery, delivered across 3 production-structured repositories (infra / app / gitops). Experienced in infrastructure automation, high-availability design, network troubleshooting, security controls, observability, and incident response (99.99% availability; 92% MTTR reduction).

CKA and CKAD certified, with practical experience automating infrastructure from VM provisioning through Kubernetes deployment, security, monitoring, and GitOps-based application delivery.

CORE SKILLS
Cloud: VMware, OpenStack (VPC, Subnet, Routing, ELB, VPC Peering, NAT, VPN Gateway, Security Groups, ACL, CCE), AWS (EC2, IAM, Secrets Manager), Proxmox VE
Networking: TCP/IP, Routing, DNS, Load Balancing, VLAN, IPv4/IPv6
IaC & Automation: Terraform, Ansible, Bash
Kubernetes & Containers: Kubernetes, K3s, kubectl, Helm, Kustomize, Docker, FluxCD (Image Automation, ArtifactGenerator), Istio, cert-manager, RBAC, Kyverno, External Secrets
CI/CD & Monitoring: GitHub Actions (Gitleaks, SonarQube SAST, Trivy), Zabbix, Prometheus, Grafana, Kiali, Vector, Quickwit
Storage & Security: NFS, Garage (S3-compatible), PVC, TLS automation, secrets management (AWS Secrets Manager)

EXPERIENCE
Network Administrator (IaaS/PaaS)
360 Bizmate Co., Ltd. — Assigned to National Telecom Public Company Limited (NT)
Jan 2022 – Present | Thailand

Support and operate network and infrastructure services within a national telecommunications cloud environment, working across IaaS/PaaS infrastructure, network operations, incident response, troubleshooting, and infrastructure changes.

- Support network infrastructure for IaaS/PaaS cloud services, including network configuration, troubleshooting, incident response, and infrastructure changes.
- Maintain 99.99% network availability through proactive monitoring, systematic troubleshooting, and incident prevention.
- Automate multi-node health checks, reducing daily manual inspection effort by 95% (from ~20 minutes to ~1 minute per day).
- Troubleshoot network and infrastructure incidents involving routing, DNS, VLAN, load balancing, and IPv4/IPv6 connectivity.
- Act as Tier 2 network support, resolving escalated incidents and coordinating with L1/L3 engineers and vendors under SLA requirements.
- Execute service requests, including VLAN provisioning, network configuration, and load balancing.
- Maintain network device configuration backups, infrastructure documentation, and network diagrams as operational sources of truth.
- Mentor L1 support engineers and prepare monthly operational reports for management.

Key Achievements:
- Reduced MTTR by 92% (from ~60 minutes to ~5 minutes) by implementing proactive ingress traffic monitoring with Zabbix to detect silent failures that traditional node-down monitoring missed.
- Resolved IPv6 security policy conflicts by disabling unintended IPv6 auto-configuration, restoring compliance with firewall security policies.

PROJECTS
1) K3s Platform on Proxmox (Infra) — https://github.com/traipoap/infra
Stack: Proxmox VE · Terraform · Ansible · K3s · Istio · FluxCD · HAProxy · NFS · Garage (S3)

- Built and operate a multi-VM Kubernetes infrastructure — super node (HAProxy LB, NFS, Garage S3), K3s master, worker — provisioned from zero in under an hour with zero manual deployment steps.
- Provisioned VMs with Terraform from optimized templates with cloud-init; count-driven node scaling — HA-ready by design (additional masters auto-join via etcd token), sized to a 16 GB lab host.
- Automated the cluster lifecycle with Ansible: OS prerequisites, kernel tuning, K3s install/HA join, service mesh, storage, and GitOps bootstrap — all idempotent and repeatable.
- Delivered load balancing, NFS persistent storage, and Garage S3 object storage; resource optimization via LimitRange and Kyverno CPU/memory defaults.
- Documented 12 architecture decisions (K3s vs kubeadm, GitOps vs kubectl, two-tier storage) plus backup/restore design (etcd snapshots, PVCs, S3 data).

2) Log-Search Platform (App) — https://github.com/traipoap/app · Live: https://app.traipoap.com
Stack: Go (Gin) · Astro/JS · Docker · GitHub Actions · Gitleaks · SonarQube · Trivy · GHCR

- Built and run a log-search platform in production — Go API (JWT auth, Quickwit search, CSV export) + Astro/JS dashboard.
- Implemented a security-first CI/CD pipeline: Gitleaks + SonarQube SAST gates → build → Trivy image scan (CRITICAL/HIGH gate, SARIF) → GHCR — caught and eliminated 67 critical/high-severity container vulnerabilities.
- Verified images are promoted to the cluster automatically via FluxCD Image Automation — no manual deployment step.

3) GitOps Repository — https://github.com/traipoap/gitops
Stack: FluxCD · Kustomize · Helm · Istio Gateway API · cert-manager · External Secrets · AWS Secrets Manager · Kyverno · Vector · Quickwit

- Operate the GitOps source of truth for the K3s cluster — all cluster state in Git, continuously reconciled by FluxCD, self-healing configuration drift.
- Built a multi-environment foundation: shared base + staging/production overlays, per-cluster Flux bootstrapping, ArtifactGenerator packaging, and manifest validation (flux-schema).
- Manage secrets securely with External Secrets Operator + AWS Secrets Manager — registry credentials, application JWTs, and storage endpoints kept out of Git.
- Enforce Kubernetes policy and hardening with Kyverno policies and LimitRange defaults across 7 namespaces.
- Automate TLS with cert-manager.
- Deploy and operate the Go API + Astro frontend behind an Istio Gateway (TLS, path-based routing), with Flux Web UI, Vector → Quickwit centralized logging, and Grafana dashboards for operational visibility.

CERTIFICATIONS
Certified Kubernetes Administrator (CKA) | Linux Foundation | Valid: Mar 2026 – Mar 2028
Certified Kubernetes Application Developer (CKAD) | Linux Foundation | Valid: July 2026 – July 2028

EDUCATION
Rajamangala University of Technology Pranakorn
Bachelor of Science in Computer Science | Aug 2014 - May 2018
