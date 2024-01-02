# Using label and annotation

definition

```bash
# delete a label
$ kubectl label pod backend env-

# search label in values
$ kubectl get pods -l 'team in (shiny, legacy)',env=prod --show-labels
```