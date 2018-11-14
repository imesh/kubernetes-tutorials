# Create a Secret and Expose as Environment Variables

This tutorial guides you creating a Kubernetes Secret and exposing that as environment variables.

## How to Run

1. Create credentials secret:

   ```bash
   kubectl apply -f credentials-secret.yaml
   ```
2. Create busybox pod:

   ```bash
   kubectl apply -f busybox-pod.yaml
   ```

3. Wait until the busybox pod status is changed to Completed:

   ```bash
   kubectl get pods/busybox

   NAME      READY     STATUS      RESTARTS   AGE
   busybox   0/1       Completed   0          4s
   ```

4. Check the output of the busybox pod:

   ```bash
   kubectl logs busybox
   
   KUBERNETES_PORT=tcp://xxx:443
   KUBERNETES_SERVICE_PORT=443
   HOSTNAME=busybox
   SHLVL=1
   HOME=/root
   SECRET_PASSWORD=1f2d1e2e67df
   KUBERNETES_PORT_443_TCP_ADDR=xxx
   PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
   KUBERNETES_PORT_443_TCP_PORT=443
   KUBERNETES_PORT_443_TCP_PROTO=tcp
   SECRET_USERNAME=admin
   KUBERNETES_SERVICE_PORT_HTTPS=443
   KUBERNETES_PORT_443_TCP=tcp://xxx:443
   PWD=/
   KUBERNETES_SERVICE_HOST=xxx
   ```

## How to Clean

- Execute below commands to remove all Kubernetes resources created in this tutorial:
  
  ```bash
  kubectl delete -f busybox-pod.yaml
  kubectl delete -f credentials-secret.yaml
  ```