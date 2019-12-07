# helm3-imagetrigger-test

Demo Chart to reproduce the case of https://github.com/helm/helm/pull/6987

This demo works only on Openshift.

# Prepare

1. Login into openshift
2. Create a project like `oc new-project test`
3. Download this Chart.
4. Install it `helm upgrade -i test .`

# How to reproduce this issue

1. run `helm upgrade -i test .`

Inside the namespace the Deployment will create 2 new deployments because
* the first one because helm revert the value back to the original state
* the second one bacause openshift will replace the value of the image field with the image spec from the imagestream.

# Documentation

* ImageTrigger:
  https://docs.openshift.com/container-platform/3.11/dev_guide/managing_images.html#image-stream-kubernetes-resources
