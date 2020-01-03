### Question 1: Service

<details><summary>Expand The Question </summary>
<p>

Create a deployment named kplabs-service. The deployment should have three replicas and the image should be based on nginx. Create a service based on NodePort. The service port should be 8080. Website should be accessible from port 32001 from all hosts.

</details>

### Question 2: Troubleshoot Service

<details><summary>Expand The Question </summary>
<p>

Apply the following manifest file in your Kubernetes enviornement:

https://github.com/zealvora/myrepo/blob/master/demo-files/troubleshoot-service.yaml

Verify if you are able to access website by referencing to the service IP address from a busybox pod. If it's not working, fix the issue so that the website is downloadable when following command is ran: wget [SERVICE-IP]:8080

</details>


### Question 3: Namespace

<details><summary>Expand The Question </summary>
<p>
Create a pod named kplabs-namespace. The pod should be part of namespace kplabs.
The pod should make use of redis image. Expose port 6379.
</details>


