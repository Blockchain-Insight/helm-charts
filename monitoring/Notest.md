hid1e8gele4kgu45ser7xgkrjrjfacfukczy8uaprf
hidvaloper1e8gele4kgu45ser7xgkrjrjfacfukczyc72ttk

Prepare Monitoring 
2 inputes are required from the deployed validator 
# vim .hid-node/config/config.toml

# hid-noded keys list --keyring-backend=test
- name: node1
  type: local
  address: hid1zcu3lgxujgawdc4zaw82y6eqqvm2a2kk0za97g
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"AqkO8Y5UbZzfyFRI1E7Q842Qx+D+/K9tEbDOz1g/OyHq"}'
  mnemonic: ""

# echo "Validator Address: "
Validator Address:
# hid-noded keys show node1 --bech val -a --keyring-backend=test
hidvaloper1zcu3lgxujgawdc4zaw82y6eqqvm2a2kksq20kh
# echo "Private Block Signer Key:"
Private Block Signer Key:
# cat $HOME/.hid-node/config/priv_validator_key.json
# cat $HOME/.hid-node/config/priv_validator_key.json
{
  "address": "F8C4154126BAEA6929A6F9EAB1E2FBC5E3691FE4",
  "pub_key": {
    "type": "tendermint/PubKeyEd25519",
    "value": "Jv61227araBPvhw2zJQRJIZS6Dbjc/pa9KFftG/SXMk="
  },
  "priv_key": {
    "type": "tendermint/PrivKeyEd25519",
    "value": "SJgjWoCK/A1YUPRyCL2I7oCXZZoEFKvHhL2PrK2EQbUm/rXbbtqtoE++HDbMlBEkhlLoNuNz+lr0oV+0b9JcyQ=="
  }




Deploy Monitoring 
https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/kube-prometheus-stack -n monitoring -f values.yaml 
helm show values prometheus-community/kube-prometheus-stack

apply global manager configuration 
helm upgrade prometheus prometheus-community/kube-prometheus-stack -n monitoring -f values.yaml

Monitoring cosmos sdk chain 
https://speakerdeck.com/ricotoothless/how-to-monitor-cosmos-validator-by-prometheus

# Access grafana 
akaur@XIN719367 Thesis % kubectl port-forward svc/prom-grafana 3000:80 -n monitoring
http://localhost:3000
username: admin 
password: prom-operator

# Access alertmanager
kubectl port-forward svc/prom-kube-prometheus-stack-alertmanager 4000:9093 -n monitoring
http://localhost:4000

# Cosmos exporter 
http://localhost:9300/metrics/general
http://localhost:9300/metrics/params
http://localhost:9300/metrics/validators
http://localhost:9300/metrics/validator
http://localhost:9300/metrics/wallet
