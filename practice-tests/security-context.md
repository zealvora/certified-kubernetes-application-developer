### Challenge - Security Context

Deploy a Pod from the `busybox:latest` image. Pod should be named `security-pod` and it must be created in the default namespace. The container should run `sleep` command for `3600` seconds.The Pod must also meet the following security requirements:

1. Run all containers with UID of `1001`

2. Run all containers with GID of `2002`

3. Pods should not allow any privilege escalation.
