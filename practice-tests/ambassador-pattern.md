## Ambassador Sidecar Container Lab 

### This lab and solution are part of the KPLABS course.

### Question: 

Enterprise Corp has a legacy application that was built by the team which no longer exists. All the members of the team have left the organization. The legacy application only works on the port of 9080. The client does not want to always include port 9080 in their request.

They want that the application should be accessible via port 80. Create an ambassador container based on HAProxy which can handle the scenario. You don't have to learn about HAProxy. All the configuration files are provided.
 
1.  Create a pod named kplabs-ambassador-pod from the legacy application image.

2. Create configmap called as kplabs-ambassador-config which has the following data:
```sh
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
```
3. Create an ambassador container from the image of haproxy:1.7
4. Expose the port 80 from Haproxy container.
5. Mount the configmap to the haproxy in such a way that HAProxy config is available at the following file:
```sh
 /usr/local/etc/haproxy/haproxy.cfg
```
6. Create a Busybox pod from following pod definition:
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
7. Verify if you can perform CURL from busybox pod towards the ambassador pod on port 80.
