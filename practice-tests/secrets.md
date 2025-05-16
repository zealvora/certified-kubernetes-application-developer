## Challenge - Secrets and Pod Environment Variables

### Question 
You are tasked with deploying a new application that requires sensitive configuration data to be securely managed. This data should be made available to the application container as environment variables.

### Tasks:

1. Create a new Kubernetes Secret named `app-secret` in the default namespace.

2. The Secret should contain the following key-value pairs:
```sh
DB_USERNAME: admin
DB_PASSWORD: supersecret
```

3. Create a new Pod named `my-app-pod` in the default namespace.

4. The Pod should use the `nginx:latest` image.

5. Configure the Pod to expose the `DB_USERNAME` and `DB_PASSWORD` values from the `app-secret` Secret as environment variables named `APP_DB_USER` and `APP_DB_PASS` respectively, within the container.

6. Ensure the Pod is running and verify that the environment variables are correctly set inside the container.