### Documentation Referenced:

https://kubernetes.io/docs/concepts/policy/limit-range/

## Use-Case 1 - Set Default Request/Limits for a Container
```sh
kubectl create namespace lr-demo
```
```sh
nano limitranges-eg1.yaml
```
```sh
apiVersion: v1
kind: LimitRange
metadata:
  name: resource-limits
  namespace: lr-demo
spec:
  limits:
  - default:
      cpu: "100m"
      memory: "128Mi"
    defaultRequest:
      cpu: "50m"
      memory: "64Mi"
    type: Container
```
```sh
kubectl create -f limitranges-eg1.yaml
```
```sh
kubectl get limitrange resource-limits -n lr-demo

kubectl describe limitrange resource-limits -n lr-demo

```
### Test 1 - Deploy a Pod Without Resource Requests/Limits
```sh
nano test-pod-1.yaml
```
```sh
apiVersion: v1
kind: Pod
metadata:
  name: test-pod-1
  namespace: lr-demo
spec:
  containers:
  - name: busybox
    image: busybox
    command: ["sleep", "3600"]
```
```sh
kubectl apply -f test-pod-1.yaml
```
```sh
kubectl get pod test-pod-1 -o yaml -n lr-demo

kubectl delete -f test-pod-1.yaml
```

### Test 2 - Deploy a Pod Over the Limit
```sh
nano test-pod-2.yaml
```
```sh
apiVersion: v1
kind: Pod
metadata:
  name: test-pod-2
  namespace: lr-demo
spec:
  containers:
  - name: busybox
    image: busybox
    command: ["sleep", "3600"]
    resources:
      limits:
        cpu: "102m"
        memory: "130Mi"
```
```sh
kubectl apply -f test-pod-2.yaml
```
```sh
kubectl delete -f test-pod-2.yaml

kubectl delete -f limitranges-eg1.yaml
```
## Use-Case 2 - Set Minimum/Maximum for a Container
```sh
nano limitranges-eg2.yaml
```
```sh
apiVersion: v1
kind: LimitRange
metadata:
  name: stricter-limits
  namespace: lr-demo
spec:
  limits:
  - type: Container
    max:
      cpu: "100m"
      memory: "128Mi"
    min:
      cpu: "30m"
      memory: "50Mi"
```

```sh
kubectl create -f limitranges-eg2.yaml
```
```sh
kubectl describe limitrange stricter-limits -n lr-demo

```

### Test Case 1: Below Minimum Limit
```sh
nano test-pod-3.yaml
```
```sh
apiVersion: v1
kind: Pod
metadata:
  name: pod-below-min
  namespace: lr-demo
spec:
  containers:
  - name: busybox
    image: busybox
    command: ["sleep", "3600"]
    resources:
      limits:
        cpu: "20m"
        memory: "64Mi"
      requests:
        cpu: "20m"
        memory: "64Mi"
```

```sh
kubectl create -f test-pod-3.yaml
```

### Test Case 3: Above Maximum Limit
```sh
nano test-pod-4.yaml
```
```sh
apiVersion: v1
kind: Pod
metadata:
  name: pod-above-max
  namespace: lr-demo
spec:
  containers:
  - name: busybox
    image: busybox
    command: ["sleep", "3600"]
    resources:
      requests:
        cpu: "90m"
        memory: "256Mi"
```

```sh
kubectl create -f test-pod-4.yaml
```

```sh
kubectl delete -f limitranges-eg2.yaml

kubectl delete namespace lr-demo
```
