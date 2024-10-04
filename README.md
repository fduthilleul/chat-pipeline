# Demo Steps

## Clone this demo to your local environment

```
git clone https://github.com/fduthilleul/chat-pipeline.git
```
## Create a project acs-pipeline-demo and enter the project
```
oc create ns acs-pipeline-demo
```
```
oc project acs-pipeline-demo
```
## Create a K8s secret with your Quay credentials
```
podman login quay.io
```

```
oc create secret generic regcred --from-file=.dockerconfigjson=$HOME/.docker/config.json --type=kubernetes.io/dockerconfigjson
```
## Create a K8s secret with your ACS API token
```
oc create secret generic acstoken --from-literal=token=<add-your-api-token>
```
## Create the artifacts
```
oc create -f deploy .
```
## Add role and SCC to Service Account
```
oc adm policy add-role-to-user isview -z pipeline-svc --role-namespace=dso-pipeline -n dso-pipeline
```

```
oc adm policy add-scc-to-user privileged -z pipeline-svc
```
## TBA
```
oc create -f pipeline-run-with-scan.yaml
```
