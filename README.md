# NKP GitOps Demo

This repository contains applications designed to demonstrate GitOps workflows on Nutanix Kubernetes Platform (NKP).

By connecting this repository to an NKP Project as a GitOps Source, NKP's embedded FluxCD engine will automatically detect, deploy, and continuously reconcile the application state.

## Prerequisites

- An active NKP Workload Cluster.
- A configured Workspace and Project within the NKP UI.

## Deployment Instructions

1. Fork or Clone this Repository: Ensure the repository is accessible from your NKP management cluster.
2. Add a GitOps Source:
    - Navigate to your target Project in the NKP UI.
    - Go to Project Deployments -> GitOps Sources.
    - Click Add GitOps Source and provide the URL to this repository.
    - Specify the branch (e.g., `main`) and the path (use `./hello-world` for a simple stateless app).
3. Sync and Verify:
    - Once saved, NKP will automatically generate the required Flux `GitRepository` and `Kustomization` resources.
    - Within a few moments, the application will be deployed to the project's namespace.

## Modifying the Demo

Because this is a GitOps-driven deployment, you should not modify resources directly via `kubectl`. Instead:

1. Make a change to `deployment.yaml` (e.g., increase `replicas: 3`).
2. Commit and push the change to your Git repository.
3. Watch as NKP automatically detects the commit and rolls out the changes to the cluster.

