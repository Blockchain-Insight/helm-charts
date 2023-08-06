# Deploying Cosmos-exporter for full-node
This Readme.md file provides an overview of the configuration options available for deploying the Cosmos Exporter using the specified values in *values.yaml*. The deployment is intended for AWS (Amazon Web Services) infrastructure. Below are the configuration options that can be set:

**General Options:**
- provider: The cloud provider where the deployment will take place. In this case, it is set to "aws."
- replicaCount: The number of replicas for the Cosmos Exporter. It is set to 1 in this case.
- strategyType: The deployment strategy type. It is set to "RollingUpdate" for a rolling update strategy.
- imagePullSecrets (required): A list of secrets needed to pull the container image from the container registry.
- nameOverride and fullnameOverride: Optional overrides for the name of the deployment.
- podAnnotations: Additional annotations to add to the deployment's pods.
- podSecurityContext and securityContext: Security context options for pods and containers.

**Node Options:**
- env: Environment variables to be set in the Cosmos Exporter container.
  
*Following fields must be set with appropriate values for the blockchain that is deployed earlier using the full-node helm chart*

- bondDenom (required): Denominated token name. You can find it in genesis file.
- benchPrefix (required): Prefix for chain addresses. You can find it in public addresses.

**Image Options:**
- image.repository (required): The repository URL for the container image.
- image.pullPolicy: The image pull policy, which determines when to pull the image.
- image.tag (required): The specific tag of the container image to use.

**Full Node Application Options:**
- fullNodeAppName (required): The name of the helm release used to deploy full-node application (in this case, "hypersign").

**Service Options:**
- service.type: The type of Kubernetes service to create for the Cosmos Exporter.

**Node Selector, Tolerations, and Affinity Options:**
- nodeSelector: Node selector options to determine which nodes the pods will be scheduled on.
- tolerations: Tolerations to control the scheduling of pods.
- affinity: Affinity rules for pod scheduling.

Please note that some configuration options might have default values that will be used if not explicitly provided.

Ensure to set the appropriate values for the desired deployment and customize the configurations based on your specific requirements.

Once configurations are set, deploy cosmos-exporter

```bash
helm install <name> . -n node
```
