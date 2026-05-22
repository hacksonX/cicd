# Uptime Kuma (Argo CD)

This folder contains Kubernetes manifests to deploy Uptime Kuma and an Argo CD `Application` resource.

Steps:

1. Commit this folder to a Git repository and update `argocd-application.yaml` -> `spec.source.repoURL` to that repo URL.
2. Apply the Argo CD `Application` (or let Argo CD track the repo):

```bash
# If you already have Argo CD installed, apply the Application into the argocd namespace:
kubectl apply -f argocd-application.yaml -n argocd
```

3. Argo CD will sync the manifests from `uptime-kuma/manifests` and create the namespace, PVC, Deployment, and Service.

Access:
- NodePort: http://<node-ip>:30080 (or use an Ingress/LoadBalancer)
