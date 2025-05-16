### Challenge - Canary Deployment

1. Create a deploymet named `app-v1` that has 5 replicas and uses image of `nginx:latest `

2. Developers has recently released `app-v2` that uses `httpd:latest` image. Create canary version of the deployment so that 40% traffic goes to `app-v2` and 80% traffic goes to `app-v1`. Total number of Pods should be `5`.

3. Service should be based on ClusterIP with the name of `app-service`




### Solution

Formula for Canary

Total Pods Needed = 5

Canary Percentage = 40%

Canary Pods = round(Total Pods × (Desired Percentage / 100))

Final Result = round(5 x (40/100) = 2



