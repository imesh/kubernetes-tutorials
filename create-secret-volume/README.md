# Create a Secret and Expose as a Volume Mount

This tutorial guides you creating a Kubernetes Secret and exposing that as a volume mount.

## How to Run

1. Create credentials secret:

   ```bash
   kubectl apply -f credentials-secret.yaml
   ```
2. Create busybox pod:

   ```bash
   kubectl apply -f busybox-pod.yaml
   ```

3. Wait until the busybox pod status is changed to Running:

   ```bash
   kubectl get pods/busybox

   NAME      READY     STATUS      RESTARTS   AGE
   busybox   0/1       Running     0          4s
   ```

4. Check the contents of the volume `/etc/secrets`:

   ```bash
   kubectl exec -it busybox sh
   ls /etc/credentials
   password  username

   cat /etc/credentials/username
   admin
   
   cat /etc/credentials/password
   1f2d1e2e67df
   ```

## How to Clean

- Execute below commands to remove all Kubernetes resources created in this tutorial:
  
  ```bash
  kubectl delete -f busybox-pod.yaml
  kubectl delete -f credentials-secret.yaml
  ```

