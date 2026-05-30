# ECS to Kubernetes

An interactive, single-page guide for engineers moving from AWS ECS to the Kubernetes ecosystem.

The guide is designed for engineers who already understand containers, AWS, ECS services, task definitions, load balancers, IAM roles, and CloudWatch, but want to build a practical mental model for Kubernetes and the wider cloud-native toolchain.

## Contents

The site walks through Kubernetes from familiar ECS concepts into production-grade platform patterns:

1. **Mental Model Shift**
   - How ECS and Kubernetes are similar
   - Why Kubernetes exposes more of the orchestration stack
   - Desired state, reconciliation loops, controllers, and APIs

2. **ECS → Kubernetes Mapping**
   - ECS Cluster → Kubernetes Cluster
   - EC2 Instance → Node
   - Task Definition → Pod spec
   - ECS Service → Deployment + Service
   - ALB / Target Group → Service + Ingress
   - Parameter Store / Secrets Manager → ConfigMap + Secret / External Secrets
   - CloudWatch Logs → `kubectl logs` + log aggregation

3. **Core Primitives**
   - Nodes
   - Pods
   - Namespaces
   - Labels, selectors, and annotations
   - Resource APIs and manifests

4. **Workloads**
   - Deployments
   - ReplicaSets
   - StatefulSets
   - DaemonSets
   - Jobs and CronJobs
   - Rolling updates and workload lifecycle patterns

5. **Networking**
   - Cluster networking model
   - Services
   - DNS and CoreDNS
   - Ingress
   - Load balancers
   - Network policies
   - Service discovery differences from ECS

6. **Storage**
   - Volumes
   - PersistentVolumes
   - PersistentVolumeClaims
   - StorageClasses
   - Stateful workload considerations

7. **Config and Secrets**
   - ConfigMaps
   - Kubernetes Secrets
   - Environment variables vs mounted files
   - External Secrets patterns for AWS-backed secret stores

8. **kubectl**
   - Common inspection and troubleshooting commands
   - Logs, exec, describe, apply, diff, rollout, and context usage
   - How to think about `kubectl` compared with the AWS ECS CLI

9. **Helm**
   - Charts
   - Values files
   - Releases
   - Templating
   - When Helm helps and when plain manifests are enough

10. **Terraform and Infrastructure**
    - Cluster provisioning
    - Separating infrastructure from application manifests
    - Terraform, providers, Helm releases, and Kubernetes resources

11. **Operators and CRDs**
    - Custom Resource Definitions
    - Controllers
    - Operators as domain-specific automation
    - How Kubernetes can be extended beyond built-in resources

12. **Development and Build Tools**
    - Local development workflows
    - Image building
    - Inner-loop tooling
    - Kubernetes-focused developer experience tools

13. **Advanced Concepts**
    - Autoscaling
    - Scheduling controls
    - Service mesh
    - GitOps
    - Security and policy
    - Multi-cluster patterns

14. **Ecosystem Map**
    - Cluster provisioning
    - Infrastructure as code
    - Package management
    - GitOps
    - Networking
    - Service mesh
    - Security
    - Observability
    - Local development
    - Autoscaling
    - Multi-cluster tooling

15. **Knowledge Check**
    - Interactive quiz for reinforcing key concepts
    - Immediate feedback and explanations
    - Score summary at the end

## Project structure

```text
.
├── index.html
├── README.md
└── .github/
    └── workflows/
        └── pages.yml
```

## View locally

Because this is a static HTML site, no build step is required.

Open `index.html` directly in a browser, or serve the directory locally:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## Deployment

This repo is configured for GitHub Pages using GitHub Actions.

The workflow in `.github/workflows/pages.yml` deploys the repository root whenever changes are pushed to `main`.

### First-time GitHub Pages setup

In the GitHub repository:

1. Open **Settings**.
2. Go to **Pages**.
3. Set **Build and deployment** source to **GitHub Actions**.
4. Push to `main`.
5. Wait for the Pages workflow to complete.

After the workflow succeeds, GitHub will show the published site URL in the Pages settings and in the workflow deployment summary.

## Development notes

- The guide is intentionally implemented as a single `index.html` file.
- CSS and JavaScript are embedded to keep the site portable and easy to publish.
- The page is responsive and should work on desktop, tablet, and mobile screens.
- No package manager, bundler, framework, or static site generator is required.
- External fonts are loaded from Google Fonts.

## Updating content

Most edits can be made directly in `index.html`:

- Navigation buttons are defined near the top of the `<body>`.
- Guide sections are separate `<div class="section">` blocks.
- Expandable deep dives use `.depth-toggle` blocks.
- Code examples use `<pre>` blocks.
- Quiz data and scoring logic are defined in the script section near the bottom of the file.

When adding a new section:

1. Add a navigation button with `onclick="showSection('section-id')"`.
2. Add a matching `<div id="section-id" class="section">` block.
3. Keep the section hidden by default; the existing JavaScript handles switching sections.

## Audience

This guide is best suited for:

- Backend engineers moving services from ECS to Kubernetes
- Platform engineers onboarding application teams to Kubernetes
- DevOps engineers comparing AWS-native orchestration with Kubernetes
- Engineers preparing for Kubernetes-heavy infrastructure work
- Teams building shared vocabulary before an ECS-to-K8s migration

## License

No license has been specified yet.
