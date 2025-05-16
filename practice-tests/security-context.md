### Challenge - Security Context

Deploy a busybox pod named `security-pod` in the default namespace that meets the following security requirements:

1. Run all containers with UID of `1001`

2. Run all containers with UID of `2002`

3. Pods should not allow any privilege escalation.
