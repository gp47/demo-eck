# Demo-eck

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

## Request an Access

TBC