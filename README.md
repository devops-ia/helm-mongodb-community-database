# MongoDB Community Database Helm Chart

> [!NOTE]
> This project is not affiliated with [MongoDB](https://github.com/mongodb/helm-charts).

A Helm chart to deploy MongoDB Community databases using the MongoDB Community Operator Custom Resource Definitions (CRDs).

## Features

- MongoDB Community Operator CRD support
- Replica Set configuration
- TLS/SSL encryption support
- SCRAM and X.509 authentication
- Prometheus metrics integration
- Custom MongoDB configuration
- ServiceMonitor for Prometheus Operator
- Flexible storage options
- High availability configurations
- Custom cluster domain support

## Prerequisites

- Kubernetes 1.19+
- Helm 3.0+
- [MongoDB Community Operator](https://github.com/mongodb/mongodb-kubernetes-operator) installed in your cluster

## Installation

### Install MongoDB Community Operator

Before deploying this chart, you need to install the MongoDB Community Operator:

```console
helm repo add mongodb https://mongodb.github.io/helm-charts
helm install community-operator mongodb/community-operator
```

### Chart Repository

#### Add repository

```console
helm repo add mongodb-community-database https://devops-ia.github.io/helm-mongodb-community-database
helm repo update
```

#### Install Helm chart

```console
helm install [RELEASE_NAME] mongodb-community-database/mongodb-community-database
```

This installs all the Kubernetes components associated with the chart and creates the release.

_See [helm install](https://helm.sh/docs/helm/helm_install/) for command documentation._

### OCI Registry

Charts are also available in OCI format. The list of available charts can be found [here](https://github.com/devops-ia/helm-mongodb-community-database/pkgs/container/helm-mongodb-community-database%2Fmongodb-community-database).

#### Install Helm chart

```console
helm install [RELEASE_NAME] oci://ghcr.io/devops-ia/helm-mongodb-community-database/mongodb-community-database --version=[version]
```

## Quick Start

### Basic Deployment

```console
helm install my-mongodb mongodb-community-database/mongodb-community-database \
  --set mongodb.users[0].password=mySecurePassword
```

### With Custom Storage

```console
helm install my-mongodb mongodb-community-database/mongodb-community-database \
  --set mongodb.statefulSet.spec.volumeClaimTemplates[0].spec.storageClassName=fast-ssd \
  --set mongodb.statefulSet.spec.volumeClaimTemplates[0].spec.resources.requests.storage=50Gi
```

### With TLS Enabled

```console
# First, create the required secrets
kubectl create secret generic mongodb-tls-cert --from-file=tls.pem=./mongodb-cert.pem
kubectl create secret generic mongodb-ca-cert --from-file=ca.pem=./ca-cert.pem

# Install with TLS enabled
helm install my-mongodb mongodb-community-database/mongodb-community-database \
  --set mongodb.security.tls.enabled=true \
  --set mongodb.security.tls.certificateKeySecretRef.name=mongodb-tls-cert \
  --set mongodb.security.tls.caCertificateSecretRef.name=mongodb-ca-cert
```

## Examples

The chart includes several example configurations in the [examples](charts/mongodb-community-database/examples/) directory:

- [01-basic-deployment.yaml](charts/mongodb-community-database/examples/01-basic-deployment.yaml) - Simple 3-member replica set
- [02-tls-enabled.yaml](charts/mongodb-community-database/examples/02-tls-enabled.yaml) - Deployment with TLS encryption
- [03-prometheus-monitoring.yaml](charts/mongodb-community-database/examples/03-prometheus-monitoring.yaml) - With Prometheus monitoring
- [04-high-availability.yaml](charts/mongodb-community-database/examples/04-high-availability.yaml) - 5-member HA setup with anti-affinity
- [05-custom-cluster-domain.yaml](charts/mongodb-community-database/examples/05-custom-cluster-domain.yaml) - Custom DNS configuration

## Configuration

See the [values.yaml](charts/mongodb-community-database/values.yaml) file for the full list of configuration options.

### Key Configuration Parameters

| Parameter | Description | Default |
|-----------|-------------|---------|
| `mongodb.members` | Number of replica set members | `3` |
| `mongodb.version` | MongoDB version | `8.0.6-ubi9` |
| `mongodb.type` | Deployment type | `ReplicaSet` |
| `mongodb.clusterDomain` | Custom cluster domain | `""` |
| `mongodb.security.authentication.modes` | Authentication modes | `["SCRAM"]` |
| `mongodb.security.tls.enabled` | Enable TLS | `false` |
| `mongodb.prometheus.enabled` | Enable Prometheus metrics | `false` |
| `serviceMonitor.enabled` | Create ServiceMonitor | `false` |

## Accessing MongoDB

After deployment, MongoDB will be accessible through the service:

```console
# Get connection string from secret
kubectl get secret [RELEASE_NAME]-admin -o jsonpath='{.data.connectionString\.standard}' | base64 -d

# Port forward to access locally
kubectl port-forward service/[RELEASE_NAME]-svc 27017:27017

# Connect with mongosh
mongosh "mongodb://admin:password@localhost:27017/?authSource=admin"
```

## Upgrading

To upgrade the chart:

```console
helm upgrade [RELEASE_NAME] mongodb-community-database/mongodb-community-database
```

## Uninstallation

To uninstall/delete the deployment:

```console
helm uninstall [RELEASE_NAME]
```

## Documentation

- [Chart Documentation](charts/mongodb-community-database)
- [MongoDB Community Operator](https://github.com/mongodb/mongodb-kubernetes-operator)
- [MongoDB Documentation](https://docs.mongodb.com/)

## Contributing

Contributions are welcome! Please read the [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
