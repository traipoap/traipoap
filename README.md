Hi ![](https://user-images.githubusercontent.com/18350557/176309783-0785949b-9127-417c-8b55-ab5a4333674e.gif)My name is Traipoap.

# Platform / DevOps Engineer

I design, build, and operate **Kubernetes platforms** where everything — infrastructure, configuration, and applications — is declared in Git and deployed automatically (GitOps). In practice, this means:

* ⏱️ A full platform (VMs, K3s cluster, service mesh, monitoring, logging) is provisioned in **~20 minutes** instead of several hours
* ✅ **No manual Kubernetes deployment steps** — the cluster continuously reconciles itself to the state declared in Git
* 🔁 A complete, repeatable rebuild of the environment from a single repository

## What I do

| Skill | In plain terms |
|---|---|
| **Infrastructure as Code** (Terraform, Ansible) | VMs, OS setup, and cluster installs are created from code — no manual clicks |
| **GitOps** (Flux CD, Kustomize, Helm) | The cluster stays in sync with Git automatically; configuration drift is detected and corrected |
| **CI/CD** (GitHub Actions, Docker) | Push code → lint/test → build image → deploy, fully automated |
| **Kubernetes & service mesh** (K3s, Istio, Gateway API) | High-availability clusters with routing, TLS, and traffic visibility |
| **Observability** (Prometheus, Grafana, Kiali, Vector, Quickwit) | Metrics, dashboards, service-mesh traffic views, and centralized log search |
| **Storage & security** (NFS, Garage S3, cert-manager, RBAC) | Persistent + S3-compatible storage, automated TLS certificates, access control |
| **Application operations** (Go, JS) | Operate polyglot stacks — Go APIs, Astro/JS frontends |

## Certifications

* 🎓 **CKA** — [Certified Kubernetes Administrator](https://www.credly.com/badges/e592b729-06ce-4999-8686-92baf76c8662/public_url)
* 🎓 **CKAD** — [Certified Kubernetes Application Developer](https://www.credly.com/badges/4377148c-cbda-48ee-a063-6880e0086fd8/public_url)
* 📚 **AWS SAA** — AWS Solutions Architect Associate *(in progress)*

## Selected Projects

### [K3s GitOps Platform on Proxmox](https://github.com/traipoap/gitops-platform)
End-to-end platform automation: Terraform provisions the VMs, Ansible installs and configures the K3s cluster, and Flux CD then manages everything from Git — including the CI/CD pipeline, monitoring, centralized logging, and S3 object storage.

* ⏱️ **Reduced infrastructure provisioning time from several hours to ~20 minutes**
* ✅ **Eliminated manual Kubernetes deployment steps** — all workloads are declared in Git and auto-reconciled
* Stack: Terraform, Ansible, K3s, Flux CD, Istio, GitHub Actions, Prometheus, Grafana, Kiali, Vector, Quickwit, Garage (S3), NFS, cert-manager

### [Fleet Infra — Flux CD GitOps](https://github.com/traipoap/fleet-infra)
GitOps source of truth for a **K3s HA cluster (3 masters)** — all Kubernetes state declared in Git and continuously reconciled by Flux CD.

* 🔐 **TLS automation with cert-manager** (self-signed for dev, Let's Encrypt configured for prod)
* 📜 **Centralized logging pipeline**: Vector → Quickwit, with Grafana dashboards
* 📊 **Weave GitOps dashboard** for at-a-glance cluster health
* 🔄 **Multi-environment promotion design** (dev → staging → prod)
* Stack: Flux CD, Kustomize, Helm, Istio Gateway API, cert-manager, Vector, Quickwit

## Contact

* 🌍 Based in Nonthaburi, Thailand
* ✉️ [traipoap@hotmail.com](mailto:traipoap@hotmail.com)
* 💼 Open to Platform / DevOps Engineer roles
