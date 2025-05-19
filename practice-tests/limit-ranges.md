
## Exercise - Limit Ranges and NodePort Service

1. Create a LimitRange object in the `test` namespace that enforces maximum memory of `500Mi`. The default cpu request should be `25m`.

2. Create a Pod named `half-mem-pod` in the `test` namespace with a single container based on following specification.

|     Key       |                   Value                   |
|:-------------:|:-----------------------------------------:|
| Container name|                 nginx                     |
|     Image     |              nginx:latest                 |
| Memory Limit  | Half of the test namespace memory limit   |

3. Make sure that the Pod restarts only in-case of Failure.

4. Create a service named `nodeport-service` that has NodePort of `32000` and sends request to the `half-mem-pod` on Port `80`.

