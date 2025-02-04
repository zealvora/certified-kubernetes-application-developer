### Base Manifest File Used

```sh
apiVersion: batch/v1
kind: Job
metadata:
  name: ping-job-manifest
spec:
  template:
    metadata:
    spec:
      containers:
      - command:
        - ping
        - -c
        - "100"
        - google.com
        image: busybox:latest
        name: ping-job
      restartPolicy: Never
```


### Final Manifest File

jobs.yaml

```sh
apiVersion: batch/v1
kind: Job
metadata:
  name: ping-job-manifest
spec:
  activeDeadlineSeconds: 30
  template:
    metadata:
    spec:
      containers:
      - command:
        - ping
        - -c
        - "100"
        - google.com
        image: busybox:latest
        name: ping-job
      restartPolicy: Never
```

```sh
kubectl apply -f jobs.yaml

kubectl get pods
```
