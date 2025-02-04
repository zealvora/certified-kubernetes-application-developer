
### Commands Used
```sh
kubectl create cronjob --help

kubectl create cronjob demo-cronjob --image=busybox:latest --schedule="* * * * *" -- ping "-c" "5" "google.com

kubectl get pods
```
### Create Manfiest File for CronJob
```sh
kubectl create cronjob demo-cronjob --image=busybox:latest --dry-run=client -o yaml --schedule="* * * * *" -- ping "-c" "5" "google.com
```

### Delete the Resources after Practical
```sh
kubectl delete cronjob demo-cronjob
```