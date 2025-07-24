# k3s-infra

This repository holds Argo CD’s configuration for our k3s cluster.

## Adding a new app

1. In `clusters/main/apps/app-of-apps.yaml`, under `generators.list.elements`, add:

   ```yaml
   - name: your-app
     chart: your-chart-directory
     repoURL: https://github.com/frallan97/your-app-repo
     targetRevision: main
   ```

   Commit & push. Argo CD will auto-detect and deploy into the your-app namespace.

## Bootstrapping

- Install Argo CD (done).
- Create this repo on GitHub (`frallan97/k3s-infra`) and push.
- In Argo CD UI, create a top-level Application pointing at this repo:

    - Name: infra
    - Repo URL: https://github.com/frallan97/k3s-infra
    - Path: clusters/main/apps
    - Cluster: in-cluster
    - Namespace: argocd
    - Sync Policy: Auto 