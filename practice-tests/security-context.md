### Challenge - Security Context

Deploy a Pod from the `busybox:latest` image. Pod should be named `security-pod` and it must be created in the default namespace. The Pod must meet the following security requirements:

1. Run all containers with UID of `1001`

2. Run all containers with UID of `2002`

3. Pods should not allow any privilege escalation.
