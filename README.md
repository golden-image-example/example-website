# Example Website

```console
oc create -f ./tekton/apply_manifest_task.yaml -n golden-image-example

oc create -f ./tekton/update_deployment_task.yaml -n golden-image-example
```

```
oc new-project golden-image-example | oc project golden-image-example
oc create -f ./tekton/pipeline.yaml -n golden-image-example
```