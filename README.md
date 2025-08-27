# OpenCTI Helm Chart

A Helm chart to deploy CR MongoDB Community database

## Usage

Charts are available in:

* [Chart Repository](https://helm.sh/docs/topics/chart_repository/)
* [OCI Artifacts](https://helm.sh/docs/topics/registries/)

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

This install all the Kubernetes components associated with the chart and creates the release.

_See [helm install](https://helm.sh/docs/helm/helm_install/) for command documentation._

### OCI Registry

Charts are also available in OCI format. The list of available charts can be found [here](https://github.com/devops-ia/helm-mongodb-community-database/pkgs/container/helm-mongodb-community-database%2Fmongodb-community-database).

#### Install Helm chart

```console
helm install [RELEASE_NAME] oci://ghcr.io/devops-ia/helm-mongodb-community-database/mongodb-community-database --version=[version]
```

## OpenCTI chart

Can be found in [mongodb-community-database chart](https://github.com/devops-ia/helm-mongodb-community-database/tree/main/charts/mongodb-community-database).
