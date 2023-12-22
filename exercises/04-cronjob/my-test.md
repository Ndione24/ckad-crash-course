## Cron Job
Depuis la doc avec -h de kubectl:

```bash
kubectl create cronjob my-job --image=busybox --schedule="*/1 * * * *"

# Create a cron job with a command
kubectl create cronjob my-job --image=busybox --schedule="*/1 * * * *" -- date
```
Examples:
# Create a cron job


* Directly 
kubectl create cronjob myjob --image=busybox --schedule="* * * * *" -- /bin/sh -c 'echo "Current date: $(date)"'

### Get the yaml before
```bash
  kubectl create cronjob my-job --image=busybox --schedule="* * * * *" --dry-run=client  -o yaml > mycc.yaml -- echo "Current date: $(date)" 

  cat mycc.yaml
  apiVersion: batch/v1
kind: CronJob
metadata:
  creationTimestamp: null
  name: my-job
spec:
  jobTemplate:
    metadata:
      creationTimestamp: null
      name: my-job
    spec:
      template:
        metadata:
          creationTimestamp: null
        spec:
          containers:
          - command:
            - echo
            - "Current date: $(date)" # replace default date by $(date)
            image: busybox
            name: my-job
            resources: {}
          restartPolicy: OnFailure
  schedule: '* * * * *'
status: {}

  # Create the resource
  k create -f mycc.yaml
  
```
