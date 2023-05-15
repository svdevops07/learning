# HELM 


## BASIC COMMANDS

helm install wordpress

helm upgrade wordpress

helm rollback wordpress

helm uninstall wordpress


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
