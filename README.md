# Labelstudio: Kubernetes Cluster

## Reproduction steps

Use either via pip (local, SQLite DB):

- `pip install label-studio`
- `label-studio start`

Or a kubernetes cluster a proper setup (PostgreSQL). For local testing of the cluster minikube is an possible solution:

- Install minikube (see https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download)
- Start the local node: `minkube start`

The easiest way to setup labelstudio is via helm:

- Install helm (see https://helm.sh/docs/intro/install/)
- Add the repository to the helm chart & install:
  - `helm repo add heartex https://charts.heartex.com/`
  - `helm repo update heartex`
  - Create resource config for labelstudio (see ls-values.yaml)
  - `helm install <RELEASE_NAME> heartex/label-studio -f ls-values.yaml` (choose your own RELEASE_NAME)
  - Portforwarding to access UI: `kubectl port-forward service/<RELEASE_NAME>-ls-app 8080:80`
  - Access on http://localhost:8080/
