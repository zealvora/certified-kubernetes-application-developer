## Challenge: Deployment Updates

### Context
You are managing a Kubernetes Deployment for a web application with `3` replicas. Your application is critical, and you want to minimize downtime during a rolling update, but you also want the update to finish quickly.

### Requirement

1. At least `2` Pods must be available at all times during the rolling update.

2. You want to allow `1` extra Pod to be created above the desired replica count during the update for faster rollout.

### Task:

Create a deployment named `kplabs-deployment` using image of `nginx:latest` that satisfies the requirements.

Once the deployment is running, update the image of the deployment from `nginx:latest` to `httpd:latest`
