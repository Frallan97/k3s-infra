# Adding a new app

To add a new app, edit `app-of-apps.yaml` and append a new entry under `generators.list.elements`:

```yaml
- name: your-app
  chart: your-chart-directory
  repoURL: https://github.com/frallan97/your-app-repo
  targetRevision: main
```

Commit and push. Argo CD will auto-detect and deploy into the `your-app` namespace. 