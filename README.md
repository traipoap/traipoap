Hi ![](https://user-images.githubusercontent.com/18350557/176309783-0785949b-9127-417c-8b55-ab5a4333674e.gif)My name is Traipoap.

I design, build, and operate **Kubernetes platforms** where everything — infrastructure, configuration, and applications — is declared in Git and deployed automatically (GitOps). In practice, this means:

* ⏱️ A full platform (VMs, K3s cluster, service mesh, monitoring, logging) is provisioned in **under an hour** instead of several hours
* ✅ **No manual Kubernetes deployment steps** — the cluster continuously reconciles itself to the state declared in Git
* 🔁 A complete, repeatable rebuild of the environment — **structured like a real platform team: infra, app, and gitops repos with an automated handoff between them**
* 🔒 **Security built into the pipeline** — secret scanning, SAST, and container image vulnerability scanning (caught & eliminated 67 critical/high-severity vulnerabilities)

## What I do

| Skill | In plain terms |
|---|---|
| **Infrastructure as Code** (Terraform, Ansible) | VMs, OS setup, and cluster installs are created from code — no manual clicks |
| **GitOps** (Flux CD, Kustomize, Helm) | The cluster stays in sync with Git automatically; configuration drift is detected and corrected |
| **CI/CD & DevSecOps** (GitHub Actions, Docker) | Push code → security gate (Gitleaks, SonarQube SAST, Trivy image scan) → build image → deploy, fully automated |
| **Kubernetes & service mesh** (K3s, Istio, Gateway API) | K8s clusters with routing, TLS, and traffic visibility — **HA-ready by design** (masters auto-join via etcd token) |
| **Observability** (Prometheus, Grafana, Kiali, Vector, Quickwit) | Metrics, dashboards, service-mesh traffic views, and centralized log search |
| **Security & storage** (NFS, Garage S3, cert-manager, RBAC, NetworkPolicy, Kyverno) | Persistent + S3-compatible storage, automated TLS, access control & admission policies |
| **Application operations** (Go, JS) | Operate polyglot stacks — Go APIs, Astro/JS frontends |

## Certifications

* 🎓 **CKA** — [Certified Kubernetes Administrator](https://www.credly.com/badges/e592b729-06ce-4999-8686-92baf76c8662/public_url)
* 🎓 **CKAD** — [Certified Kubernetes Application Developer](https://www.credly.com/badges/4377148c-cbda-48ee-a063-6880e0086fd8/public_url)

## Selected Projects

> A full platform split into **3 focused repos** — the same structure a production platform team uses:

### [Infra — K3s Platform on Proxmox](https://github.com/traipoap/infra)
*Terraform + Ansible — the entire VM/virtualization layer, as code*

* ⏱️ **Provisions the full platform from zero in under an hour** — super node (HAProxy LB, NFS, Garage S3) + K3s master + worker — repeatable, no manual steps
* 🔁 **Count-driven scaling** — node roles are generated from two variables; **HA-capable by design** (additional masters auto-join via etcd token) — this deployment is sized to a 16 GB lab host
* 🧱 Documented trade-offs: one super node hosts LB + storage + S3 (single point of failure — mitigated by NFS/Garage backups) with a scale-out path in the architecture decisions
* Stack: Terraform, Ansible, Proxmox VE, K3s, Istio, NFS, Garage (S3), cloud-init

### [App — Log-Search Platform](https://github.com/traipoap/app) · live: [app.traipoap.com](https://app.traipoap.com)
*Go/GIN + Astro — the application, with a security-first release pipeline*

* 🔒 **Security gates on every build**: Gitleaks (secret scan) + SonarQube (SAST) → build → **Trivy image scan (CRITICAL/HIGH gate, SARIF)** → GHCR — **caught & eliminated 67 critical/high-severity vulnerabilities**
* ⚡ Go API (JWT auth, log search, CSV export) + Astro/JS dashboard
* Stack: Go (Gin), Astro/JS, Docker, GitHub Actions, Gitleaks, SonarQube, Trivy, GHCR

### [GitOps — Flux CD Repository](https://github.com/traipoap/gitops)
*Source of truth for the cluster — verified images from the App repo land here and are deployed automatically*

* 🔄 **Flux CD** for the K3s cluster (embedded etcd; HA-ready: masters auto-join via etcd token) — continuous reconciliation, self-healing drift; **Image Automation** (semver policy → auto-commit → deploy)
* 🔐 **Secrets out of Git**: External Secrets Operator ← **AWS SecretsManager**; Kyverno policies + LimitRange defaults across all namespaces
* 📜 **Vector → Quickwit** centralized logging + Grafana datasources, **Flux Web UI** for cluster health
* 🚦 **base → staging → production** overlays with per-cluster bootstrapping
* Stack: Flux CD, Kustomize, Helm, Istio Gateway API, cert-manager, External Secrets, Kyverno, Vector, Quickwit

## Contact

* 🌍 Based in Nonthaburi, Thailand
* ✉️ [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
* 💼 Open to **DevOps / DevSecOps / Cloud & Infrastructure / Kubernetes** roles — full-time, hybrid or remote
