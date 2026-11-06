Hi ![](https://user-images.githubusercontent.com/18350557/176309783-0785949b-9127-417c-8b55-ab5a4333674e.gif)My name is Traipoap.

I design, build, and operate **Kubernetes platforms** where everything — infrastructure, configuration, and applications — is declared in Git and deployed automatically (GitOps). In practice, this means:

* ⏱️ A full platform (VMs, K3s cluster, service mesh, monitoring, logging) is provisioned in **under an hour** instead of several hours
* ✅ **No manual Kubernetes deployment steps** — the cluster continuously reconciles itself to the state declared in Git
* 🔁 A complete, repeatable rebuild of the environment — **structured like a real platform team: infra, app, and gitops repos with an automated handoff between them**
* 🔒 **Security built into the pipeline** — secret scanning, SAST, and container image vulnerability scanning

## What I do

| Skill | In plain terms |
|---|---|
| **Infrastructure as Code** (Terraform, Ansible) | VMs, OS setup, and cluster installs are created from code — no manual clicks |
| **GitOps** (Argo CD, FluxCD, Kustomize, Helm) | The cluster stays in sync with Git automatically; configuration drift is detected and corrected |
| **CI/CD & DevSecOps** (GitHub Actions, Docker) | Push code → security gate (Gitleaks, SonarQube SAST, Trivy image scan) → build image → deploy, fully automated |
| **Kubernetes & service mesh** (K3s, Istio, Gateway API) | K8s clusters with routing, TLS, and traffic visibility — **HA-ready by design** (masters auto-join via etcd token) |
| **Observability** (Prometheus, Grafana, Kiali, OpenTelemetry, Loki) | Metrics, dashboards, service-mesh traffic views, and centralized log search |
| **Security & storage** (NFS, Garage S3, RBAC, NetworkPolicy, LimitRange) | Persistent + S3-compatible storage, edge TLS, access control & resource governance |
| **Application operations** (Go, JS) | Operate polyglot stacks — Go APIs, Astro/JS frontends |

## 🟢 Live Demos
| Service | URL |
|---|---|
| Log-Search App | https://app.traipoap.com |
| Argo CD (GitOps UI) | https://argocd.traipoap.com |
| Grafana (Observability) | https://grafana.traipoap.com |
| Kiali (Service Mesh) | https://kiali.traipoap.com |
| SonarQube (SAST) | https://sonarqube.traipoap.com |

## Selected Projects

> A full platform split into **3 focused repos** — the same structure a production platform team uses:

### [Infra — K3s Platform on Proxmox](https://github.com/traipoap/infra)
*Terraform + Ansible — the entire VM/virtualization layer, as code*

* ⏱️ **Provisions the full platform from zero in under an hour** — super node (HAProxy LB, NFS, Garage S3) + K3s master + worker — repeatable, no manual steps
* 🔁 **Count-driven scaling** — node roles are generated from two variables; **HA-capable by design** (additional masters auto-join via etcd token) — this deployment is sized to a 16 GB lab host
* 🧱 Documented trade-offs: one super node hosts LB + storage + S3 (single point of failure — mitigated by NFS/Garage backups) with a scale-out path in the architecture decisions
* Stack: Terraform, Ansible, Proxmox VE, K3s, Istio, NFS, Garage (S3), cloud-init

### [App — Log-Search Platform](https://github.com/traipoap/app)
*Go/GIN + Astro — the application, with a security-first release pipeline*

* 🔒 **Security gates on every build**: Gitleaks (secret scan) + SonarQube (SAST) → build → **Trivy image scan (CRITICAL/HIGH gate, SARIF)** → GHCR — **caught & eliminated 127 critical/high-severity vulnerabilities**
* ⚡ Go API (JWT auth, log search, CSV export) + Astro/JS dashboard
* Stack: Go (Gin), Astro/JS, Docker, GitHub Actions, Gitleaks, SonarQube, Trivy, GHCR

### [GitOps — FluxCD](https://github.com/traipoap/gitops)
*First generation of the platform's GitOps — cluster source of truth on FluxCD*

* 🔄 **FluxCD** for the K3s cluster (embedded etcd; HA-ready: masters auto-join via etcd token) — continuous reconciliation, self-healing drift
* 🖼️ **FluxCD Image Automation** (ImageRepository + semver ImagePolicy) — new images auto-detected, tags updated, deployed
* 🔐 **Secrets out of Git**: External Secrets Operator ← **AWS SecretsManager**
* 🌐 **flux-web UI** (flux-operator) in server-only mode for cluster visibility
* 🚦 **base → staging → production** overlays (Kustomize/Helm) with per-cluster bootstrapping

### [GitOps — Argo CD](https://github.com/traipoap/argocd-bootstrap)
*Current GitOps controller — the platform now reconciles on Argo CD*

* 🔄 **Argo CD** (bootstrap repo + apps) — continuous reconciliation, self-healing drift; **Argo CD Image Updater** (semver policy → auto-update → deploy)
* 📜 **OpenTelemetry → Loki** centralized logging + Grafana datasources, **Argo CD UI** for cluster health (argocd.traipoap.com)
* 🛡️ **LimitRange defaults** across all namespaces + manifest validation
* ✅ **Both GitOps controllers — FluxCD and Argo CD — operated in real environments**, same Git-as-source-of-truth discipline

### [AWS — Multi-region Failover DR](https://github.com/traipoap/infra/tree/main/aws)
*Terraform for AWS — cross-provider disaster recovery for a production domain*

* 🌏 **Multi-region failover**: primary origin behind **CloudFront origin groups** with automatic failover on 4xx/5xx to a **Lambda (Go/Gin, ECR)** API and **S3** static build in ap-southeast-1/7 and us-east-1
* 🧩 **Terraform modules** (CloudFront, ECR, IAM, S3, ACM) — CloudFront Function for clean-URL routing, **OAC/SigV4** for private S3 access

## Certifications

* 🎓 **CKA** — [Certified Kubernetes Administrator](https://www.credly.com/badges/e592b729-06ce-4999-8686-92baf76c8662/public_url)
* 🎓 **CKAD** — [Certified Kubernetes Application Developer](https://www.credly.com/badges/4377148c-cbda-48ee-a063-6880e0086fd8/public_url)

## Contact

* 🌍 Based in Nonthaburi, Thailand
* ✉️ [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
* 🔗 [LinkedIn](https://www.linkedin.com/in/traipoap-hunthong)
* 💼 Open to **DevOps / Cloud & Infrastructure Engineer** roles — full-time, hybrid or remote
