# ConfigMap

# Define ConfigMap
```bash
  # from a file 
   k create configmap app-config --from-file=./application.yaml

  # Create a new config map named my-config based on folder bar
  kubectl create configmap my-config --from-file=path/to/bar
  
  # Create a new config map named my-config with specified keys instead of file basenames on disk
  kubectl create configmap my-config --from-file=key1=/path/to/bar/file1.txt --from-file=key2=/path/to/bar/file2.txt
  
  # Create a new config map named my-config with key1=config1 and key2=config2
  kubectl create configmap my-config --from-literal=key1=config1 --from-literal=key2=config2
  
  # Create a new config map named my-config from the key=value pairs in the file
  kubectl create configmap my-config --from-file=path/to/bar
  
  # Create a new config map named my-config from an env file
  kubectl create configmap my-config --from-env-file=path/to/foo.env --from-env-file=path/to/bar.env
```

## Use data in configMap as environment variables 
```yaml
      envFrom:
        - configMapRef:
            name: my-configmap-object
```

## Use it as a volume

```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: backend
  name: backend
spec:
  containers:
    - image: nginx:1.23.4-alpine
      name: backend
      volumeMounts:
        - mountPath: "/etc/config"
          name: env-config
      resources: {}
  volumes:
    - name: env-config
      configMap:
        name: app-config
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}

```

## Get the value of a configmap key

```yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: backend
  name: backend
spec:
  containers:
    - image: nginx:1.23.4-alpine
      name: backend
      volumeMounts:
        - mountPath: "/etc/config"
          name: env-config
      resources: {}
      # on cree ici une variable d'env de nom betta dont la valeur est associé à la clé hello du configmap simpleconfig.
      env:
        - name: betta
          valueFrom:
            configMapKeyRef:
              name: simpleconfig
              key: hello
```