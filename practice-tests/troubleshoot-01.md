## Challenge - Troubleshooting

### 1 - Pre-Requisite:

Run the following command to setup the environement

```sh
kubectl create -f https://raw.githubusercontent.com/zealvora/certified-kubernetes-application-developer/refs/heads/master/practice-tests/sa.yaml
```
### 2 - Question:

Application in the Pods that are part of the deployment named `mypod-lister` are failing. Application in the pods managed by this deployment are trying to list other pods in the same namespace as part of their startup routine, but they are encountering permission errors.


#### Task:

Fix the  issue preventing the application within the `mypod-lister` deployment's pods from listing other pods in the namespace. Validate the fix by inspecting the pod logs.


#### Hints:

A ServiceAccount named `pod-lister-sa` exists. Use this service account for the application Pods.

A Role named `pod-reader` exists in the `dev-namespace` which grants permission to get, watch, and list pods.
