# Sysdig Security Workshop


Output the primary architecture of the machine it’s run on.
```
dpkg --print-architecture
```

This will be ```armhf``` on a machine running 32-bit ARM Debian <br/>
Ubuntu (or a derivative), ```arm64``` on a machine running 64-bit ARM

## Creating the Environment

Update the repository:
```
sudo apt-get update
```

Run the below command:
```
curl https://raw.githubusercontent.com/n1g3ld0ugla5/CIS-Compliant-Kubernetes/main/master.sh | bash
```

After this step, check that all pods are created but not running <br/>
This is because we have yet to install our networking layer:

```
kubectl get pods -A
```

If you joined the nodes from the above steps, you should be able to confirm their status:

```
kubectl get nodes -o wide
```

## Creating a zero-trust network architecture

Project Calico is a Pure Layer 3 Approach to Virtual Networking for Highly Scalable Data Centers. <br/>
https://github.com/projectcalico <br/>
<br/>

This also packages the admission controller which is required to prevent workloads from being created <br/>
https://github.com/open-policy-agent/gatekeeper


```
curl https://raw.githubusercontent.com/n1g3ld0ugla5/CIS-Compliant-Kubernetes/main/tools.sh | bash
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
