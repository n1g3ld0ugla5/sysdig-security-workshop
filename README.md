# Sysdig Security Workshop


Output the primary architecture of the machine it’s run on.
```
dpkg --print-architecture
```

This will be ```armhf``` on a machine running 32-bit ARM Debian <br/>
Ubuntu (or a derivative), ```arm64``` on a machine running 64-bit ARM

# Setting-up the MiniKube Environment

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube
```

If you're not using ```amd64```, check out the MiniKube Install Docs: <br/>
https://minikube.sigs.k8s.io/docs/start/

