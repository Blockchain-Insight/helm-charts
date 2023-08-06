Configuration Options for Full Node Deployment

This Readme file provides an overview of the configuration options available for deploying a full node using the specified values. The deployment is intended for AWS (Amazon Web Services) infrastructure. Below are the configuration options that can be set:

**General Options:**
- provider: The cloud provider where the deployment will take place. In this case, it is set to "aws."
- replicaCount: The number of desired pods for the full node. It is set to 2 in this case.
- imagePullSecrets (required): A list of secrets needed to pull the container image from docker hub.
- nameOverride and fullnameOverride: Optional overrides for the name of the deployment.
- serviceAccount: Configuration for the Kubernetes service account, such as whether to create a new one, annotations, and name.
- podAnnotations: Additional annotations to add to the deployment's pods.
- podSecurityContext and securityContext: Security context options for pods and containers.
- strategyType: The deployment strategy type.
- resources: Resource limits and requests for the pods.
- hostedZone (required): Dns zone to host full node applicaiton.

**Image Options:**
- image.repository (required): The repository URL for the container image.
- image.pullPolicy: The image pull policy, which determines when to pull the image.
- image.tag (required): The specific tag of the container image to use.

**Node Options:**
- env: Environment variables to be set in the full node container. All blockchain specific information is passed as enivormemnt variables.

*Following fields must be set with appropriate values for the blockchain. These values can be found in the documentation sources present for the given blockchain.*
- githubUrl: URL of the GitHub repository for the application.
- chainId: The ID of the blockchain network.
- appVersion: The version of the application.
- cosmovisorVersion: The version of Cosmovisor.
- moniker: The moniker for the node.
- gasFee: The gas fee.
- genesisUrl: URL of the genesis file for the blockchain.
- addressBookUrl: URL of the address book file for the blockchain.
- seedUrl: The seed URL for the node.
- daemonName: The name of the daemon.
- daemonHome: The home directory for the daemon.
- repoHome: The home directory for the repository.
*If pruningOption is set, all the following pruning values must also be given*
* If pruningOption not set, use default values. What are the default values*
- pruningOption: The pruning option for the blockchain data.
- pruningKeepRecent, pruningKeepEvery, and pruningInterval: Pruning values when custom pruning is enabled.
 * If STATE_SYNC is true, only then the following state sync values are required.*
- stateSync: Whether to enable state sync.
- stateSyncRpc: RPC URL for state sync.
- stateSyncPeer: State sync peer URL.
- stateSyncMaxValidHeight: The maximum valid height for state sync.
- apiCorsEnable: Whether to enable CORS for the API.
- apiEnable: Whether to enable the API.
- apiSwaggerEnable: Whether to enable API Swagger documentation.
- importValidator: Must be set to false for full node. keyringBackend, valKey, valMnemonic, valPrivKey are set with empty string.

**Service Options:**
- service.type: The type of Kubernetes service to create for the full node.

**Persistence Options**
- persistence.enabled: Whether to enable persistence for the node.
- persistence.hostPath: The host path for persistence (used when persistence is enabled).

**Node Selector, Tolerations, and Affinity Options:**
- nodeSelector: Node selector options to determine which nodes the pods will be scheduled on.
- tolerations: Tolerations to control the scheduling of pods.
- affinity: Affinity rules for pod scheduling.

Please note that some configuration options have default values that will be used if not explicitly provided.
Ensure to set the appropriate values for the desired deployment and customize the configurations based on your specific requirements.



Deploying full node

```bash
helm install hypersign . -n node
```

