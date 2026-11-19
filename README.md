Hi, I'm Traipoap.

I build and operate Kubernetes platforms where infrastructure, config, and apps live in Git and deploy automatically.

- A full platform (VMs, K3s, service mesh, monitoring, logging) provisions from zero in under an hour, and tears down just as cleanly
- No manual deploy steps: the cluster reconciles itself to Git
- Split into infra, app, and gitops repos, with automated handoff between them
- Security gates in the pipeline: secret scanning, SAST, image vulnerability scanning (137 critical/high caught and eliminated)

## What I do

| Skill | Notes |
|---|---|
| Infrastructure as Code (Terraform, Ansible) | VMs, OS setup, cluster install from code |
| GitOps (Argo CD, FluxCD, Kustomize, Helm) | Cluster follows Git; drift is detected and corrected |
| CI/CD (GitHub Actions, Docker) | Push, gate (Gitleaks, SonarQube, Trivy), build, deploy |
| Kubernetes (K3s, Istio, Cilium, Gateway API) | HA in production: 3 control-planes (etcd quorum) + 3 workers |
| Observability (Prometheus, Grafana, Kiali, OpenTelemetry, Loki, Vector, Quickwit) | Metrics, mesh traffic, centralized logs |
| Security & storage (NFS, Garage S3, RBAC, NetworkPolicy, LimitRange, Kyverno, cert-manager) | Storage, edge TLS, access control, resource limits |
| App operations (Go, JS) | Go APIs, Astro frontends |

## Live

| Service | URL |
|---|---|
| Portfolio | https://app.traipoap.com |
| Log-search app | https://app.traipoap.com/query |
| Argo CD | https://argocd.traipoap.com |
| Grafana | https://grafana.traipoap.com |
| SonarQube | https://sonarqube.traipoap.com |

## Projects

### Infra: K3s platform on Proxmox
[github.com/traipoap/infra](https://github.com/traipoap/infra) · Terraform + Ansible, the full virtualization layer as code

- Provisions the whole platform from zero in under an hour: super node (HAProxy LB, NFS, Garage S3), 3 K3s control-planes (etcd quorum), 3 workers. Repeatable, and `terraform destroy` tears it down
- Node roles come from two variables (count-driven scaling); extra masters auto-join via etcd token
- 3,400+ lines of IaC across 18 modules and roles
- Documented trade-offs: one super node hosts LB + storage + S3 (single point of failure, mitigated by NFS/Garage backups); scale-out path in the ADRs
- Stack: Terraform, Ansible, Proxmox VE, K3s, Istio, NFS, Garage (S3), cloud-init

### App: log-search platform
[github.com/traipoap/app](https://github.com/traipoap/app) · Go/Gin + Astro, security-first release pipeline

- Security gates on every build: Gitleaks, SonarQube, Trivy (CRITICAL/HIGH gate, SARIF) to GHCR. Caught and eliminated 137 critical/high vulnerabilities
- Go API (JWT auth, log search, CSV export), Astro dashboard
- Stack: Go (Gin), Astro, Docker, GitHub Actions, Gitleaks, SonarQube, Trivy, GHCR

### GitOps: FluxCD (first generation)
[github.com/traipoap/gitops](https://github.com/traipoap/gitops)

- FluxCD on the K3s cluster: continuous reconciliation, self-healing
- Image Automation (ImageRepository + semver ImagePolicy): images auto-detected, tags updated, deployed
- External Secrets Operator reading from AWS SecretsManager; no secrets in Git
- flux-web UI (flux-operator) in server-only mode
- base, staging, production overlays (Kustomize/Helm)
- Stack of that generation: Vector to Quickwit logging, cert-manager TLS, Kyverno policies

### GitOps: Argo CD (current)
[github.com/traipoap/argocd-bootstrap](https://github.com/traipoap/argocd-bootstrap)

- Argo CD (bootstrap repo + apps): reconciliation, self-healing, Image Updater (semver)
- OpenTelemetry to Loki logging, Grafana datasources, Argo CD UI (argocd.traipoap.com)
- LimitRange defaults in all namespaces, manifest validation
- Replaced FluxCD as the platform's controller; both generations ran real workloads

### AWS: multi-region failover DR
[github.com/traipoap/infra/aws](https://github.com/traipoap/infra/tree/main/aws) · Terraform for AWS, DR for a production domain

- CloudFront origin groups in front of the primary origin; on 4xx/5xx it fails over to a Lambda (Go/Gin, ECR) API and S3 static build in ap-southeast-1/7 and us-east-1
- Failover game-day: simulated origin failure, switchover in about 6 seconds, no data lost
- Terraform modules: CloudFront, ECR, IAM, S3, ACM; CloudFront Function for routing, OAC/SigV4 for private S3

## Certifications

- CKA: [Certified Kubernetes Administrator](https://www.credly.com/badges/e592b729-06ce-4999-8686-92baf76c8662/public_url)
- CKAD: [Certified Kubernetes Application Developer](https://www.credly.com/badges/4377148c-cbda-48ee-a063-6880e0086fd8/public_url)

## Contact

- Nonthaburi, Thailand
- [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
- [LinkedIn](https://www.linkedin.com/in/traipoap-hunthong)
- Open to DevOps / Cloud & Infrastructure Engineer roles: full-time, hybrid, remote
