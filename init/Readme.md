Prepare the eks cluster
```bash
git clone git@github.com:Blockchain-Insight/helm-charts.git
```

```bash
cd helm-charts/init
```

```bash
kubectl apply -f namespaces.yaml
```

```bash
helm repo add external-secrets https://charts.external-secrets.io
helm install external-secrets external-secrets/external-secrets -n addons
```

```bash
kubectl apply -f cluster_secret_store.yaml
```

```bash
kubectl apply -f external_secrets.yaml
```

```bash
helm install ingress oci://ghcr.io/nginxinc/charts/nginx-ingress -n ingress
```