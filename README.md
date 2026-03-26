# Argonaut Helm Chart

# argonaut-helm-chart  

Integrations::
git, gh needs email, name, github token (OPTIONAL)
SLACK AS I/O for the model (OPTIONAL)
webhook for posting the messages 
OPENAI the model
files/elasticsearch (OPTIONAL) for conversation storage
argocd via serviceaccount or via creds
kubectl (OPTIONAL) needs kubeconfigs for the clusters

1. clone repo  
2. create secrets (see values.yaml)  
    openAI secret (MANDATORY)  
    git secret (OPTIONAL)  
    elasticsearch secret (OPTIONAL)  
    argocd secret (OPTIONAL)  
    slack secret  (OPTIONAL)  
    kubeconfig secret (OPTIONAL)  
    put the secret names in values.yaml and make any additional changes 
3. helm install  


---
## Overview

- **Chart Name:** argonaut
- **Type:** Application
- **Description:** A Helm chart for Kubernetes to deploy Argonaut, a Slack bot and automation tool.
- **Version:** 0.1.0

## Files

- `Chart.yaml`: Chart metadata.
- `values.yaml`: Default configuration values.
- `minimum-values.yaml.yaml`: Minimal configuration example.
- `templates/`: Kubernetes manifest templates.

## Installation

First, ensure you have [Helm](https://helm.sh/) installed.

```sh
helm install argonaut . -f values.yaml
```

To use minimal configuration:

```sh
helm install argonaut . -f minimum-values.yaml
```

## Configuration

You can customize the deployment by editing `values.yaml` or providing your own values file. Key configuration options include:

- **LOG_LEVEL**: Logging level (default: INFO)
- **GIT**: Git integration settings
- **AUTO_RUN**: Enable automatic command execution
- **STORAGE_BACKENDS**: Choose between `file_storage` or `elasticsearch`
- **openAI**: OpenAI API integration settings
- **argocd**: ArgoCD integration settings
- **kubernetes**: Kubernetes API access settings
- **serviceAccount**: Service account creation and usage
- **ingress**: Ingress resource configuration

For a full list of options, see [`values.yaml`](values.yaml).

## Templates

The chart includes templates for:

- StatefulSet
- Service
- Ingress
- ServiceAccount
- ClusterRole and ClusterRoleBinding
- External ConfigMap

## Example

To deploy with Slack and Elasticsearch integration, update the relevant sections in `values.yaml` and provide the necessary Kubernetes secrets.

## Development

To package the chart:

```sh
helm package .
```

To lint the chart:

```sh
helm lint .
```

## License

MIT

---

For more details, see the individual files:

- [values.yaml](values.yaml)
- [minimum-values.yaml.yaml](minimum-values.yaml.yaml)
- [templates/](templates/)
