Deployment ingress controller 
https://github.com/nginxinc/kubernetes-ingress/tree/main/deployments/helm-chart
$ helm install ingress oci://ghcr.io/nginxinc/charts/nginx-ingress

Crete route53 enteries
- api.hypersign.node.blockchaininsight.org	A	Simple	-	Yes	dualstack.a5e7c7bb07b984b24856e303b77a04c1-1859217857.eu-central-1.elb.amazonaws.com.
grpc.hypersign.node.blockchaininsight.org	A	Simple	-	Yes	dualstack.a5e7c7bb07b984b24856e303b77a04c1-1859217857.eu-central-1.elb.amazonaws.com.
rpc.hypersign.node.blockchaininsight.org



https://hooks.slack.com/services/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

https://github.com/external-secrets/external-secrets/tree/main/deploy/charts/external-secrets
External secret management for Kubernetes
helm repo add external-secrets https://charts.external-secrets.io
helm install external-secrets external-secrets/external-secrets

monitong slack docker
addons external secret pod
ingress ingresspod
node
validator
