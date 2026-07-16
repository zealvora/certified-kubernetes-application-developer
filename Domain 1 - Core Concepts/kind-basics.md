
## Part 1 - Simpler Approach

### Deploy Simple Kubernetes Cluster Using Kind
```sh
kind create cluster

kind create cluster --name kplabs-k8s
```
### Verify Cluster
```sh
kind get clusters
```
### Delete Cluster
```sh
kind delete clusters kind kplabs-k8s
```


## Part 2- Advanced Approach

If you decide you need to test these multi-node scenarios, you don't use the default command.

Create a new file named `kind-config.yaml` with following contents

```sh
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
```
```sh
kind create cluster --config kind-config.yaml
```

```sh
kind delete clusters kind
```

## Part 3 - Cluster for Upcoming Videos

Make sure you have a simple Kubernetes cluster configured for upcoming set of videos.

```sh
kind create cluster --name kplabs-k8s
```