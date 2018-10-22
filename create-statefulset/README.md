# Create a Cassandra Ring on Kubernetes

This tutorial was directly taken from official Kubernetes tutorial [Example: Deploying Cassandra with Stateful Sets](https://kubernetes.io/docs/tutorials/stateful-application/cassandra/).

## How to run

1. Create Cassandra Service:

```bash
kubectl apply -f cassandra-service.yaml
```

2. Create Cassandra StatefulSet:

```bash
kubectl apply -f cassandra-statefulset.yaml
```