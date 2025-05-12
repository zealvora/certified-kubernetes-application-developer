### Documentation Referenced:

https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/#jobs-history-limits

### Example 1 - Create CronJob with successfulJobsHistoryLimit as 3

`cronjob-success-history-3.yaml`
```sh
apiVersion: batch/v1
kind: CronJob
metadata:
  name: success-custom
spec:
  schedule: "*/1 * * * *"
  successfulJobsHistoryLimit: 3
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: pass
            image: busybox
            args:
            - ping
            - -c2
            - "google.com"
          restartPolicy: Never
```
```sh
kubectl create -f cronjob-success-history-3.yaml
```

Wait for a 3-4 minutes 
```sh
kubectl get jobs

kubectl get pods

kubectl delete -f cronjob-history-3.yaml
```


### Example 1 - Create CronJob with failedJobsHistoryLimit as 3

`cronjob-fail-history-3.yaml`
```sh
apiVersion: batch/v1
kind: CronJob
metadata:
  name: failjob-default
spec:
  schedule: "*/1 * * * *"
  failedJobsHistoryLimit: 2
  jobTemplate:
    spec:
      backoffLimit: 0
      template:
        spec:
          containers:
          - name: fail
            image: busybox
            args:
            - /bin/sh
            - -c
            - "exit 1"
          restartPolicy: Never
```

```sh
kubectl create -f cronjob-fail-history-3.yaml
```

Wait for a 3-4 minutes 
```sh
kubectl get jobs

kubectl get pods

kubectl delete -f cronjob-fail-history-3.yaml
```