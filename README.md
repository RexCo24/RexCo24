# Alexander Koch

Junior DevOps Engineer (career changer) · Katerini, Greece · open to remote roles (EU)

I moved into DevOps from an investigative/security role at an industrial site operator, where I ran video systems, built internal AI tooling and did OSINT research. Since 2026 I have been building a hands-on DevOps stack end to end: Linux, Docker, CI/CD, Terraform on Azure and AWS, Kubernetes, Ansible, Prometheus/Grafana.

I don't have professional DevOps experience yet. What I do have: a working demo stack I built myself, a systematic troubleshooting approach (symptom → hypothesis → test → fix), and a lot of practice diagnosing broken Kubernetes and Linux setups in a lab.

## Stack

| Area | Tools | Level |
|---|---|---|
| Containers & orchestration | Docker, Kubernetes (minikube), Helm | main focus – build, deploy, debug |
| Linux | Ubuntu Server, systemd, journalctl, nginx, cron, networking basics | daily use, troubleshooting |
| IaC | Terraform (azurerm, aws) | own projects, applied in AWS and Azure |
| CI/CD | GitHub Actions, Docker Hub | own pipelines (test → build → push) |
| Config management | Ansible | own playbooks |
| Monitoring | Prometheus, Grafana, kube-prometheus-stack | own setup on Kubernetes |
| Cloud | Azure (AZ-900 certified), AWS (basics) | Azure is the primary platform |
| Scripting | Python, Bash | automation scripts, Azure CLI |

## NordikTech demo stack

NordikTech Solutions is a fictional company. The five repositories below form one end-to-end delivery chain for a small Flask inventory API. Everything except the Azure Terraform apply was run and tested locally (Ubuntu 24.04 VM, minikube).

```
 Terraform (Azure)          GitHub Actions                Kubernetes (minikube)
 VNet · NSG · LB · VM  ──►  pytest → build → push  ──►  Deployment (3 replicas, probes, limits)
 [infra-demo]              [app-demo]                    NodePort Service · ServiceMonitor
                                                         [k8s-demo]
 Ansible                                                           │
 nginx reverse proxy · Flask as systemd service                    ▼
 [config-demo]                                          Prometheus + Grafana (Helm)
                                                         scrapes /metrics every 15s
                                                         [monitoring]
```

| Repository | What it does | Status |
|---|---|---|
| [nordiktech-infra-demo](https://github.com/RexCo24/nordiktech-infra-demo) | Azure staging infrastructure with Terraform: VNet, subnets, NSG, load balancer, Ubuntu VM | `validate`/`plan` verified; not applied (no active Azure subscription at the time) |
| [nordiktech-app-demo](https://github.com/RexCo24/nordiktech-app-demo) | Flask inventory API, pytest, Dockerfile, GitHub Actions pipeline to Docker Hub | pipeline runs green, image on Docker Hub |
| [nordiktech-config-demo](https://github.com/RexCo24/nordiktech-config-demo) | Ansible playbook: nginx reverse proxy, venv, Flask as systemd service | tested on Ubuntu 24.04 |
| [nordiktech-k8s-demo](https://github.com/RexCo24/nordiktech-k8s-demo) | Kubernetes Deployment with readiness/liveness probes, resource limits, NodePort Service | tested on minikube |
| [nordiktech-monitoring](https://github.com/RexCo24/nordiktech-monitoring) | kube-prometheus-stack via Helm, ServiceMonitor for the Flask `/metrics` endpoint | tested on minikube, Grafana dashboard live |

## Other work

- [azure-vnet-vm-mediterraneanretail](https://github.com/RexCo24/azure-vnet-vm-mediterraneanretail) – Azure IaaS setup with Terraform (VNet, subnet, NSG, public IP, VM), applied in Azure
- [aws-balticgoods-infra-demo](https://github.com/RexCo24/aws-balticgoods-infra-demo) – HA-ready VPC across two availability zones with an Application Load Balancer, Terraform, applied in AWS
- Kubernetes troubleshooting lab – coming next: documented drills for CrashLoopBackOff, ImagePullBackOff, OOMKilled, pending pods, probe failures, label/port mismatches

## Certifications

- Microsoft Azure Fundamentals (AZ-900), August 2026

## Contact

[LinkedIn](https://www.linkedin.com/in/alexander-koch-72276610b/) · GitHub issues or discussions on any of the repos
