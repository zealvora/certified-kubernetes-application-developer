### Challenge - Requests and Limits

Create a Pod named `cpu-mem-limits` in the  namespace of `limits` that has a single container based on the following specifications

|     Key       |                   Value                   |
|:-------------:|:-----------------------------------------:|
| Container name|                 nginx                     |
|     Image     |            busybox:latest                 |
|   Command     |               sleep for 100 seconds       |
|    CPU Request  |                  20m                    |
|    CPU Limit    |                  80m                    |
|  Memory Request  |                 50Mi                   |
| Memory Limit  |                    256Mi                  |




This container must NOT be restarted after the main command has completed it's operations.


