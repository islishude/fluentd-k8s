# fluentd on kubernetes

# Install elastic and kibana

## [Install elastic operator](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-eck.html)

```
kubectl create -f https://download.elastic.co/downloads/eck/2.1.0/crds.yaml

kubectl apply -f https://download.elastic.co/downloads/eck/2.1.0/operator.yaml
```

## Start elasticsearch

```
kubectl apply -f k8s/es.yaml
```

## Get elastic password

kubectl get secret quickstart-es-elastic-user -o go-template='{{.data.elastic | base64decode}}'

## Start kibana

kubectl apply -f k8s/kibana.yaml 

## Open kibana

```
kubectl port-forward svc/kibana-kb-http 5601
```

On anthor terminal pannel

```
open http://localhost:5601
```

# Start fluentd

```
kubectl apply -f k8s/fluentd-rbac.yaml
kubectl apply -f k8s/fluentd.yaml
```

# Start test app

```
kubectl apply -f k8s/testapp.yaml
```
