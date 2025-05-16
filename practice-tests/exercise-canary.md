### Challenge - Canary Deployment

#### Tasks: (Complete each step sequentially) 

1. Create a deploymet named `app-v1` that has 5 replicas and uses image of `nginx:latest `

2. Developers has recently released `app-v2` that uses `httpd:latest` image. Create canary version of the deployment so that 40% traffic goes to `app-v2` and 80% traffic goes to `app-v1`. Total number of Pods in the default namespace should be `5`.

3. A service named `app-service` should redirect traffic to the Pods associated with both the deployments. 




