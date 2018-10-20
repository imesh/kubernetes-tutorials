# Create a Tomcat Pod

This tutorial guides you to create an Apache Tomcat container on Kubernetes using a Kubernetes Pod definition and access it using a Kubernetes Service of Load Balancer Type.

## Steps to follow:

1. Create Tomcat pod:

```
kubectl apply -f tomcat-pod.yaml
```

2. Check Tomcat pod status:

```bash
kubectl get pods/tomcat
```

3. Now create the Tomcat service for exposing it via an external endpoint. On Google Kubernetes Engine (GKE) this action will create a Load Balancer:

```bash
kubectl apply -f tomcat-service.yaml
```

4. Wait until Tomcat service becomes active:

```bash
kubectl get services/tomcat
```

