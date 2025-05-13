
### Documentation Referenced:

https://kubernetes.io/docs/tasks/inject-data-application/define-environment-variable-container/

### Create Pod with Env Variable

`pod-env.yaml`
```sh
apiVersion: v1
kind: Pod
metadata:
  name: env-pod
spec:
  containers:
  - name: busybox
    image: busybox:latest
    command: ["sleep","3600"]
    env:
    - name: DB_HOST
      value: "prod-db.kplabs.internal"
    - name: DB_PASS
      value: "notsosecretpassword"
```
```sh
kubectl create -f pod-env.yaml
```
### Verification
```sh
kubectl exec -it env-pod -- sh

echo $DB_HOSt

echo $DB_PASS
```

### Delete the Resource Created

```sh
kubectl delete -f pod-env.yaml
```
