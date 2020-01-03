### Question 1: Resource Quota 

<details><summary>Expand The Question </summary>
<p>

Create a pod named kplabs-quota. The pod should have following configuration:

 a. Should run with nginx image.
 b. It should use maximum of 512 MiB of memory.
 c. It should use maximum of 2 core CPU.
 d. The POD should require a minimum of 128 MiB of memory before it is scheduled.
 
 </details>

### Question 2: Secrets

<details><summary>Expand The Question </summary>
<p>

Create a secret named kplabs-secret. The secret should have content where user=admin and pass=12345. Create a pod from the nginx image. Mount the secret as environment variables in the pod.

 </details>
