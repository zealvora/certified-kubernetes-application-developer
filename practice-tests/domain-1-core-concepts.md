### Question 1: Creating Single Container Pods 

<details><summary>Expand The Question </summary>
<p>


a. Create a pod with the name of kplabs-nginx. 

b. The pod should be launched from an image of ``` mykplabs/kubernetes:nginx``` 

c. The name of the container should be mycontainer

</details>

### Question 2: Commands and Arguments

<details><summary>Expand The Question </summary>
<p>


Create a pod with the name of kplabs-cmdargs. The pod should be launched from an image of ```busybox``` . The name of the container should be cmdcontainer. Both the container image's CMD and ENTRYPOINT instruction should be overridden. 

The container should start with ```sleep``` command and argument of ```3600```
</details>

### Question 3: Exposing Ports for PODS

<details><summary>Expand The Question </summary>
<p>

Create a pod with the name of kplabs-ports. The pod should be launched from an image of ```nginx``` . The name of the container should be nginx. Expose Port ```80``` for the POD.

</details>


### Question 4: Arguments

<details><summary>Expand The Question </summary>
<p>

Create a pod named ```kplabs-logging```

The Pod should have a container running from the nginx image with the following arguments:

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

Once POD is created, connect to the POD and verify the contents of ```/var/log/1.log``` and ```/var/log/2.log```

</details>
