### Challenge - Canary Deployment

#### Tasks: (Complete each step sequentially) 

1. Create a deploymet named `app-v1` that has 5 replicas and uses image of `nginx:latest `

2. Create canary deployment named `app-v2` in a way that 40% traffic goes to `app-v2` and 60% traffic goes to `app-v1`. The canary deployment should image of `httpd:latest`. Total number of Pods in the namespace should only be `5`.

3. Create a service named `app-service`. This service should redirect traffic to the Pods associated with both the deployments. 




