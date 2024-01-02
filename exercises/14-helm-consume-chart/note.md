# Helm note 

APP version : version du logiciel que le cha

## CHART VERSION :

CHART VERSION fait référence à la version du chart lui-même. C'est la version du package Helm (chart) en tant qu'entité indépendante. Lorsque vous développez ou mettez à jour un chart, vous pouvez incrémenter la CHART VERSION pour indiquer une nouvelle version du chart. Cela permet aux utilisateurs de savoir qu'une nouvelle version du chart est disponible.
Exemple :

```yaml
apiVersion: v2
name: mychart
description: A Helm chart
version: 1.2.3  # C'est la CHART VERSION
```

## APP VERSION :

APP VERSION fait référence à la version de l'application ou du logiciel que le chart déploie. Il spécifie la version de l'application que le chart est conçu pour gérer. Par exemple, si votre chart déploie une application web, APP VERSION pourrait être la version de l'application web elle-même.
Exemple :
```yaml
apiVersion: v2
name: mychart
description: A Helm chart for MyApp
version: 1.2.3
appVersion: 2.5.1  # C'est l'APP VERSION
```

# Commands to know

helm list : pour lister les charts qui sont installer
helm search hub  <name-search> : pour chercher des charts dans le hub
helm repo add URL : pour ajouter un repo en local
helm repo list : pour lister les repo
helm upgrade : pour upgrader les repo
helm install : pour installer un chart.
helm uninstall
helm show values ./repertoire-du-chart : pour afficher les valeurs d'un chart
