# Create a ConfigMap for Updating Server Configurations

This tutorial guides you on creating a ConfigMap for updating configurations of Apache Tomcat.

## How to run:

1. Have a look at the `<Connector port="9090">` section of the Apache Tomcat server.xml configuration file located in the `conf/` folder. Here, we have updated the default HTTP port to `9090`:

   ```bash
   cat conf/server.xml
   ```

2. Create a ConfigMap by pointing to the `conf/server.xml` file:

   ```bash
   kubectl create configmap tomcat-server-xml-conf --from-file=conf/server.xml 
   ```
3. Have a look at the `volumeMounts` and `volumes` sections of the Apache Tomcat Pod definition in the `tomcat-pod.yaml` file.

4. Create a Tomcat Pod:

   ```bash
   kubectl apply -f tomcat-pod.yaml
   ```

5. Wait until the Tomcat Pod status is changed to Running:

   ```bash
   kubectl get pod
   
   NAME      READY     STATUS    RESTARTS   AGE
   tomcat    1/1       Running   0          1m
   ```

6. Verify the updated configuration:

   ```bash
   kubectl exec -it tomcat bash
   netstat -nlp
   
   Active Internet connections (only servers)
   Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
   tcp        0      0 :::9090                 :::*                    LISTEN      1/java
   tcp        0      0 ::ffff:127.0.0.1:8005   :::*                    LISTEN      1/java
   tcp        0      0 :::8009                 :::*                    LISTEN      1/java
   Active UNIX domain sockets (only servers)
   Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
   ```

