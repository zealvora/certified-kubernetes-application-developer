## Challenge: Probes

### Context
You need to create a Deployment that runs your web application and configure both liveness and readiness probes so that Kubernetes can verify the health and readiness of your Pods before routing traffic.

### Requirement

1. Create a Deployment named `kplabs-probes` that uses `2` replicas.
2. Container image should be `nginx:latest`
3. Expose container port `8081`.

Make sure deployment is created before proceeding with the next steps.

4. Configure a readiness probe that:
     - Performs an `HTTP GET` on path `/healthz`
     - Port should be same as the Container Port.
     - Has initialDelaySeconds: `15`
     - Has failureThreshold: `3`

5. Configure a livenessProbe that
    - Performs an `HTTP GET` on path `/healthz`
    - Port should be same as the Container Port.
    - Has initialDelaySeconds: `15`
    - Has periodSeconds: `10`
    - Has failureThreshold: `5`
