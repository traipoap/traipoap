# TRAIPOAP HUNTHONG
Tel: +66 80 638 0921 | E-mail: traipoap@hotmail.com | Location: Nonthaburi, Thailand
GitHub: https://github.com/traipoap | LinkedIn: https://www.linkedin.com/in/traipoap-hunthong

**DevSecOps Engineer**

## ABOUT ME
DevSecOps engineer with 4+ years of Network administration (IaaS/PaaS) experience in a national telco cloud environment, now focused on secure, automated Kubernetes delivery. CKA & CKAD certified. Designed and operate an end-to-end GitOps platform — Terraform, Ansible, K3s, Istio, FluxCD, GitHub Actions — with security built into the pipeline (secret scanning, container image vulnerability scanning (67 critical & high-severity vulnerabilities remediated), TLS automation, RBAC, NetworkPolicy), cutting cluster provisioning from hours to under an hour with zero manual deployment steps.

## TECHNICAL SKILLS
- **Cloud Native & Orchestration:** Kubernetes (K3s, HA/etcd), Docker, Helm, Kustomize, Istio (Service Mesh / microservices), cert-manager
- **CI/CD & GitOps:** GitHub Actions, FluxCD (GitOps), ImageAutomation, Git-based delivery
- **DevSecOps & Compliance:** Vulnerability management, SAST (SonarQube), Trivy (container image scanning), Gitleaks (secret scanning), External Secrets Operator, Kyverno (admission policies), RBAC (access control), NetworkPolicy, TLS / private-CA encryption, security policy & change management
- **IaC & Automation:** Terraform, Ansible, Proxmox VE, VMware vSphere, OpenStack
- **Scripting:** Go, Bash, Python
- **Cloud & Storage:** IaaS/PaaS cloud operations, AWS (SecretsManager), S3-compatible object storage (Garage)
- **Monitoring & Logging:** Prometheus, Grafana, Kiali, Vector, Quickwit, Zabbix
- **Networking & Security:** TCP/IP, DNS, Routing, load balancing, firewall policy

## CERTIFICATIONS
- **Certified Kubernetes Administrator (CKA)** | Linux Foundation | Valid: Mar 2026 – Mar 2028
- **Certified Kubernetes Application Developer (CKAD)** | Linux Foundation | Valid: Jul 2026 – Jul 2028

## KEY PROJECTS — Kubernetes GitOps Platform (DevSecOps focus)

### gitops-platform
https://github.com/traipoap/gitops-platform
- Designed an end-to-end automated Kubernetes platform: Terraform (template-clone VM provisioning, count-driven cluster scaling) → Ansible (idempotent roles, kernel tuning) → K3s HA (3 masters, embedded etcd) → Istio Service Mesh → FluxCD GitOps.
- **Security-first CI/CD pipeline on GitHub Actions:** Gitleaks + SonarQube gate → path-filtered image build → Trivy vulnerability scan → push to GHCR → FluxCD auto-deploy.
- **Vulnerability management:** Trivy-based image scanning enforced a "no critical/high in production" gate, eliminating **67 critical & high-severity** container vulnerabilities.
- **Container & network security:** cert-manager TLS with a private CA, RBAC, NetworkPolicy, and a Kyverno admission policy injecting missing resource requests/limits.
- **Observability & centralized logging:** Prometheus, Grafana, Kiali, and a Vector → Quickwit logging pipeline.
- **High-availability delivery:** two-tier storage (NFS RWX + Garage S3) and HAProxy/Keepalived load balancing.
- Reduced infrastructure provisioning time from several hours to under an hour; eliminated all manual Kubernetes deployment steps. Documented 16 architecture decisions + deployment and troubleshooting runbooks.

### fleet-infra (GitOps fleet management)
https://github.com/traipoap/fleet-infra
- Operate the GitOps source of truth for a K3s HA cluster — all state in Git, continuously reconciled by FluxCD with self-healing configuration drift.
- **Secrets & security:** External Secrets Operator + AWS SecretsManager — JWT, registry, and storage credentials synced into the cluster, never stored in Git.
- Designed an ArtifactGenerator-based layout cleanly separating infrastructure controllers (Helm), configs (YAML), and per-environment app overlays (base + staging + production).
- Set up FluxCD Image Automation (ImageRepository + semver ImagePolicy) — new images auto-detected, tags updated, and auto-deployed.
- Added manifest validation (validate.sh), LimitRange defaults across all namespaces, and a Kyverno cluster policy; deployed Flux Web UI (flux-operator) for at-a-glance GitOps visibility.

## EXPERIENCE
### Network Administrator (IaaS/PaaS Support) | Jan 2022 – Present
Employed by 360 Bizmate Co., Ltd. — assigned to National Telecom Public Company Limited (NT) Cloud Service
- Reduced MTTR by 92% (60 min → 5 min) by implementing proactive ingress traffic monitoring with Zabbix to detect silent failures bypassing traditional node-down alerts.
- Maintained 99.99% network availability for cloud service infrastructure through proactive monitoring and systematic troubleshooting.
- Automated multi-node health checks, reducing daily manual inspection by 95% (20 min → 1 min/day).
- Eliminated IPv6 security policy conflicts by disabling automatic configuration, achieving 100% firewall policy compliance.
- Acted as Tier 2 network support engineer — resolved escalated incidents and coordinated with L1/L3/vendor teams under SLA.
- Executed Change/Service Requests: VLAN provisioning, network configuration changes, infrastructure updates.
- Maintained device configuration backups and data center diagrams as single source of truth; mentored L1 team; prepared monthly operational reports for management.

## EDUCATION
Rajamangala University of Technology Pranakorn
Bachelor of Science in Computer Science | Aug 2014 – May 2018

## LANGUAGES
Thai: Native
English: Intermediate (Technical Reading & Writing)

## ADDITIONAL INFORMATION
Hackathon: GATI_Team — Received the "The WINNER AWARD", AgTech AI Incubation 2023
