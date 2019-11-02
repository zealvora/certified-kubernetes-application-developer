### Question 1: Multi-Container Pods

<details><summary>Expand The Question </summary>
<p>

a. Create a Multi-Container POD with the name of kplabs-multi-container. 

b. There should be three containers in the pod. 

c. Name the first container should be first-container, 2nd container should be second-container and 3rd container should be third-container

d. 1st container should be launched from nginx image, second container should be launched from mykplabs/kubernetes:nginx image and third container from busybox image.

e. Connect to the first-container and run the following command:  apt-get update && apt-get install net-tools

f. Connect to the third-container and identify the ports in which processes are listening. Perform wget command on those ports and check if you can download the HTML page.

</details>

### Question 2: Ambassador Container 

<details><summary>Expand The Question </summary>
<p>

Enterprise Corp has a legacy application that was built by the team which no longer exists. All the members of the team have left the organization. The legacy application only works on the port of 9080. The client does not want to always include port 9080 in their request. They want that the application should be accessible via port 80. Create an ambassador container based on HAProxy which can handle the scenario. You don't have to learn about HAProxy. All the configuration files are provided.
 
Create a pod named kplabs-ambassador-pod from the legacy application image.
Create configmap called as kplabs-ambassador-config which has the following data:

    global
        daemon
        maxconn 256

    defaults
        mode http
        timeout connect 5000ms
        timeout client 50000ms
        timeout server 50000ms

    listen http-in
        bind *:80
        server server1 127.0.0.1:9080 maxconn 32

Create an ambassador container from the image of haproxy:1.7

Expose the port 80 from Haproxy container.

Mount the configmap to the haproxy in such a way that HAProxy config is available at the following file:
```sh
 /usr/local/etc/haproxy/haproxy.cfg
```
Create a Busybox pod from following pod definition:
```sh
apiVersion: v1
kind: Pod
metadata:
  name: kplabs-busybox-curl
spec:
  containers:
  - name: curl-container
    image: yauritux/busybox-curl
    command: ['sh', '-c', 'while true; do sleep 3600; done']
```

Verify if you can perform CURL from busybox pod towards the ambassador pod on port 80.

</details>


### Question 3: Adapter Pattern

<details><summary>Expand The Question </summary>
<p>

Create a pod named kplabs-adapter-logging.

The Pod should have a container running from the busybox image with the following arguments:

    - /bin/sh
    - -c
    - >
      i=0;
      while true;
      do
        echo "$i: $(date)" >> /var/log/1.log;
        echo "$(date) INFO $i" >> /var/log/2.log;
        i=$((i+1));
        sleep 1;
      done

Create and mount a volume under the mount path of /var/log of the first container. The volume should be removed as soon as the pod is deleted. 

Create a second container in the pod. It should be launched from the following image. 

```sh
k8s.gcr.io/fluentd-gcp:1.30
```

The container should have an environment variable named FLUENTD_ARGS with following values:
```sh
-c /etc/fluentd-config/fluentd.conf
```
The second container should also have the same volume as the first container mounted on the path of /var/log

The second container should also have a fluentd configuration (mentioned in below configmap) available in the following path:
```sh 
/etc/fluentd-config/fluentd.conf
```

Create a ConfigMap object with the name of fluentd-config. The ConfigMap should have the following configuration:

```sh
    <source>
      type tail
      format none
      path /var/log/1.log
      pos_file /var/log/1.log.pos
      tag PHP
    </source>

    <source>
      type tail
      format none
      path /var/log/2.log
      pos_file /var/log/2.log.pos
      tag JAVA
    </source>

    <match **>
       @type file
       path /var/log/fluent/access
    </match>
```
Verify if you can see log files with the tag of PHP and JAVA under the following directory
```sh 
/var/log/fluent/access 
```
</details>

