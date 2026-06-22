# Source: https://coursify.hasanraiyan.me/research/getting-started-with-argocd

Getting Started with ArgoCD

# 

Getting Started with ArgoCD

Verified Sources

Jun 15, 2026

## AI Summary

\\142 i have ab we have teh $234 $

ArgoCD is a declarative, GitOps continuous delivery tool for Kubernetes. It automates the deployment of applications by continuously comparing the desired state defined in a Git repository with the actual live state in your Kubernetes cluster, and reconciling any differences — the core premise of GitOps.

### Why ArgoCD?

Traditional CI/CD pipelines push changes to clusters using external tools and credentials. ArgoCD flips this model: it runs **inside** your cluster and **pulls** changes from Git. This approach provides:

- **Git as Single Source of Truth**: Every change is versioned, reviewed, and auditable in Git
- **Easy Rollback**: Revert a Git commit and ArgoCD automatically reverts the cluster state
- **Cluster Disaster Recovery**: Rebuild your entire cluster from the Git repository
- **Better Access Control**: Leverage Git's permission model (CODEOWNERS, branch protection) instead of granting CI systems direct cluster access

### How ArgoCD Works — The Reconciliation Loop

At the heart of ArgoCD is a continuous reconciliation loop that detects and corrects configuration drift:

1. The **Repo Server** clones your Git repository and renders Helm/Kustomize/Jsonnet into raw Kubernetes manifests.
2. The **Application Controller** compares the desired state (from Git) with the live state (from the Kubernetes API).
3. If drift is detected and auto-sync is enabled, ArgoCD applies the changes automatically; otherwise it reports the app as **Out of Sync** .

## Footnotes

1. [Argo CD Official Documentation](https://argo-cd.readthedocs.io) - Overview of ArgoCD, GitOps principles, and benefits of Git as single source of truth. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-1-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-1-4)
 
2. [Argo CD Component Architecture](https://argo-cd.readthedocs.io/en/stable/developer-guide/architecture/components) - Official component architecture documentation detailing dependencies and reconciliation flow. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 

#### ArgoCD Tutorial for Beginners | GitOps CD for Kubernetes

### ArgoCD Architecture: Core Components

An ArgoCD installation consists of several components working together inside the `argocd` namespace [2]():

| Component | Purpose | Key Details |
| --- | --- | --- |
| **argocd-server** (API Server) | Exposes REST/gRPC API, serves the Web UI, handles authentication & RBAC | Port 8080 internal, 443 external |
| **argocd-repo-server** (Repo Server) | Clones Git repos and renders manifests via Helm, Kustomize, or Jsonnet | Resource-intensive; scales independently |
| **argocd-application-controller** | Runs the reconciliation loop; compares desired vs. live state and executes syncs | Watches `Application` and `AppProject` CRs |
| **argocd-applicationset-controller** | Manages `ApplicationSet` resources for templated, multi-app deployment | Enables generator patterns (cluster, git, matrix) |
| **Redis** | In-memory cache reducing requests to Kube API and Git providers | Password-authenticated by default |
| **Dex** | Authentication broker supporting OIDC, SAML, LDAP, GitHub, etc. | Enables SSO integration |

### Custom Resource Definitions (CRDs)

ArgoCD extends the Kubernetes API with three key CRDs:

- **Application**: Defines a deployed application — its source repo, destination cluster/namespace, and sync policy.
- **AppProject**: Groups applications with shared RBAC policies, source repos, and destination clusters.
- **ApplicationSet**: Automates the creation of multiple `Application` resources from generator patterns (cluster, git, list, matrix, etc.) .

### Component Dependency Diagram

## Footnotes

1. [ArgoCD Architecture & Installation - AI Agent Factory](https://agentfactory.panaversity.org/docs/Deploying-Agent-Factories-in-the-Cloud/cicd-gitops-argocd/argocd-architecture-installation) - Comprehensive breakdown of five core components and installation steps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-3-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-3-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-3-4)
 
2. [ArgoCD Architecture Core Components - KodeKloud](https://notes.kodekloud.com/docs/Prep-Course-Certified-Argo-Project-Associate-CAPA/ArgoCD/ArgoCD-Architecture-Core-Components/page) - Component table and architecture details for CAPA certification prep. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2)
 
3. [Argo CD Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started) - Official getting started guide with installation, CLI, access, and first application deployment. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

### 

ArgoCD Development & Evolution Timeline

#### Project Inception

2018

ArgoCD was created by Intuit as an open-source GitOps continuous delivery tool for Kubernetes, adopted into the Argo project family."

#### CNCF Sandbox

2019

ArgoCD was accepted as a CNCF Sandbox project, gaining broader community visibility and adoption."

#### v1.x Stable Releases

2020

Major stable releases introduced core features: ApplicationSets, SSO via Dex, multi-cluster management, and Helm/Kustomize support."

#### Helm Chart & HA

2021

Official Helm chart maturity, high-availability mode with Redis HA, and progressive delivery integration with Argo Rollouts."

#### CNCF Incubating

2023

ArgoCD was promoted to CNCF Incubating status, reflecting production-grade maturity and wide industry adoption."

#### v3.x Release

2024-2025

Major v3 release with improved performance, component-based architecture refinements, and server-side apply by default."

### Installing and Configuring ArgoCD

1. 1
 
 Step 1
 
 Create the ArgoCD Namespace
 
 Create a dedicated namespace to isolate ArgoCD components:
 
 `1kubectl create namespace argocd`
 
 This keeps all ArgoCD services and application resources separated from your workloads.
 
2. 2
 
 Step 2
 
 Install ArgoCD Using Manifests
 
 Apply the official installation manifests. The `--server-side --force-conflicts` flags are required due to CRD size limitations :
 
 `1kubectl apply -n argocd \ 2  --server-side --force-conflicts \ 3  -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`
 
 For production, pin to a specific version (e.g., `v3.2.0`) rather than using `stable` .
 
 ## Footnotes
 
 1. [Argo CD Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started) - Official getting started guide with installation, CLI, access, and first application deployment. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2)
 
 
3. 3
 
 Step 3
 
 Install the ArgoCD CLI
 
 Download the CLI for your platform. On macOS/Linux:
 
 `1# macOS 2brew install argocd 3 4# Linux (amd64) 5curl -sSL -o /usr/local/bin/argocd \ 6  https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64 7sudo chmod +x /usr/local/bin/argocd`
 
 The CLI enables scripting, automation, and headless operations.
 
4. 4
 
 Step 4
 
 Access the ArgoCD API Server
 
 By default the API server is not externally exposed. Use port-forwarding for local access:
 
 `1kubectl port-forward svc/argocd-server -n argocd 8080:443`
 
 Alternatively, change the Service type to `LoadBalancer` or configure an Ingress for production .
 
 ## Footnotes
 
 1. [Argo CD Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started) - Official getting started guide with installation, CLI, access, and first application deployment. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
5. 5
 
 Step 5
 
 Retrieve the Admin Password
 
 The initial admin password is auto-generated and stored in a Kubernetes Secret:
 
 `1kubectl -n argocd get secret argocd-initial-admin-secret \ 2  -o jsonpath="{.data.password}" | base64 -d`
 
 Log in and **change the password immediately** :
 
 `1argocd login localhost:8080 2argocd account update-password`
 
 ## Footnotes
 
 1. [Argo CD Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started) - Official getting started guide with installation, CLI, access, and first application deployment. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
6. 6
 
 Step 6
 
 Register an External Cluster (Optional)
 
 ArgoCD can deploy to its own cluster by default. To add an external cluster target :
 
 `1argocd cluster add <CONTEXT_NAME>`
 
 This creates the necessary ServiceAccount and RBAC bindings in the target cluster.
 
 ## Footnotes
 
 1. [GitOps Tutorial: Getting Started With GitOps & Argo CD - Octopus Deploy](https://octopus.com/devops/gitops/gitops-tutorial) - Step-by-step GitOps tutorial covering cluster registration and application creation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6)
 
 
7. 7
 
 Step 7
 
 Create Your First Application
 
 Use the CLI to deploy a sample guestbook application :
 
 `1argocd app create guestbook \ 2  --repo https://github.com/argoproj/argocd-example-apps.git \ 3  --path guestbook \ 4  --dest-server https://kubernetes.default.svc \ 5  --dest-namespace default`
 
 Or create it graphically via the **\+ New App** button in the Web UI.
 
 ## Footnotes
 
 1. [Argo CD Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started) - Official getting started guide with installation, CLI, access, and first application deployment. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 

### Alternative Installation: Helm Chart

For production deployments, the Helm chart offers more flexibility and configuration options :

`1# Add the ArgoCD Helm repository 2helm repo add argo https://argoproj.github.io/argo-helm 3helm repo update 4 5# Install with default values 6helm install argocd argo/argo-cd -n argocd --create-namespace 7 8# Or with custom values for production 9helm install argocd argo/argo-cd -n argocd \ 10  -f argocd-custom-values.yaml`

A typical `argocd-custom-values.yaml` for production might include:

`1server: 2  replicas: 2 3  ingress: 4    enabled: true 5    annotations: 6      cert-manager.io/cluster-issuer: letsencrypt-prod 7 8controller: 9  replicas: 1 10  resources: 11    requests: 12      cpu: 500m 13      memory: 512Mi 14 15redis: 16  ha: 17    enabled: true  # Enable Redis HA for production`

## Footnotes

1. [GitOps with Argo CD: Comprehensive Installation Guide - Medium](https://medium.com/@manikandan_t/gitops-with-argo-cd-a-comprehensive-installation-guide-for-default-custom-paths-and-771797808bb9) - Detailed guide covering default, custom path, and namespace-scoped RBAC installations. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 

Declarative (YAML)

Imperative (CLI)Web UI

`1apiVersion: argoproj.io/v1alpha1 2kind: Application 3metadata: 4  name: guestbook 5  namespace: argocd 6spec: 7  project: default 8  source: 9    repoURL: https://github.com/argoproj/argocd-example-apps.git 10    targetRevision: HEAD 11    path: guestbook 12  destination: 13    server: https://kubernetes.default.svc 14    namespace: default 15  syncPolicy: 16    automated: 17      prune: true 18      selfHeal: true 19    syncOptions: 20      - CreateNamespace=true`

### Understanding Sync Policies

The sync policy controls how and when ArgoCD synchronizes your application state :

| Policy | Behavior | When to Use |
| --- | --- | --- |
| **Manual** | Sync triggered only by operator action | Production, high-risk changes, compliance environments |
| **Auto Sync** | Automatically applies Git changes to the cluster on detection | Dev/staging environments, low-risk deployments |
| **Self-Heal** | Automatically corrects configuration drift when manual cluster changes are detected | Enforce immutability, prevent manual overrides |
| **Auto-Prune** | Removes cluster resources that are no longer defined in Git | Clean decommissioning of removed resources |

**Key Sync Options** :

- `CreateNamespace=true` — Auto-create the destination namespace
- `PrunePropagationPolicy=foreground` — Control how pruned resources are deleted
- `PruneLast=true` — Prune resources after new ones are healthy
- `ApplyOutOfSyncOnly=true` — During auto-sync, only apply resources that differ (saves API server load)
- `Validate=false` — Skip server-side validation

### Retry Configuration

Failed syncs can be automatically retried:

`1syncPolicy: 2  automated: 3    prune: true 4    selfHeal: true 5  retry: 6    limit: 5 7    backoff: 8      duration: 5s    # Initial wait 9      factor: 2        # Exponential multiplier 10      maxDuration: 3m  # Maximum wait between retries`

This implements exponential backoff: 5s,10s,20s,40s,80s→3m5\\text{s}, 10\\text{s}, 20\\text{s}, 40\\text{s}, 80\\text{s} \\rightarrow 3\\text{m}5s,10s,20s,40s,80s→3m cap .

## Footnotes

1. [ArgoCD Sync Policies: A Practical Guide - Octopus Deploy](https://octopus.com/devops/argo-cd/argo-cd-sync-policies) - In-depth guide to manual, automated, self-heal, selective sync, and resource protection options. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-8) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-8-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-8-3)
 

### 

ArgoCD Sync Policy Comparison

Feature availability across sync policy types

#### Boolean Flags — A Common Pitfall

When creating applications via the CLI, sync policy flags like `--auto-prune` and `--self-heal` are **boolean flags**. Including them in the command sets them to `true`, even without an explicit value. Many beginners accidentally enable auto-prune or self-heal by adding these flags without understanding their impact. Self-heal will **override any manual cluster changes** and auto-prune will **delete resources removed from Git** — always double-check your intent.

more...

#### Use the App of Apps Pattern

For managing multiple applications, adopt the **App of Apps** pattern: create a single ArgoCD `Application` resource whose source directory contains other `Application` manifests. ArgoCD will automatically deploy and manage all child applications. This gives you a single Git repository to control your entire deployment fleet, and changes to any child Application manifest are automatically detected and applied .

## Footnotes

1. [Best Practices ArgoCD: K8s Deployment Strategy - Medium](https://medium.com/@dikshantmali.dev/best-practices-argocd-k8s-deployment-strategy-with-argocd-5b8226052718) - Community best practices covering App of Apps, ApplicationSet, sync policies, and retry configuration. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-9)
 

more...

### Common Questions & Edge Cases

What is the difference between ArgoCD and traditional CI/CD pipelines?

Can ArgoCD deploy to multiple clusters?

How does ArgoCD handle Helm charts and Kustomize overlays?

What happens if I make a manual change directly in the cluster?

Should I use automated sync in production?

### Deploying Your First Application — End-to-End Walkthrough

1. 1
 
 Step 1
 
 Verify ArgoCD Installation
 
 Confirm all pods are running before proceeding:
 
 `1kubectl get pods -n argocd`
 
 You should see pods for `argocd-server`, `argocd-repo-server`, `argocd-application-controller`, `redis`, and `dex` in `Running` status.
 
2. 2
 
 Step 2
 
 Log In via CLI
 
 `1# Port-forward the API server (in a separate terminal) 2kubectl port-forward svc/argocd-server -n argocd 8080:443 3 4# Retrieve the initial admin password 5kubectl -n argocd get secret argocd-initial-admin-secret \ 6  -o jsonpath="{.data.password}" | base64 -d 7 8# Log in 9argocd login localhost:8080`
 
3. 3
 
 Step 3
 
 Create the Application
 
 `1argocd app create guestbook \ 2  --repo https://github.com/argoproj/argocd-example-apps.git \ 3  --path guestbook \ 4  --dest-server https://kubernetes.default.svc \ 5  --dest-namespace default`
 
4. 4
 
 Step 4
 
 Sync the Application
 
 Since the default sync policy is Manual, trigger the initial deployment:
 
 `1argocd app sync guestbook`
 
 Or click **Sync** in the Web UI. ArgoCD will apply all manifests from the `guestbook` path to the cluster.
 
5. 5
 
 Step 5
 
 Verify the Deployment
 
 `1# Check application status 2argocd app get guestbook 3 4# The app should show as Healthy and Synced 5# Verify resources in the cluster 6kubectl get deployments,services -n default`
 
6. 6
 
 Step 6
 
 Observe Drift Detection
 
 To see ArgoCD's drift detection in action, manually scale the deployment:
 
 `1kubectl scale deployment guestbook-ui --replicas=5 -n default`
 
 Then check the app status — ArgoCD will report **Out of Sync** because the live replicas count (5) doesn't match the desired state in Git. If self-heal were enabled, it would automatically revert to the Git-defined replica count.
 

### Best Practices Summary

Drawing from community experience and official guidance [3]():

1. **Use Declarative Application Manifests** — Store `Application` CRDs in Git, not just create them via CLI. This makes your ArgoCD configuration itself GitOps-managed.
2. **Adopt the App of Apps or ApplicationSet Pattern** — Manage fleet deployments declaratively rather than creating individual applications manually.
3. **Pin ArgoCD Versions** — Avoid using the `stable` tag in production; pin to a specific version to prevent unexpected upgrades .
4. **Separate App Repos from Source Code** — ArgoCD should point to a **configuration repository** (manifests, Helm values), not your source code repo. CI pipelines build images and update the config repo; ArgoCD deploys from the config repo .
5. **Enable RBAC via AppProjects** — Use `AppProject` CRDs to restrict which repos, clusters, and namespaces teams can deploy to.
6. **Protect Critical Resources** — Use the annotation `argocd.argoproj.io/sync-options: Delete=false` to prevent accidental deletion of resources like PersistentVolumeClaims .
7. **Monitor ArgoCD Metrics** — Expose Prometheus metrics and set up alerts for failed syncs, out-of-sync apps, and controller health.

## Footnotes

1. [Best Practices ArgoCD: K8s Deployment Strategy - Medium](https://medium.com/@dikshantmali.dev/best-practices-argocd-k8s-deployment-strategy-with-argocd-5b8226052718) - Community best practices covering App of Apps, ApplicationSet, sync policies, and retry configuration. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-9)
 
2. [Argo CD Best Practices - Octopus Deploy](https://octopus.com/blog/argo-cd-best-practices) - Production best practices including separation of source code and config repos, and audit trail maintenance. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-10) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-10-2)
 
3. [Best practices for syncPolicy for CI/CD - GitHub Discussion](https://github.com/argoproj/argo-cd/discussions/6114) - Community discussion on automated vs. manual sync tradeoffs in CI/CD pipelines. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-11)
 
4. [Argo CD Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started) - Official getting started guide with installation, CLI, access, and first application deployment. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
5. [ArgoCD Sync Policies: A Practical Guide - Octopus Deploy](https://octopus.com/devops/argo-cd/argo-cd-sync-policies) - In-depth guide to manual, automated, self-heal, selective sync, and resource protection options. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-8)
 

### Knowledge Check

Question 1 of 5

Q1Single choice

What is the primary difference between traditional CI/CD pipelines and ArgoCD?

ArgoCD requires Jenkins to function

ArgoCD pushes changes to clusters using external credentials

ArgoCD runs inside the cluster and pulls changes from Git

ArgoCD replaces all CI tools including build steps

BackNext

## Explore Related Topics

[1\\ \\ Learn AI in 90 Days: A Complete Roadmap\\ \\ Artificial Intelligence is no longer a niche specialty—it is the defining technology of the decade. From healthcare diagnostics to autonomous vehicles, from financial fraud detection to generative content creation, AI is reshaping every industry. For professionals and students alike, acquiring AI co](https://coursify.hasanraiyan.me/research/learn-ai-in-90-days-a-complete-roadmap) [2\\ \\ Master Class: Kubernetes Fundamentals\\ \\ Kubernetes is the industry‑standard platform for orchestrating containerized microservices, separating cluster management (Control Plane) from workload execution (Worker Nodes) and emphasizing declarative, version‑controlled deployments.\\ \\ - The Control Plane (kube‑apiserver, etcd, scheduler, controller‑manager) stores the cluster’s desired state and makes global scheduling decisions. - Worker nodes run kubelet, kube‑proxy, and a container runtime to host Pods and enforce networking rules. - Core Kubernetes objects—Pods, Services, and Deployments—enable self‑healing, stable networking, and scalable rollouts. - Declarative YAML manifests (`kubectl apply`) support IaC and GitOps, while imperative commands are discouraged. - Production workloads should use higher‑level abstractions (Deployments/StatefulSets) instead of bare Pods to ensure resilience.](https://coursify.hasanraiyan.me/research/master-class-kubernetes-fundamentals) [3\\ \\ How to Become a DevOps Engineer\\ \\ The course maps a comprehensive DevOps Engineer career path, emphasizing foundational systems knowledge, layered skill development, and a results‑focused portfolio.\\ \\ - Start with Linux, Git, networking, and scripting before moving to containers. - Learn CI/CD pipelines, IaC (Terraform), cloud basics, then Docker and Kubernetes. - Apply DORA metrics – deployment frequencydeployment\\ frequencydeployment frequency, lead timelead\\ timelead time, change failure ratechange\\ failure\\ ratechange failure rate, time to restoretime\\ to\\ restoretime to restore – to gauge performance. - Build a public portfolio showing automated pipelines, IaC, container deployment, monitoring, and runbooks. - Use a 6‑month plan and the weekly formula Weekly Progress\=Theory+Labs+Documentation+Reflection\\text{Weekly Progress}= \\text{Theory}+ \\text{Labs}+ \\text{Documentation}+ \\text{Reflection}Weekly Progress\=Theory+Labs+Documentation+Reflection.](https://coursify.hasanraiyan.me/research/how-to-become-a-devops-engineer)

[![Coursify logo](https://coursify.hasanraiyan.me/_next/image?url=%2Fimages%2Fapps%2Fcoursify.png&w=48&q=75)Browse all research articles](https://coursify.hasanraiyan.me/research)