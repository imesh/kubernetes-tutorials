# Create a Persistent Volume using a Persistent Volume Claim

This tutorial guides you creating a persistent volume (pv) using a persistent volume claim (pvc) and mounting it to a pod.

## How to Run

1. Create persistent volume claim:

   ```bash
   kubectl create -f busybox-pvc.yaml
   ```

2. Wait until persistent volume's status is changed to Bound:

   ```bash
   kubectl get pvc/busybox-pvc

   NAME          STATUS    VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
   busybox-pvc   Bound     pvc-504ab23d-e863-11e8-af7d-42010a9800cd   1Gi        RWO            standard       1m
   ```

3. Create busybox pod:

   ```bash
   kubectl apply -f busybox-pod.yaml
   ```

4. Wait until pod's status is changed to Running:

   ```bash
   kubectl get pods/busybox

   NAME      READY     STATUS    RESTARTS   AGE
   busybox   1/1       Running   0          10s
   ```

5. Verify the volume mount:

   ```
   kubectl exec -it busybox sh
   echo "Hello persistent volumes!" > /mnt/volume1/hello-pv.txt
   cat /mnt/volume1/hello-pv.txt

   # Now, delete this pod and create a new one and check the above file
   ```

## How to Clean

- Execute below commands to remove all Kubernetes resources created in this tutorial:
  
  ```bash
  kubectl delete -f busybox-pod.yaml
  kubectl delete -f busybox-pvc.yaml
  ```
