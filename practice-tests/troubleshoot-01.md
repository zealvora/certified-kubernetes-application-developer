## Challenge - Troubleshooting

### 1 - Pre-Requisite:

Run the following command to setup the environement

```sh
kubectl create -f sa.yaml
```
### 2 - Question:

A deployment named `mypod-lister` is failing. The pods managed by this deployment are trying to list other pods in the same namespace as part of their startup routine, but they are encountering permission errors.


#### Task:

Fix the issue so that the Pods of the deployment are able to list other pods in the namespace. Verify the pod logs to check this.

#### Hints:

A ServiceAccount named `pod-lister-sa` exists.

A Role named `pod-reader-role` exists in the `dev-namespace` which grants permission to get, watch, and list pods.
