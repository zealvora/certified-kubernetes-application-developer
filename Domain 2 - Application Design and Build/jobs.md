
### Command Used in Video

```sh
kubectl create job --help

kubectl create job ping-job --image=busybox:latest -- ping "-c" "5" "google.com"
```

### Verification of Job and Pods
```sh
kubectl get pods
kubectl logs <pod-name>
kubectl describe job ping-job
```

### Testing Use-Case of Deletion of Pod
```sh
kubectl delete job ping-job

kubectl create job ping-job --image=busybox:latest -- ping "-c" "100" "google.com"

kubectl get pods

kubectl delete pod <pod-name>

kubectl get pods
```
### Generate Manifest File For Job
```sh
kubectl create job ping-job --image=busybox:latest --dry-run=client -o yaml -- ping "-c" "100" "google.com" > jobs.yaml
```

### Delete the Resources Created
```sh
kubectl delete job ping-job
```