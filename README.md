```
podman login quay.io
```

```
oc create secret generic regcred --from-file=.dockerconfigjson=$HOME/containers/auth.json --type=kubernetes.io/dockerconfigjson
```
```
oc create secret generic acstoken --from-literal=token=<add-your-api-token>
```

```
oc create -f deploy
```

```
oc adm policy add-role-to-user isview -z pipeline-svc --role-namespace=dso-pipeline -n dso-pipeline
```

```
oc adm policy add-scc-to-user privileged -z pipeline-svc
```

```
oc create -f pipeline-run-with-scan.yaml
```
