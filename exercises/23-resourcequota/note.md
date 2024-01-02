# ResourceQuota 

Resource quota c'est un objet permettant de limiter les ressources d'un namespace.
Il peut limiter ainsi le nombre de pod total dans un namespace ainsi que le nombre de service, la quantité de cpu et de mémoire utilisé par l'ensemble des pods.

You can set quota for the total number of certain resources of all standard, namespaced resource types using the following syntax:

    count/<resource>.<group> for resources from non-core groups
    count/<resource> for resources from the core group

Here is an example set of resources users may want to put under object count quota:

    count/persistentvolumeclaims
    count/services
    count/secrets
    count/configmaps
    count/replicationcontrollers
    count/deployments.apps
    count/replicasets.apps
    count/statefulsets.apps
    count/jobs.batch
    count/cronjobs.batch


# Example 

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: app-quota
  namespace: rq-demo
spec:
  hard:
    cpu: "2"
    memory: 500Mi
    pods: "2"
```





ResourceQuota et LimitRange sont deux mécanismes distincts dans Kubernetes qui permettent de définir des politiques de gestion des ressources, mais ils se concentrent sur des aspects différents.

ResourceQuota :

Objectif principal : Contrôler la quantité totale de ressources (CPU, mémoire, nombre de pods, services, etc.) qu'un espace de noms donné peut utiliser dans un cluster Kubernetes.
Utilisation : Vous utilisez ResourceQuota lorsque vous souhaitez définir des limites sur l'ensemble des ressources qu'un espace de noms peut consommer.
Exemple : Vous pourriez définir un ResourceQuota pour limiter le nombre total de pods, services, CPU et mémoire que tous les objets d'un espace de noms peuvent consommer.
LimitRange :

Objectif principal : Définir des contraintes sur les ressources individuelles (CPU, mémoire, etc.) pour chaque objet (pods, conteneurs, etc.) dans un espace de noms.
Utilisation : Vous utilisez LimitRange lorsque vous souhaitez spécifier des limites pour chaque objet individuel au niveau des ressources, tels que la quantité maximale de CPU et de mémoire qu'un pod peut utiliser.
Exemple : Vous pourriez définir une LimitRange pour spécifier que chaque pod ne peut utiliser qu'un certain montant de CPU et de mémoire.
En résumé, ResourceQuota agit au niveau global de l'espace de noms, en imposant des limites sur la quantité totale de ressources, tandis que LimitRange agit au niveau de chaque objet, en spécifiant des limites individuelles pour chaque type d'objet. Ces deux mécanismes peuvent être utilisés ensemble pour appliquer des politiques de gestion des ressources plus complètes dans un cluster Kubernetes.