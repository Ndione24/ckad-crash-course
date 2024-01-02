# RBAC

## Create a service account
service account is ....

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  annotations:
  name: my-serviceaccount
  namespace: t23
```




Admission controller

Role 
    k create role -h # ...
        options : verb, resource

Role binding

After creating a role, we can binding to a specific user or account

clusterRole
ServiceAccount



resource unit kubernetes
cpu, memory