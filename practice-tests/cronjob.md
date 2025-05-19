## Challenge:  CronJob

### Context
You’re a Kubernetes engineer and need to implement a recurring maintenance task in the `default` namespace. Write a complete YAML manifest named `kplabs-cronjob.yaml` that meets **all** of the above requirements.

### Requirements

1. **Schedule**
   - Run every 1 minute.

2. **Job Configuration**
   - Image: `busybox`
   - Command:  
     ```shell
     echo "Hello from Kubernetes CronJob!"
     ```

3. **History Limits**  
   Prevent old Jobs/Pods from accumulating:
   - Retain only the most recent `3` successful Job records.
   - Retain only the most recent `5` failed Job records.

4. **Timeout**
   - Terminate any Pod that runs longer than `25` seconds  

5. **Restart Policy**
   - Pods should restart **only on failure**  

