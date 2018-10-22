# Create a Sample DaemonSet

This tutorial creates a sample daemonset using `gcr.io/google-samples/node-hello:1.0` docker image in the default namespace.

## Create DaemonSet
kubectl apply -f hello-daemonset.yaml

## Remove DaemonSet
kubectl delete -f hello-deamonset.yaml