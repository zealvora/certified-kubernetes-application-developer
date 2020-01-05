### Question 1: ConfigMap
<details><summary>Expand The Question </summary>
<p>
Create a configmap named kplabs-config which contains all the contents of that file.

course: kubernetes 2020

instructor: zeal

type: certification

Mount the configmap to a pod named configmap-pod based on nginx image in such a way that all contents are available at /etc/config/kplabs.config

</details>

### Question 2 - PV and PVC
<details><summary>Expand The Question </summary>
<p>

Create a persistent volume with the name kplabs-pv. The size should be 2Gi and hostpath should be /tmp/mydata. It should have access mode of ReadWriteOnce 

Create a persistent volume claim that will make use of the PV created earlier.

Create a Pod named kplabs-pv-pod. The POD should have the volume mounted at /mydata directory.
</details>

### Question 3 - Security Context
<details><summary>Expand The Question </summary>
<p>
Create a POD named busybox-security. The pod should run command "sleep 3600".  The primary process in POD should run with UID of 1000 and GID of 2000 all contents of volume any mounted volume should have the group ID of 3000.
</details>

### Question 4: Secrets and Enviornement Variables
<details><summary>Expand The Question </summary>
<p>

Andrew works as a database administrator and has generated set of credentials that will be used by the application to connect to the database. Instead of giving the credentials to developers to hard-code in their application, he has requested security team to create a secret and mount it as enviornement variable to the application containers.

a. Create a secret name db-creds which has following data: 
       user: dbreadonly
       pass: myDBPassword#%
       
b. Create a pod from nginx image.

c. Mount the secret to the POD in such a way that the contents of database user is available in form of DB_USER enviornement variable and database password is available in form of DB_PASSWORD environment variable inside the container.

</details>

### Question 5: Secrets and Volumes

<details><summary>Expand The Question </summary>
<p>


a. Create a secret name app-creds which has following data: 
       appuser: dbreadonly
       apppass: myDBPassword#%

b. Create a pod with the name of secret-pod.
c. Mount the secret to the pod so that it is available in the path of /etc/secret

</details>

