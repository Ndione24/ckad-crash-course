# The ultimate Guide

Nous allons travailler avec le Dockerfile suivant
* access to docker cheatsheet
*                                                                                                    
## Docker


```bash
# -d : run in background
docker run -d -p 8080:8080 java-hello-world:1.0.0

# see logs
$ docker logs b0ee04accf078ea7c...

# connect to the container
$ docker exec -it b0ee04accf078ea7c... bash 

# Tag a image
docker tag my-image ndione/my-image:1.0.1

# Publisj
docker login --username=[name]
docker push [dom]/image_name:x.x.x

# Backup image 
docker save -o [archive-name] [image-name] ## docker -o ndione-image.tar ndione-im

# Load a image from an archive
docker load [archive-name] ## docker load ndione-image.tar 

# build and create two tags at the same time 
$ sudo docker build -t registry.killer.sh:5000/sun-cipher:latest -t registry.killer.sh:5000/sun-cipher:v1-docker .

## Some commands in podman

podman build
podman run                                                                          

# create tag in podman

# see logs with podman

```



## HELM
https://helm.sh/docs/intro/cheatsheet/

Example complet:
```bash
helm install <name> <chart>                           # Install the chart with a name
helm install <name> <chart> --namespace <namespace>   # Install the chart in a specific namespace
helm install <name> <chart> --set key1=val1,key2=val2 # Set values on the command line (can specify multiple or separate values with commas)
helm install <name> <chart> --values <yaml-file/url>  # Install the chart with your specified values
helm install <name> <chart> --dry-run --debug         # Run a test installation to validate chart (p)
helm install <name> <chart> --verify                  # Verify the package before using it 
helm install <name> <chart> --dependency-update       # update dependencies if they are missing before installing the chart
helm uninstall <name>  

# -all: show all releases without any filter applied, because by default, helm ls display only the running release
helm ls -a 

```

update
set values
see values 


## GREP 

### Options:
* -i
* -C
* -A 

## POD

### Running commands in pod 
## JOB and CRONJOB

## VOLUME : ephemeral, persistence

## init container

## Deployment rollout
undo 
history
...
## Label annotation

## API DEPRECATIOn
## Pod metrics
## HPA 
## PROb

## CRD

## Service account
* secret use service acc
* another type of service account
* 
## Resource quota, limitrange


## Config map 

* as environmment key

```yaml
  # on cree ici une variable d'env de nom betta dont la valeur est associé à la clé hello du configmap simpleconfig.
      env:
        - name: betta
          valueFrom:
            configMapKeyRef:
              name: simpleconfig
              key: hello
```


* as volume

```yaml
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
```


* as env : envfrom
  use data in configMap as environment variables
```yaml
      envFrom:
        - configMapRef:
            name: my-configmap-object
```


## Secret
* as environmment key
* as volume
* as env : envfrom


## Security context

## Service

## Ingress


## network policy
permet de definir le traffic entrant et sortant des pods.

### Ingress
pour le traffic entrant

### Egress pour le traffic sortant
pour le traffic sortant

### Example

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: test-network-policy
  namespace: default
spec:
  podSelector:
    matchLabels:
      role: db
  policyTypes:
    - Ingress
    - Egress
  ingress:
    - from:
        - ipBlock:
            cidr: 172.17.0.0/16
            except:
              - 172.17.1.0/24
        - namespaceSelector:
            matchLabels:
              project: myproject
        - podSelector:
            matchLabels:
              role: frontend
      ports:
        - protocol: TCP
          port: 6379
  egress:
    - to:
        - ipBlock:
            cidr: 10.0.0.0/24
      ports:
        - protocol: TCP
          port: 5978
```
* Ingress:
```yaml
  ingress:
    - from:
        - ipBlock:
            cidr: 172.17.0.0/16
            except:
              - 172.17.1.0/24
        - namespaceSelector:
            matchLabels:
              project: myproject
        - podSelector:
            matchLabels:
              role: frontend
      ports:
        - protocol: TCP
          port: 6379
```
Dans cette exemple plusieurs sources sont autorisées. Ces sources doivent obligatoirement passées via le port 6379 en TCP.
Si on avait un "-" au niveau du keyword **ports** , le traffic serait autorisait des trois sources ou tous pods qui passerait via le port  6379 en TCP. 

![networkPolicyAND&OR.png](..%2F..%2FDocuments%2Fdev_life%2FDEV%2FExcalidraw%2FnetworkPolicyAND%26OR.png)


* Egress 
Dans cette exemple, les sorties du traffic des pods ayant le label: **role: db** dans le namespace default passe via 10.0.0.0/24 et de port 5978 en TCP.

### AND & OR
![networkPolicyAND&OR.png](..%2F..%2FDocuments%2Fdev_life%2FDEV%2FExcalidraw%2FnetworkPolicyAND%26OR.png)

### Example

des examples deny et allow pour tout un namespace est dispo dans la doc.