
#### Create a new deployment
```sh
kubectl create deployment demo-deployment --image=nginx
```
```sh
kubectl get deployment demo-deployment -o yaml
```
#### Set a new image to Deployment
```sh
kubectl set image deployment demo-deployment nginx=httpd
```
#### Edit Deployment
```sh
kubectl edit deployment demo-deployment
```
Set the maxSurge=0

#### Verify the Result
```sh
kubectl set image deployment demo-deployment nginx=httpd
```
```sh
kubectl get pods
```