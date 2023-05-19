# Helm
## Customisation
### Scenario1
```
helm install my-release bitnami/wordpress \
--set wordpressBlogName="Helm for Beginners" \
--set wordpressEmail="admin@rotoro.cloud"

kubectl get deploy my-release-wordpress -oyaml

helm install my-release bitnami/wordpress \
--set my-values.yaml
```

### Scenario2
```
helm pull bitnami/wordpress
helm pull bitnami/wordpress --untar

--> change values.yaml
helm install my-release ./wordpress
```


## App's Lifecycle

```
helm install balancer bitnami/nginx --version 9.7.0

kubectl get po
kubectl describe po balancer-nginx-xyz

helm upgrade balancer bitnami/nginx

helm history balancer bitnami/nginx

helm rollback balancer 1

kubectl get secrets             # save old Revisions

kubectl get secrets sh.helm.release.v1.balancer.v1 -o jsonpath='{.data.release}' | base64 -d | base64 -d | gunzip -c | jq -r .manifest                          # see Revision v1
```