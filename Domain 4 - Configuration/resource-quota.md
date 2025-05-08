### Documentation Referenced:

https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/quota-memory-cpu-namespace/

https://kubernetes.io/docs/concepts/policy/resource-quotas/

### Create Namespace for today's practical
```sh
kubectl create namespace quota-demo
```
### Setting Compute Quota
```sh
nano compute-quota.yaml
```
```sh
apiVersion: v1
kind: ResourceQuota
metadata:
  name: mem-cpu-demo
  namespace: quota-demo
spec:
  hard:
    requests.cpu: "100m"
    requests.memory: "128Mi"
    limits.cpu: "200m"
    limits.memory: "256Mi"
```

```sh
kubectl create -f compute-quota.yaml
```

#### Test 1 - Pod with Exceeded Quota
```sh
nano test-pod-1.yaml
```
```sh
apiVersion: v1
kind: Pod
metadata:
  name: test-pod-fail
  namespace: quota-demo
spec:
  containers:
  - name: demo
    image: busybox
    command: ["sleep", "3600"]
    resources:
      requests:
        cpu: "101m"
        memory: "128Mi"
      limits:
        cpu: "101m"
        memory: "128Mi"
```
```sh
kubectl create -f test-pod-1.yaml
```
#### Test 2 - Pod without Request/Limits
```sh
kubectl run nginx-pod --image=nginx -n quota-demo
```
```sh
kubectl delete -f compute-quota.yaml

```

### Setting Object Quota

```sh
nano object-quota.yaml
```

```sh
apiVersion: v1
kind: ResourceQuota
metadata:
  name: object-count-quota
  namespace: quota-demo
spec:
  hard:
    pods: "1"
    secrets: "3"
    services: "10"
    services.loadbalancers: "2"
```

```sh
kubectl create -f object-quota.yaml
```

#### Test 2 - Launch 3 Pods

```sh
kubectl run test-pod-1 --image=nginx -n quota-demo

kubectl run test-pod-2 --image=nginx -n quota-demo
```

### Delete Resources Created
```sh
kubectl delete pods --all -n quota-demo --force

kubectl delete namespace quota-demo
```