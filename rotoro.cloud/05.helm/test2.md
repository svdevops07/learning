# Customisation
## Scenario1
```
helm install my-release bitnami/wordpress \
--set wordpressBlogName="Helm for Beginners" \
--set wordpressEmail="admin@rotoro.cloud"

kubectl get deploy my-release-wordpress -oyaml

helm install my-release bitnami/wordpress \
--set my-values.yaml
```

## Scenario2
```
helm pull bitnami/wordpress
helm pull bitnami/wordpress --untar

--> change values.yaml
helm install my-release ./wordpress
```