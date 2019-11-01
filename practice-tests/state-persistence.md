### Question 1: Secrets and Enviornement Variables
<details><summary>Expand The Question </summary>
<p>

Andrew works as a database administrator and has generated set of credentials that will be used by the application to connect to the database. Instead of giving the credentials to developers to hard-code in their application, he has requested security team to create a secret and mount it as enviornement variable to the application containers.

a. Create a secret name db-creds which has following data: 
       user: dbreadonly
       pass: myDBPassword#%
       
b. Create a pod from nginx image.

c. Mount the secret to the POD in such a way that the contents of database user is available in form of DB_USER enviornement variable and database password is available in form of DB_PASSWORD enviornement variable inside the container.

</details>

### Question 2: Secrets and Volumes

<details><summary>Expand The Question </summary>
<p>


a. Create a secret name app-creds which has following data: 
       appuser: dbreadonly
       apppass: myDBPassword#%

b. Create a pod with the name of secret-pod.
c. Mount the secret to the pod so that it is available in the path of /etc/secret

</details>

### Question 3:  ConfigMaps

<details><summary>Expand The Question </summary>
<p>
       
Following is the configuration file for an application. Create a ConfigMap based on the configuration file. Mount the configmap in such a way that the configuration file is accessible in the location of /etc/app.config

    defaults
        mode http
        timeout connect 5000ms
        timeout client 50000ms
        timeout server 50000ms
</details>

 ### Question 4: POD Security Policies
 
<details><summary>Expand The Question </summary>
<p>
 
 Create a POD named kplabs-security with the following configuration:
 
   a. The primary process should run with the userid of 1000
   
   b. The primary group id should be 2000
   
</details>
