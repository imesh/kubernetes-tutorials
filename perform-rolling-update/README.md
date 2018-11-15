# Execute a Rolling Update

This tutorial guides you executing a rolling update for deploying a newer version of a software component.

# How to Run

1. Create a tomcat deployment with tomcat:8-slim image:

   ```bash
   cd perform-rolling-update/
   kubectl apply -f tomcat-deployment.yaml
   ```

2. Verify the current Tomcat version:

   ```bash
   kubectl get pods -l app=tomcat -o=yaml | grep image
   ```

3. Rollout the newer Tomcat version:

   ```bash
   kubectl set image deployments/tomcat tomcat=tomcat:9-slim
   ```

4. Check the rolling update process which creates a newer replica-set:

   ```bash
   kubectl get replicasets -l app=tomcat
   ```

5. Verify the newer Tomcat version

   ```bash
   kubectl get pods -l app=tomcat -o=yaml | grep image
   ```

# How to Rollback to Previous Version

1. Rollback to previous Tomcat version:
   
   ```bash
   kubectl rollout undo deployments/tomcat
   ```

2. Check the rolling update process which creates a newer replica-set:

   ```bash
   kubectl get replicasets -l app=tomcat
   ```

3. Verify the current version:

   ```bash
   kubectl get pods -l app=tomcat -o=yaml | grep image
   ```

# How to Clean

- Execute below commands to remove all Kubernetes resources created in this tutorial:
  
  ```bash
  kubectl delete -f tomcat-deployment.yaml
  kubectl delete -f tomcat-service.yaml
  ```
