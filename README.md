# Example Website

First: https://github.com/golden-image-example/nginx
Second: https://github.com/golden-image-example/php


```console
oc new-project golden-image-example | oc project golden-image-example

oc create -f ./tekton/apply_manifest_task.yaml -n golden-image-example
oc create -f ./tekton/update_deployment_task.yaml -n golden-image-example
oc create -f ./tekton/wait_for_deployment_task.yaml -n golden-image-example
oc create -f ./tekton/oc_rsync_task.yaml -n golden-image-example
oc create -f ./tekton/oc_exec_task.yaml -n golden-image-example
```

```
oc create -f ./tekton/pipeline-single-deployment.yaml -n golden-image-example
```


```
oc create -f ./tekton/pipeline.yaml -n golden-image-example

curl https://$(oc get route nginx --template={{.spec.host}})
```