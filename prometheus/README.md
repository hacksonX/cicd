# Prometheus (Argo CD)

This folder contains Kubernetes manifests to deploy Prometheus and an Argo CD `Application` resource.

## Steps:

1. Commit this folder to a Git repository and update `argocd-application.yaml` -> `spec.source.repoURL` to that repo URL.
2. Apply the Argo CD `Application`:

```bash
kubectl apply -f argocd-application.yaml -n argocd
```

3. Argo CD will sync the manifests from `prometheus/manifests` and create the namespace, ConfigMap, PVC, ServiceAccount, Deployment, and Service.

## Access:

- Prometheus NodePort: `http://localhost:30090` (or use port-forward: `kubectl port-forward -n prometheus svc/prometheus 9090:9090`)
- Prometheus API: `http://localhost:30090/api/v1/query`

## Default Configuration:

Prometheus is configured to scrape:
- Prometheus itself
- Kubernetes API servers
- Kubernetes nodes
- Any pod with `prometheus.io/scrape: 'true'` annotation
