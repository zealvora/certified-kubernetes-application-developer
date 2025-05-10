
### Step 1 - Calculate Total Canary Pods

Total Pods Needed = `5`

Canary Percentage = `20%`

Canary Pods = `round(Total Pods × Desired Percentage)`

Final Result = `round(5 x 0.2) = 1`

### Step 2 - Create Deployments
```sh
kubectl create deployment v1-app --image=nginx --replicas=4 --dry-run=client -o yaml > v1-app.yaml
```

Add a label of `env: payments-app` in the manifest file.

```sh
kubectl create deployment v2-app --image=httpd --replicas=1 --dry-run=client -o yaml > v2-canary.yaml
```
Add a label of `env: payments-app` in the manifest file.
```sh
kubectl create -f v1-app.yaml
kubectl create -f v2-canary.yaml
```

### Step 3 - Create Service
```sh
app-service.yaml
```
```sh
apiVersion: v1
kind: Service
metadata:
 name: app-service
spec:
 type: NodePort
 ports:
 - name: http
   port: 80
   targetPort: 80
 selector:
   env: payments-app
```
```sh
kubectl create -f app-service.yaml
```
```sh
kubectl describe service app-service

kubectl get endpoints app-service -o yaml
```

### Step 4 - Testing the Setup
```sh
kubectl run curl-pod --image=alpine/curl -- sleep 36000

kubectl exec -it curl-pod -- sh

for i in $(seq 1 10); do curl -s app-service:80 | grep -E 'works'; done
```

### Step 5 - Delete the Setup
```sh
kubectl delete -f v1-app.yaml

kubectl delete -f v2-canary.yaml

kubectl delete -f app-service.yaml

kubectl delete pod curl-pod
```