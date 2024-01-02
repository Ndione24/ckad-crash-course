Dans les objets LimitRange de Kubernetes, le champ type peut prendre les valeurs suivantes en fonction du contexte dans lequel il est utilisé :

## type: Container :

Ce type est utilisé pour spécifier des limites de ressources par conteneur. Les limites définies sous ce type s'appliquent individuellement à chaque conteneur à l'intérieur d'un pod.
Exemple :

```yaml
apiVersion: v1
kind: LimitRange
metadata:
name: container-resource-limits
spec:
limits:
- type: Container
  max:
   memory: 512Mi
   cpu: 200m
  min:
   memory: 256Mi
   cpu: 100m
```

## type Pod 
Ce type est utilisé pour spécifier des limites de ressources qui s'appliquent à l'ensemble du pod. Les limites définies sous ce type sont appliquées collectivement à tous les conteneurs du pod.
Exemple :

```yaml
apiVersion: v1
kind: LimitRange
metadata:
name: pod-limit-range-sample
spec:
limits:
- type: Pod
  default:
   memory: 1Gi
   cpu: 500m
  max:
   memory: 2Gi
   cpu: 1
```
## type: PersistentVolumeClaim :

Ce type est utilisé pour spécifier des limites sur les ressources liées aux volumes persistants (Persistent Volume Claims) utilisés par les pods.
Exemple :

```yaml
apiVersion: v1
kind: LimitRange
metadata:
name: pvc-limit-range-sample
spec:
limits:
- type: PersistentVolumeClaim
  max:
  storage: 1Gi
```
Chaque type définit le contexte dans lequel les limites de ressources s'appliquent, que ce soit au niveau du conteneur, du pod ou des volumes persistants. Les limites définies sous chaque type spécifié sont alors appliquées conformément aux règles définies dans la LimitRange.

Lorsqu'on definit un limitrange dans un namespace, le default request et le default limit seront configurés automatiquement dans les pods de ce namespace.
Sauf si ces derniers en definissent eux meme mais en restant dans l'intervale min et max du limitrange.
