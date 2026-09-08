TRAIPOAP HUNTHONG
Tel: +66 80 638 0921 | E-mail: traipoap@hotmail.com | Location: Nonthaburi, Thailand
GitHub: https://github.com/traipoap | Linkedin: https://www.linkedin.com/in/traipoap-hunthong
DevOps Engineer

ABOUT ME
Network administrator with 4+ years of enterprise cloud & network operations (IaaS/PaaS) experience in a national telco cloud environment, now transitioning to DevOps. CKA / CKAD certified, with a proven record in SLA-based incident response (92% MTTR reduction), change management, and vendor coordination. Hands-on experience designing and operating a fully automated Kubernetes platform — Terraform, Ansible, K3s (HA), FluxCD, Istio, GitHub Actions — reducing cluster provisioning from hours to ~20 minutes with zero manual deployment steps.

TECHNICAL SKILLS
Cloud Native & GitOps: Kubernetes (K3s, HA/etcd), Docker, Helm, Kustomize, Istio (Service Mesh, Gateway API), FluxCD (GitRepository, Kustomization, ImageAutomation), cert-manager
IaC & Automation: Terraform, Ansible, Proxmox VE, VMware vSphere, OpenStack, Python (AI Hackathon), Bash, Go (backend)
CI/CD & Observability: GitHub Actions, Container Registry, Prometheus, Grafana, Kiali, Vector, Quickwit, Zabbix
Networking & Security: Linux, TCP/IP, BGP, Cisco ACI, NSX-T, HAProxy, Nginx, RBAC, NetworkPolicy

CERTIFICATIONS
Certified Kubernetes Administrator (CKA) | Linux Foundation | Valid: Mar 2026 – Mar 2028
Certified Kubernetes Application Developer (CKAD) | Linux Foundation | Valid: July 2026 – July 2028

KEY DEVOPS & AUTOMATION PROJECTS
K3s GitOps Platform on Proxmox: In Progress
Infrastructure & Cluster Automation: https://github.com/traipoap/gitops-platform
GitOps Fleet Management: https://github.com/traipoap/fleet-infra
gitops-platform:
Designed an end-to-end automated Kubernetes platform: Terraform (template-clone VM provisioning, count-driven cluster scaling) → Ansible (idempotent roles, kernel tuning) → K3s HA (3 masters, embedded etcd) → Istio Service Mesh → FluxCD GitOps.
Reduced infrastructure provisioning time from several hours to ~20 minutes; eliminated all manual Kubernetes deployment steps.
Built CI/CD pipelines with GitHub Actions: lint/test → build image → push to registry → auto-update GitOps repo → FluxCD deploys.
Implemented observability: Prometheus, Grafana, Kiali, and a centralized Vector → Quickwit logging pipeline.
Delivered two-tier storage (NFS RWX + Garage S3), HAProxy/Keepalived load balancing, and cert-manager TLS automation (self-signed dev, Let’s Encrypt HTTP-01/DNS-01 prod).
Documented 12 architecture decisions + deployment and troubleshooting runbooks.

fleet-infra:
Operate the GitOps source of truth for a K3s HA cluster — all state in Git, continuously reconciled by FluxCD with self-healing configuration drift.
Designed an ArtifactGenerator-based layout cleanly separating infrastructure controllers (Helm), configs (YAML), and per-environment app overlays (base + staging).
Implemented External Secrets Operator + AWS SecretsManager — JWT, registry, and storage credentials synced into the cluster, never stored in Git.
Set up FluxCD Image Automation (ImageRepository + semver ImagePolicy) — new images auto-detected, tags updated, and auto-deployed.
Added manifest validation (validate.sh) and cluster-wide resource guardrails (LimitRange + resource-request requirements).

EXPERIENCE
Network Administrator (IaaS/PaaS Support) | Jan 2022 - Present
Employed by 360 Bizmate Co., Ltd. Assigned to National Telecom Public Company Limited (NT) Cloud Service
Reduced MTTR by 92% (60 min → 5 min) by implementing proactive ingress traffic monitoring with Zabbix to detect silent failures bypassing traditional node-down alerts.
Maintained 99.99% network availability for cloud service infrastructure through proactive monitoring and systematic troubleshooting.
Automated multi-node health checks, reducing daily manual inspection by 95% (20 min → 1 min/day).
Eliminated IPv6 security policy conflicts by disabling automatic configuration, achieving 100% firewall policy compliance.
Acted as Tier 2 network support engineer — resolved escalated incidents and coordinated with L1/L3/vendor teams under SLA.
Executed Change/Service Requests: VLAN provisioning, network configuration changes, infrastructure updates.
Maintained device configuration backups and data center diagrams as single source of truth; mentored L1 team; prepared monthly operational reports for management.

EDUCATION
Rajamangala University of Technology Pranakorn
Bachelor of Science in Computer Science | Aug 2014 - May 2018

LANGUAGES
Thai: Native
English: Intermediate (Technical Reading & Writing)

ADDITIONAL INFORMATION
Hackathon: GATI_Team
Received the "The WINNER AWARD", AgTech AI Incubation 2023
