## Challenge:  CronJob

### Context
You’re a Kubernetes engineer and need to implement a recurring maintenance task in the `default` namespace. Write a complete YAML manifest named `kplabs-cronjob.yaml` that meets **all** of the above requirements.

### Requirements

1. **Schedule**
   - Run every 1 minute.

2. **Job Configuration**
   - Image: `busybox`
   - Command / Args:  
     ```shell
     echo "Hello from Kubernetes CronJob!"
     ```

3. **History Limits**  
   Prevent old Jobs/Pods from accumulating in your cluster.
   - Retain only the most recent `3` successful Job records.
   - Retain only the most recent `5` failed Job records.

4. **Timeout**
   - Terminate any Pod that runs longer than `25` seconds  
5. **Delay**
   - If the CronJob controller is down or the cluster is unavailable at the exact schedule time, allow missing runs to be started for up to `30` seconds after their original schedule
5. **Restart Policy**
   - Pods should restart **only on failure**
     

