### Challenge - Deployment Manifest Upgrade

### Background

You are a Kubernetes administrator responsible for maintaining applications on a Kubernetes cluster that has recently been upgraded to the latest version. You've discovered an old deployment manifest file, `old-nginx-deployment.yaml`, which was used to deploy an Nginx application on a much older Kubernetes version (1.15).

This manifest file is no longer compatible with the current Kubernetes API versions and will fail if applied directly.

### Your Task

Your goal is to update the `old-nginx-deployment.yaml` manifest to make it compatible with your current Kubernetes environment. The application's core requirements—running 3 replicas of Nginx image must remain the same. In case if any container errors, save the logs to error-container.txt

`old-deployment.yaml`
```sh
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  template:
    metadata:
      labels:
        run: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
      - name: apache
        image: httpd:latest
        ports:
        - containerPort: 8080
```


