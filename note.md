# Alias 

```bash
alias k=kubectl

$ kubectl config set-context <context-of-question> --namespace=<namespace-of-question>
$ kubectl config use-context <context-of-question>

```
# Docker 

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
podman logs <container_name>
```


```yaml
# Update image 
 k set image deployment/nginx nginx=nginx:1.23.4=
```


# Goal
20 --> 27

3 days kubernetes
ckad exam github
plural sight
book kube study exam
25 excercices
38h kubernetes dyma
# Tool 
helm, jq

kubectl top : pour les metrics

Capabilities ???
revoir le cours de jordan sur kubernetes.

Show what you can, share it, life is temporary, enjoy it.

Demain inchallah: faire le new test.

Label, annotation, StorageClass
# Done 


* [x] 1 : docker 
* [x] 2 : pod
* [x] 20 :crd 
* [x] 21 :rbac
* [x] 22 :request 
* [x] 23 : resourcequota
* [x] 24 : limitrange
* [x] 25 : configmap
* [x] 26 : secret
* [x] 27 : secutity context
* [x] 28 : service
* [x] 29 : trouble service
* [x] 30 : ingress
* [x] 31 : network policies (retry it)
* [x] 14 : helm
* [ ] 15 : Ne fait pas parti de l'examen
* [x] 16 : API deprecation (search another exercises)
* [x] 17 : probe (à memoriser)
* [x] 18 : metrics server
* [x] 19 : troubleshoot pod 
* [x] 04 : cron job (à memoriser)
* [x] 05 : empty dir
* [x] 06 : persistence volume
* [x] 07 : init container
* [x] 08 : adapter 
* [x] 09 : ambassador pattern
* [x] 10 : label annotation
* [x] 11 : rollout 
* [x] 12 :
* [x] 13 :




Complete example project : creer un namespace qui reprendra les bases 
pv
pvc
deploy
secret
config
HPA
initContainer (say hello)
job
cronjob
service
ingress
emptydir
limit range
network policies
resourcequota
service account




## faire 11 12 13
Revoir le tout
Resumé
revoir exam prep test
Revoir exo plural sight
Resumé simple
get exo and correction in web

Do exam prep


## reployment
Default startegy is rollingUpdate. We also have Recreate startegy

.spec.strategy specifies the strategy used to replace old Pods by new ones. .spec.strategy.type can be "Recreate" or "RollingUpdate". "RollingUpdate" is the default value.
Recreate Deployment
All existing Pods are killed before new ones are created when .spec.strategy.type==Recreate.
we can have zero time deployment with recreate strategy because kubernetes will kill all existing pods before creating the news




## Test killer sh
Team Neptune needs a Job template located at /opt/course/3/job.yaml. This Job should run image busybox:1.31.0 and execute sleep 2 && echo done. It should be in namespace neptune, run a total of 3 times and should execute 2 runs in parallel.

Start the Job and check its history. Each pod created by the Job should have the label id: awesome-job. The job should be named neb-new-job and the container neb-new-job-container.


```yaml

```
* If a Secret belongs to a ServiceAccont, it'll have the annotation kubernetes.io/service-account.name. Here the Secret we're looking for is neptune-secret-1
  https://www.youtube.com/watch?v=ynmCK48nkCI