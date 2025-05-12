### Documentation Referenced:

https://kubernetes.io/docs/concepts/workloads/controllers/job/

### Create Job with backoffLimit of 3

`backoffLimit.yaml`

```sh
apiVersion: batch/v1
kind: Job
metadata:
  name: failing-job
spec:
  template:
    spec:
      containers:
      - name: always-fail
        image: busybox
        command: ["sh", "-c", "exit 1"]
      restartPolicy: Never
  backoffLimit: 3
```

```sh
kubectl create -f backoff-limit.yaml
```

### Verification
Wait for a minute or two, there should be a total of 4 failed pods.

```sh
kubectl get pods
```

### Delete the Resources Created
```sh
kubectl delete -f backoffLimit.yaml
```