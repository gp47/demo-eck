# Demo-ECK


## Summary

This is a demo/playground of Elastic Cloud On Kubernetes [(ECK)](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-eck.html).


## Deployment

Install custom resource definitions:
```
kubectl apply -f src/crds.yaml
```
Install the operator with its RBAC rules:
```
kubectl apply -f src/operator.yaml
```

Monitor the operator logs:
```
kubectl -n elastic-system logs -f statefulset.apps/elastic-operator
```


## Deploy ElasticSearch

```
kubectl apply -f src/elasticsearch.yaml
```

### Request an Access

```
kubectl -n elasticsearch get secret elasticsearch-es-elastic-user -o go-template='{{.data.elastic | base64decode}}'
```
then
```
kubectl -n elasticsearch port-forward svc/elasticsearch-es-http 9200
```


## Deploy Kibana Instance

```
kubectl apply -f src/kibana.yaml
```

### Access Kibana

```
kubectl -n elasticsearch get secret elasticsearch-es-elastic-user -o go-template='{{.data.elastic | base64decode}}'
```
then
```
kubectl -n elasticsearch port-forward svc/kibana-kb-http 5601
```


