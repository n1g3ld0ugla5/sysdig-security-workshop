# Sysdig Security Workshop


Output the primary architecture of the machine it’s run on.
```
dpkg --print-architecture
```

This will be ```armhf``` on a machine running 32-bit ARM Debian <br/>
Ubuntu (or a derivative), ```arm64``` on a machine running 64-bit ARM

## Setting-up the MiniKube Environment

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

If you're not using ```amd64```, check out the MiniKube Install Docs: <br/>
https://minikube.sigs.k8s.io/docs/start/

## Start your cluster

Update the repository:
```
sudo apt-get update
```


Download and install VirtualBox by running:
```
sudo apt-get install virtualbox
```
From a terminal with administrator access (but not logged in as root), run:
```
minikube start --driver=virtualbox
```

Install kubectl
```
sudo snap install kubectl --classic
```

Display list of contexts
```
kubectl config get-contexts 
```

Check that all pods are running:
```
kubectl get pods -A
```

Add the Falco Helm repository and update the local Helm repository cache:
```
helm repo add falcosecurity https://falcosecurity.github.io/charts
helm repo update
```

## Install Falco using Helm:

With kernel module:
```
helm install falco --set tty=true falcosecurity/falco
```

The output is similar to:
```
NAME: falco
LAST DEPLOYED: Mon Oct 24 16:55:51 2022
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
```
