
## Exercise - Limit Ranges

1. Create a LimitRange object in the `test` namespace that enforces maximum memory of `500Mi`. The default cpu request should be `25m`.

2. Create a Pod named `half-mem-pod` in the `test` namespace with a single container based on following specification.

|     Key       |                   Value                   |
|:-------------:|:-----------------------------------------:|
| Container name|                 nginx                     |
|     Image     |            busybox:latest                 |
|   Command     |        sleep for 100 seconds              |
| Memory Limit  | Half of the test namespace memory limit   |


3. Make sure that the Pod restarts only in-case of Failure.

