# Helm Chart for EFK logging


```console
$ git clone https://github.com/ab250/assignment.git
$ cd assignment/efk-helm

```

## Installing the Chart

To install the chart with the release name my-release

```console
$ helm install --name my-release . --namespace=kube-system
```
## accessing kibana

```console
$ kubectl get svc | grep kibana
find the external port number mapped to 5601 service port
run 'http://<NODE IP>:<external port>' in browser

```

## Uninstalling the Chart


```console
$ helm delete my-release
```


## Configuration

### Kibana

| Parameter                  | Description                         | Default                                                 |
|----------------------------|-------------------------------------|---------------------------------------------------------|
| `rbac.enabled` | Enables RBAC | `false` |
| `kibana.replicaCount`                 | Number of Kibana nodes | `1` |
| `kibana.image.repository`         | Image repository | `docker.elastic.co/kibana/kibana` |
| `kibana.image.tag`                | Image tag. | `6.2.4`|
| `kibana.image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `kibana.service.type`             | Kubernetes service type | `ClusterIP` |
| `kibana.service.port`             | Kubernetes port where service is exposed| `5601` |
| `kibana.ingress.enabled`          | Enables Ingress | `false` |
| `kibana.ingress.annotations`      | Ingress annotations | `{}` |
| `kibana.ingress.path`           | Custom path                       | `/`
| `kibana.ingress.hosts`            | Ingress accepted hostnames | `[kibana.chart.example.com]` |
| `kibana.ingress.tls`              | Ingress TLS configuration | `[]` |
| `kibana.resources.limits.cpu`                | CPU resource limits | `1000m` |
| `kibana.resources.requests.cpu`                | CPU resource requests | `100m` |
| `kibana.nodeSelector`             | Node labels for pod assignment | `{}` |
| `kibana.tolerations`              | Toleration labels for pod assignment | `[]` |
| `kibana.affinity`                 | Affinity settings for pod assignment | `{}` |
| `elasticsearch.replicaCount`                 | Number of ElasticSearch nodes | `1` |
| `elasticsearch.image.repository`         | Image repository | `docker.elastic.co/elasticsearch/elasticsearch` |
| `elasticsearch.image.tag`                | Image tag. | `6.2.4`|
| `elasticsearch.image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `elasticsearch.service.type`             | Kubernetes service type | `ClusterIP` |
| `elasticsearch.service.port`             | Kubernetes port where service is exposed| `9200` |
| `elasticsearch.resources.limits.cpu`                | CPU resource limits | `1000m` |
| `elasticsearch.resources.requests.cpu`                | CPU resource requests | `100m` |
| `elasticsearch.nodeSelector`             | Node labels for pod assignment | `{}` |
| `elasticsearch.tolerations`              | Toleration labels for pod assignment | `[]` |
| `elasticsearch.affinity`                 | Affinity settings for pod assignment | `{}` |
| `fluentdElasticsearch.replicaCount`                 | Number of ElasticSearch nodes | `1` |
| `fluentdElasticsearch.image.repository`         | Image repository | `k8s.gcr.io/fluentd-elasticsearch` |
| `fluentdElasticsearch.image.tag`                | Image tag. | `v2.0.4`|
| `fluentdElasticsearch.image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `fluentdElasticsearch.service.type`             | Kubernetes service type | `ClusterIP` |
| `fluentdElasticsearch.service.port`             | Kubernetes port where service is exposed| `9200` |
| `fluentdElasticsearch.resources.limits.memory`                | Mem resource limits | `500Mi` |
| `fluentdElasticsearch.resources.requests.cpu`                | CPU resource requests | `100m` |
| `fluentdElasticsearch.resources.requests.memory`                | Mem resource requests | `200Mi` |
| `fluentdElasticsearch.nodeSelector`             | Node labels for pod assignment | `{}` |
| `fluentdElasticsearch.tolerations`              | Toleration labels for pod assignment | `[]` |
| `fluentdElasticsearch.affinity`                 | Affinity settings for pod assignment | `{}` |
| `fluentdElasticsearch.dockerContainersPath`      | Path to docker containers on the node | `"/var/lib/docker/containers"` |

