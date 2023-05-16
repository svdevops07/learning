# HELM 


## BASIC COMMANDS
### Help
```
helm --help
helm repo --help
helm repo update --help

helm repo list
helm repo update
```
### Repos
```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-release bitnami/wordpress

helm list
helm status my-release

helm uninstall my-release
```

helm install wordpress

helm upgrade wordpress

helm rollback wordpress

helm uninstall wordpress


helm install <release_name> <chart_name>	- for many Releases

helm install site-1 bitnami/wordpress		- Release-1

helm install site-2 bitnami/wordpress           - Release-2


## INSTALLATION

cluster + kubectl

### v1 
```
$ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
$ chmod 700 get_helm.sh
$ ./get_helm.sh
```

### v2
```
curl -L https://get.helm.sh/helm.v3.8.0-linux-amd64.tar.gz -o ./helm-v3.tar.gz
tar -zxvf helm-v3.tar.gz
mv linux-amd64/helm /usr/local/bin/helm
```

### v3
```
sudo snap install helm --classic
```

### v4 Ubuntu / Debian
```
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```

## Autocomplete
### Loading completions in your current shell session:
```
source <(helm completion bash)
```

### Loading completions for every new session, execute once:
```
helm completion bash > /etc/bash_completion.d/helm
```