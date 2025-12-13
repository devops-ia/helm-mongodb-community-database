# mongodb-community-database

A Helm chart to deploy CR MongoDB Community database

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| ialejandro | <hello@ialejandro.rocks> | <https://ialejandro.rocks> |

## Prerequisites

* Helm 3+

## Add repository

```console
helm repo add mongodb-community-database https://devops-ia.github.io/helm-mongodb-community-database
helm repo update
```

## Install Helm chart (repository mode)

```console
helm install [RELEASE_NAME] mongodb-community-database/mongodb-community-database
```

This install all the Kubernetes components associated with the chart and creates the release.

_See [helm install](https://helm.sh/docs/helm/helm_install/) for command documentation._

## Install Helm chart (OCI mode)

Charts are also available in OCI format. The list of available charts can be found [here](https://github.com/devops-ia/helm-mongodb-community-database/pkgs/container/helm-mongodb-community-database%2Fmongodb-community-database).

```console
helm install [RELEASE_NAME] oci://ghcr.io/devops-ia/helm-mongodb-community-database/mongodb-community-database --version=[version]
```

## Uninstall Helm chart

```console
helm uninstall [RELEASE_NAME]
```

This removes all the Kubernetes components associated with the chart and deletes the release.

_See [helm uninstall](https://helm.sh/docs/helm/helm_uninstall/) for command documentation._

## Basic installation and examples

See [basic installation](docs/configuration.md) and [examples](docs/examples.md).

## Configuration

See [Customizing the chart before installing](https://helm.sh/docs/intro/using_helm/#customizing-the-chart-before-installing). To see all configurable options with comments:

```console
helm show values mongodb-community-database/mongodb-community-database
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| fullnameOverride | string | `""` | Override the full name of the chart |
| mongodb.additionalConnectionStringConfig | object | `{}` | Additional connection string configuration |
| mongodb.additionalMongodConfig | object | `{}` | Additional mongod configuration |
| mongodb.agent.auditLogRotate.includeAuditLogsWithMongoDBLogs | bool | `false` | Include audit logs with MongoDB logs |
| mongodb.agent.auditLogRotate.numTotal | int | `10` | Total number of audit log files to keep |
| mongodb.agent.auditLogRotate.numUncompressed | int | `5` | Number of uncompressed audit log files to keep |
| mongodb.agent.auditLogRotate.percentOfDiskspace | string | `"2.0"` | Percent of disk space for audit logs |
| mongodb.agent.auditLogRotate.sizeThresholdMB | string | `"1000"` | Audit log rotation size threshold (MB) |
| mongodb.agent.auditLogRotate.timeThresholdHrs | int | `24` | Audit log rotation time threshold (hours) |
| mongodb.agent.logFile | string | `""` | Log file path for automation agent |
| mongodb.agent.logLevel | string | `"INFO"` | Log level for automation agent |
| mongodb.agent.logRotate.includeAuditLogsWithMongoDBLogs | bool | `false` | Include audit logs with MongoDB logs |
| mongodb.agent.logRotate.numTotal | int | `10` | Total number of log files to keep |
| mongodb.agent.logRotate.numUncompressed | int | `5` | Number of uncompressed log files to keep |
| mongodb.agent.logRotate.percentOfDiskspace | string | `"2.0"` | Percent of disk space for logs |
| mongodb.agent.logRotate.sizeThresholdMB | string | `"1000"` | Log rotation size threshold (MB) |
| mongodb.agent.logRotate.timeThresholdHrs | int | `24` | Log rotation time threshold (hours) |
| mongodb.agent.maxLogFileDurationHours | int | `24` | Maximum log file duration in hours |
| mongodb.agent.systemLog.destination | string | `"file"` | System log destination |
| mongodb.agent.systemLog.logAppend | bool | `true` | Append to log file |
| mongodb.agent.systemLog.path | string | `"/var/log/mongodb-mms-automation/automation-agent.log"` | System log file path |
| mongodb.annotations | object | `{}` | Annotations to add to the MongoDB deployment |
| mongodb.arbiters | int | `0` | Number of arbiters in the replica set |
| mongodb.automationConfig.processes | list | `[]` | Process overrides for automation config |
| mongodb.automationConfig.replicaSet | object | `{}` | Replica set configuration overrides |
| mongodb.clusterDomain | string | `""` | Cluster domain for service DNS (e.g., "cluster.local") |
| mongodb.featureCompatibilityVersion | string | `""` | Feature compatibility version |
| mongodb.memberConfig | list | `[]` | Replica set member configuration |
| mongodb.members | int | `3` | Number of MongoDB replica set members |
| mongodb.prometheus.enabled | bool | `false` | Enable Prometheus metrics |
| mongodb.prometheus.metricsPath | string | `"/metrics"` | Prometheus metrics path |
| mongodb.prometheus.password | string | `"metrics-password"` | Prometheus metrics password |
| mongodb.prometheus.port | int | `9216` | Prometheus exporter port |
| mongodb.prometheus.tlsSecretKeyRef | object | `{}` | TLS secret key reference for Prometheus |
| mongodb.prometheus.username | string | `"metrics-user"` | Prometheus metrics username |
| mongodb.replicaSetHorizons | list | `[]` | Replica set horizons for external access |
| mongodb.security.authentication.agentCertificateSecretRef | object | `{}` | Agent certificate secret reference for X509 |
| mongodb.security.authentication.agentMode | string | `""` | Authentication mode for automation agent |
| mongodb.security.authentication.ignoreUnknownUsers | bool | `true` | Ignore unknown users |
| mongodb.security.authentication.modes | list | `["SCRAM"]` | Authentication modes (e.g., SCRAM, X509) |
| mongodb.security.roles | list | `[]` | Custom MongoDB roles |
| mongodb.security.tls.caCertificateSecretRef | object | `{}` | CA certificate secret reference |
| mongodb.security.tls.caConfigMapRef | object | `{}` | CA certificate config map reference |
| mongodb.security.tls.certificateKeySecretRef | object | `{}` | Certificate and key secret reference |
| mongodb.security.tls.enabled | bool | `false` | Enable TLS for MongoDB |
| mongodb.security.tls.optional | bool | `false` | Make TLS optional |
| mongodb.statefulSet.metadata.annotations | object | `{}` | Additional annotations for StatefulSet |
| mongodb.statefulSet.metadata.labels | object | `{}` | Additional labels for StatefulSet |
| mongodb.statefulSet.spec.template.metadata.labels | object | `{}` | Additional labels for pod template |
| mongodb.statefulSet.spec.template.spec.affinity | object | `{}` | Affinity rules for pod scheduling |
| mongodb.statefulSet.spec.template.spec.containers | list | `[]` | Additional containers |
| mongodb.statefulSet.spec.template.spec.imagePullSecrets | list | `[]` | Image pull secrets |
| mongodb.statefulSet.spec.template.spec.nodeSelector | object | `{}` | Node selector for pod scheduling |
| mongodb.statefulSet.spec.template.spec.tolerations | list | `[]` | Tolerations for pod scheduling |
| mongodb.statefulSet.spec.template.spec.volumes | list | `[]` | Additional volumes |
| mongodb.statefulSet.spec.volumeClaimTemplates[0].metadata.annotations | object | `{}` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[0].metadata.labels | object | `{}` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[0].metadata.name | string | `"data-volume"` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[0].spec.accessModes[0] | string | `"ReadWriteOnce"` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[0].spec.resources.requests.storage | string | `"10Gi"` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[0].spec.selector | object | `{}` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[0].spec.storageClassName | string | `""` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[1].metadata.annotations | object | `{}` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[1].metadata.labels | object | `{}` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[1].metadata.name | string | `"logs-volume"` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[1].spec.accessModes[0] | string | `"ReadWriteOnce"` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[1].spec.resources.requests.storage | string | `"5Gi"` |  |
| mongodb.statefulSet.spec.volumeClaimTemplates[1].spec.storageClassName | string | `""` |  |
| mongodb.type | string | `"ReplicaSet"` | MongoDB deployment type |
| mongodb.users | list | `[{"additionalConnectionStringConfig":{},"connectionStringSecretName":"","connectionStringSecretNamespace":"","db":"admin","name":"admin","password":"admin-password","roles":[{"db":"admin","name":"root"}],"scramCredentialsSecretName":"admin-scram-credentials"},{"db":"admin","name":"fintrade-rw","password":"fintrade-rw-password","roles":[{"db":"fintrade","name":"readWrite"},{"db":"fintrade","name":"dbAdmin"}],"scramCredentialsSecretName":"fintrade-rw-scram-credentials"}]` | MongoDB users configuration |
| nameOverride | string | `""` | Override the name of the chart |
| serviceAccount | object | `{"annotations":{},"automount":true,"create":true,"name":""}` | Service account configuration |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.automount | bool | `true` | Automatically mount a ServiceAccount's API credentials |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use |
| serviceMonitor | object | `{"enabled":false,"interval":"30s","metricRelabelings":[],"relabelings":[],"scrapeTimeout":"10s","serviceLabels":{"app":"mongodb-svc"}}` | ServiceMonitor configuration |
| serviceMonitor.enabled | bool | `false` | Enable or disable the ServiceMonitor |
| serviceMonitor.interval | string | `"30s"` | Scraping interval for the ServiceMonitor |
| serviceMonitor.metricRelabelings | list | `[]` | Metric relabeling rules |
| serviceMonitor.relabelings | list | `[]` | Relabeling rules |
| serviceMonitor.scrapeTimeout | string | `"10s"` | Scraping timeout for the ServiceMonitor |
| serviceMonitor.serviceLabels | object | `{"app":"mongodb-svc"}` | Service labels for selector matching |
