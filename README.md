# Example Website

```console
oc create -f ./tekton/apply_manifest_task.yaml -n golden-image-example

oc create -f ./tekton/update_deployment_task.yaml -n golden-image-example

oc create -f ./tekton/wait_for_deployment_task.yaml -n golden-image-example

oc create -f ./tekton/oc_rsh_task.yaml -n golden-image-example
```

```
oc wait --for=condition=available --timeout=60s deployment/php -n golden-image-example && oc wait --for=condition=available --timeout=60s deployment/nginx -n golden-image-example
```

```
oc new-project golden-image-example | oc project golden-image-example

oc create -f ./tekton/apply_manifest_task.yaml -n golden-image-example
oc create -f ./tekton/update_deployment_task.yaml -n golden-image-example
oc create -f ./tekton/wait_for_deployment_task.yaml -n golden-image-example
oc create -f ./tekton/oc_rsh_task.yaml -n golden-image-example
oc create -f ./tekton/pipeline.yaml -n golden-image-example

curl https://$(oc get route nginx --template={{.spec.host}})
```