# Create a ConfigMap from Key/Value Pairs

This tutorial guides you creating a ConfigMap using key/value pairs and exposing them to a Pod as environment variables.

## How to Run

1. Have a look at `special-config` ConfigMap and `busybox` Pod definitions:

   ```bash
   cat special-config-configmap.yaml
   cat busybox-pod.yaml  
   ```

2. Create `special-config` ConfigMap:

   ```bash
   kubectl apply -f special-config-configmap.yaml
   ```

3. Create `busybox` Pod:

   ```bash
   kubectl apply -f busybox-pod.yaml
   ```

4. Wait until `busybox` Pod status changes to `Completed`:
   
   ```bash
   kubectl get pods/busybox

   NAME      READY     STATUS      RESTARTS   AGE
   busybox   0/1       Completed   0          4s
   ```
5. Check the output of the `busybox` Pod:

   ```bash
   kubectl logs busybox

   KUBERNETES_PORT=tcp://xxx:xxx
   KUBERNETES_SERVICE_PORT=xxx
   HOSTNAME=busybox
   SHLVL=1
   HOME=/root
   KUBERNETES_PORT_443_TCP_ADDR=xxx
   PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
   KUBERNETES_PORT_443_TCP_PORT=xxx
   KUBERNETES_PORT_443_TCP_PROTO=tcp
   SPECIAL_LEVEL_KEY=very
   KUBERNETES_SERVICE_PORT_HTTPS=xxx
   KUBERNETES_PORT_443_TCP=tcp://xxx:xxx
   PWD=/
   KUBERNETES_SERVICE_HOST=xxx
   ```

## How to Clean

- Execute below commands to remove all Kubernetes resources created in this tutorial:
  
  ```bash
  kubectl delete -f busybox-pod.yaml
  kubectl delete -f special-config-configmap.yaml
  ```