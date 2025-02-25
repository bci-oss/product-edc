# edc-controlplane

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.0.1](https://img.shields.io/badge/AppVersion-0.0.1-informational?style=flat-square)

EDC Control-Plane - The Eclipse DataSpaceConnector administration layer with responsibility of resource management and govern contracts and data transfers

**Homepage:** <https://github.com/catenax-ng/product-edc/deployment/helm/edc-controlplane>

## TL;DR
```shell
$ helm repo add catenax-ng-product-edc https://catenax-ng.github.io/product-edc
$ helm install my-release catenax-ng-product-edc/edc-controlplane
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | [Affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#affinity-and-anti-affinity) constrains which nodes the Pod can be scheduled on based on node labels. |
| autoscaling.enabled | bool | `false` | Enables [horizontal pod autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) |
| autoscaling.maxReplicas | int | `100` | Maximum replicas if resource consumption exceeds resource threshholds |
| autoscaling.minReplicas | int | `1` | Minimal replicas if resource consumption falls below resource threshholds |
| autoscaling.targetCPUUtilizationPercentage | int | `80` | targetAverageUtilization of cpu provided to a pod |
| autoscaling.targetMemoryUtilizationPercentage | int | `80` | targetAverageUtilization of memory provided to a pod |
| configuration.properties | string | `"# edc.api.auth.key=\n# edc.api.control.auth.apikey.key=\n# edc.api.control.auth.apikey.value=\n# edc.assetindex.cosmos.account-name=\n# edc.assetindex.cosmos.container-name=\n# edc.assetindex.cosmos.database-name=\n# edc.assetindex.cosmos.preferred-region=\n# edc.atomikos.checkpoint.interval=\n# edc.atomikos.directory=\n# edc.atomikos.logging=\n# edc.atomikos.threaded2pc=\n# edc.atomikos.timeout=\n# edc.aws.access.key=\n# edc.aws.provision.retry.retries.max=\n# edc.aws.provision.role.duration.session.max=\n# edc.aws.secret.access.key=\n# edc.blobstore.endpoint=\n# edc.contractdefinitionstore.cosmos.account-name=\n# edc.contractdefinitionstore.cosmos.container-name=\n# edc.contractdefinitionstore.cosmos.database-name=\n# edc.contractdefinitionstore.cosmos.preferred-region=\n# edc.contractnegotiationstore.cosmos.account-name=\n# edc.contractnegotiationstore.cosmos.container-name=\n# edc.contractnegotiationstore.cosmos.database-name=\n# edc.contractnegotiationstore.cosmos.preferred-region=\n# edc.controlplane.validation-endpoint=\n# edc.core.retry.backoff.max=\n# edc.core.retry.backoff.min=\n# edc.core.retry.retries.max=\n# edc.core.system.health.check.liveness-period=\n# edc.core.system.health.check.readiness-period=\n# edc.core.system.health.check.startup-period=\n# edc.core.system.health.check.threadpool-size=\n# edc.cosmos.partition-key=\n# edc.cosmos.query-metrics-enabled=\n# edc.dataplane.queue.capacity=\n# edc.dataplane.wait=\n# edc.dataplane.workers=\n# edc.datasource.asset.name=\"default\"\n# edc.datasource.contractdefinition.name=\"default\"\n# edc.datasource.contractnegotiation.name=\"default\"\n# edc.datasource.policy.name=\"default\"\n# edc.datasource.transferprocess.name=\"default\"\n# edc.datasource.default.pool.maxIdleConnections=\n# edc.datasource.default.pool.maxTotalConnections=\n# edc.datasource.default.pool.minIdleConnections=\n# edc.datasource.default.pool.testConnectionOnBorrow=\n# edc.datasource.default.pool.testConnectionOnCreate=\n# edc.datasource.default.pool.testConnectionOnReturn=\n# edc.datasource.default.pool.testConnectionWhileIdle=\n# edc.datasource.default.pool.testQuery=\n# edc.datasource.default.url=\n# edc.datasource.default.user=\n# edc.datasource.default.password=\n# edc.dpf.selector.url=\n# edc.events.topic.endpoint=\n# edc.events.topic.name=\n# edc.fs.config=\n# edc.hostname=\n# edc.identity.did.url=\n# edc.ids.catalog.id=\n# edc.ids.curator=\n# edc.ids.description=\n# edc.ids.endpoint=\n# edc.ids.id=\n# edc.ids.maintainer=\n# edc.ids.security.profile=\n# edc.ids.title=\n# edc.ids.validation.referringconnector=\n# edc.ion.crawler.did-type=\n# edc.ion.crawler.interval-minutes=\n# edc.ion.crawler.ion.url=\n# edc.metrics.enabled=\n# edc.metrics.executor.enabled=\n# edc.metrics.jersey.enabled=\n# edc.metrics.jetty.enabled=\n# edc.metrics.okhttp.enabled=\n# edc.metrics.system.enabled=\n# edc.negotiation.consumer.state-machine.batch-size=\n# edc.negotiation.provider.state-machine.batch-size=\n# edc.node.directory.cosmos.account.name=\n# edc.node.directory.cosmos.container.name=\n# edc.node.directory.cosmos.database.name=\n# edc.node.directory.cosmos.preferred.region=\n# edc.oauth.client.id=\n# edc.oauth.private.key.alias=\n# edc.oauth.provider.audience=\n# edc.oauth.provider.jwks.refresh=\n# edc.oauth.provider.jwks.url=\n# edc.oauth.public.key.alias=\n# edc.oauth.token.url=\n# edc.oauth.validation.nbf.leeway=\n# edc.receiver.http.auth-code=\n# edc.receiver.http.auth-key=\n# edc.receiver.http.endpoint=\n# edc.transfer.proxy.endpoint=\n# edc.transfer.dataplane.sync.token.validity=\n# edc.transfer.proxy.token.signer.privatekey.alias=\n# edc.transfer.functions.check.endpoint=\n# edc.transfer.functions.enabled.protocols=\n# edc.transfer.functions.transfer.endpoint=\n# edc.transfer-process-store.cosmos.account.name=\n# edc.transfer-process-store.cosmos.container-name=\n# edc.transfer-process-store.cosmos.preferred-region=\n# edc.transfer-process-store.database.name=\n# edc.transfer.state-machine.batch-size=\n# edc.vault=\n# edc.vault.certificate=\n# edc.vault.clientid=\n# edc.vault.clientsecret=\n# edc.vault.name=\n# edc.vault.tenantid=\n# edc.webdid.doh.url=\n# edc.web.rest.cors.enabled=\n# edc.web.rest.cors.headers=\n# edc.web.rest.cors.methods=\n# edc.web.rest.cors.origins="` | EDC configuration.properties configuring aspects of the [eclipse-dataspaceconnector](https://github.com/eclipse-dataspaceconnector/DataSpaceConnector) |
| edc.endpoints.control.path | string | `"/api/controlplane/control"` | The path mapping the "control" api is going to be exposed at |
| edc.endpoints.control.port | string | `"9999"` | The network port, which the "control" api is going to be exposed by the container, pod and service |
| edc.endpoints.data.path | string | `"/data"` | The path mapping the "data" management api is going to be exposed at |
| edc.endpoints.data.port | string | `"8181"` | The network port, which the "data" management api is going to be exposed by the container, pod and service |
| edc.endpoints.default.path | string | `"/api"` | The path mapping the "default" api is going to be exposed at |
| edc.endpoints.default.port | string | `"8080"` | The network port, which the "default" api is going to be exposed by the container, pod and service |
| edc.endpoints.ids.path | string | `"/api/v1/ids"` | The path mapping the "ids" multipart api is going to be exposed at |
| edc.endpoints.ids.port | string | `"8282"` | The network port, which the "ids" multipart api is going to be exposed by the container, pod and service |
| edc.endpoints.metrics.path | string | `"/metrics"` | The path mapping the prometheus metrics are going to be exposed at |
| edc.endpoints.metrics.port | string | `"9090"` | The network port, which the prometheus metrics are going to be exposed by the container, pod and service |
| edc.endpoints.validation.path | string | `"/validation"` | The path mapping the "validation" api is going to be exposed at |
| edc.endpoints.validation.port | string | `"8182"` | The network port, which the "validation" api is going to be exposed by the container, pod and service |
| env | object | `{}` | Container environment variables e.g. for configuring [JAVA_TOOL_OPTIONS](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/envvars002.html) Ex.:   JAVA_TOOL_OPTIONS: >     -Dhttp.proxyHost=proxy -Dhttp.proxyPort=80 -Dhttp.nonProxyHosts="localhost|127.*|[::1]" -Dhttps.proxyHost=proxy -Dhttps.proxyPort=443 |
| fullnameOverride | string | `""` | Overrides the releases full name |
| image.pullPolicy | string | `"IfNotPresent"` | [Kubernetes image pull policy](https://kubernetes.io/docs/concepts/containers/images/#image-pull-policy) to use |
| image.repository | string | `"ghcr.io/catenax-ng/product-edc/edc-controlplane-memory"` | Which derivate of the edc controlplane to use. One of: [ghcr.io/catenax-ng/product-edc/edc-controlplane-memory, , ghcr.io/catenax-ng/product-edc/edc-controlplane-postgresql, ghcr.io/catenax-ng/product-edc/edc-controlplane-cosmosdb] |
| image.tag | string | `""` | Overrides the image tag whose default is the chart appVersion. |
| imagePullSecret.dockerconfigjson | string | `""` | Image pull secret to create to [obtain the container image from private registries](https://kubernetes.io/docs/concepts/containers/images/#using-a-private-registry) Note: This value needs to adhere to the [(base64 encoded) .dockerconfigjson format](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/#registry-secret-existing-credentials). Furthermore, if 'imagePullSecret.dockerconfigjson' is defined, it takes precedence over 'imagePullSecrets'. |
| imagePullSecrets | list | `[]` | Existing image pull secret to use to [obtain the container image from private registries](https://kubernetes.io/docs/concepts/containers/images/#using-a-private-registry) |
| ingresses[0].annotations | object | `{}` | Additional ingress annotations to add |
| ingresses[0].certManager.clusterIssuer | string | `""` | If preset enables certificate generation via cert-manager cluster-wide issuer |
| ingresses[0].certManager.issuer | string | `""` | If preset enables certificate generation via cert-manager namespace scoped issuer |
| ingresses[0].className | string | `""` | Defines the [ingress class](https://kubernetes.io/docs/concepts/services-networking/ingress/#ingress-class)  to use |
| ingresses[0].enabled | bool | `true` |  |
| ingresses[0].endpoints | list | `["ids"]` | EDC endpoints exposed by this ingress resource |
| ingresses[0].hostname | string | `"edc-controlplane.local"` | The hostname to be used to precisely map incoming traffic onto the underlying network service |
| ingresses[0].tls | bool | `false` | Enables TLS on the ingress resource |
| ingresses[1].annotations | object | `{}` | Additional ingress annotations to add |
| ingresses[1].certManager.clusterIssuer | string | `""` | If preset enables certificate generation via cert-manager cluster-wide issuer |
| ingresses[1].certManager.issuer | string | `""` | If preset enables certificate generation via cert-manager namespace scoped issuer |
| ingresses[1].className | string | `""` | Defines the [ingress class](https://kubernetes.io/docs/concepts/services-networking/ingress/#ingress-class)  to use |
| ingresses[1].enabled | bool | `false` |  |
| ingresses[1].endpoints | list | `["data","control"]` | EDC endpoints exposed by this ingress resource |
| ingresses[1].hostname | string | `"edc-controlplane.intranet"` | The hostname to be used to precisely map incoming traffic onto the underlying network service |
| ingresses[1].tls | bool | `false` | Enables TLS on the ingress resource |
| livenessProbe.enabled | bool | `true` | Whether to enable kubernetes [liveness-probe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/) |
| logging.properties | string | `".level=INFO\norg.eclipse.dataspaceconnector.level=ALL\nhandlers=java.util.logging.ConsoleHandler\njava.util.logging.ConsoleHandler.formatter=java.util.logging.SimpleFormatter\njava.util.logging.ConsoleHandler.level=ALL\njava.util.logging.SimpleFormatter.format=[%1$tY-%1$tm-%1$td %1$tH:%1$tM:%1$tS] [%4$-7s] %5$s%6$s%n"` | EDC logging.properties configuring the [java.util.logging subsystem](https://docs.oracle.com/javase/7/docs/technotes/guides/logging/overview.html#a1.8) |
| nameOverride | string | `""` | Overrides the charts name |
| nodeSelector | object | `{}` | [Node-Selector](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#nodeselector) to constrain the Pod to nodes with specific labels. |
| opentelemetry.properties | string | `"otel.javaagent.enabled=true\notel.javaagent.debug=false"` | opentelemetry.properties configuring the [opentelemetry agent](https://opentelemetry.io/docs/instrumentation/java/automatic/agent-config/) |
| podAnnotations | object | `{}` | [Annotations](https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/) added to deployed [pods](https://kubernetes.io/docs/concepts/workloads/pods/) |
| podSecurityContext | object | `{}` | The [pod security context](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/#set-the-security-context-for-a-pod) defines privilege and access control settings for a Pod within the deployment |
| readinessProbe.enabled | bool | `true` | Whether to enable kubernetes readiness-probes |
| replicaCount | int | `1` | Specifies how many replicas of a deployed pod shall be created during the deployment Note: If horizontal pod autoscaling is enabled this setting has no effect |
| resources | object | `{}` | [Resource management](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/) applied to the deployed pod |
| securityContext.runAsNonRoot | bool | `true` | Requires the container to run without root privileges |
| securityContext.runAsUser | int | `1000` | The container's process will run with the specified uid |
| service.type | string | `"ClusterIP"` | [Service type](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) to expose the running application on a set of Pods as a network service. |
| serviceAccount.annotations | object | `{}` | [Annotations](https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/) to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a [service account](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/) should be created per release |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the release's fullname template |
| startupProbe.enabled | bool | `true` | Whether to enable kubernetes startup-probes |
| tolerations | list | `[]` | [Tolerations](https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/) are applied to Pods to schedule onto nodes with matching taints. |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.10.0](https://github.com/norwoodj/helm-docs/releases/v1.10.0)
