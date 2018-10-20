# Create a Tomcat Deployment

This tutorial guides you to create an Apache Tomcat container on Kubernetes using kubectl run command and Kubernetes Deployment definition.

## Using Run Command

1. Create an apache tomcat deployment using kubectl run command:

```bash
kubectl run tomcat --image=tomcat:alpine --port=8080
```

2. Expose tomcat using a load balancer type service using kubectl expose command:

```bash
kubectl expose deployment tomcat --name=tomcat --type=LoadBalancer --port=80 --target-port=8080
```

## Using a Deployment Definition

1. Create Tomcat deployment:

```
kubectl apply -f tomcat-deployment.yaml
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

5. Access Tomcat home page using a web browser with the external IP address found above.