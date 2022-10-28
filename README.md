# Sysdig Security Workshop


Output the primary architecture of the machine it’s run on.
```
dpkg --print-architecture
```

This will be ```armhf``` on a machine running 32-bit ARM Debian <br/>
Ubuntu (or a derivative), ```arm64``` on a machine running 64-bit ARM

#### Creating a K8s environment on an EC2 instance

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


## Installing Falco

Normal workflow <br/>
https://falco.org/docs/getting-started/installation/ <br/>
<br/>
Apple Silicon workflow <br/>
https://falco.org/blog/falco-apple-silicon/

## Using Falco

This will trigger the deployment of Falco on your Kubernetes cluster. <br/>
The falco-driver-loader init container will perform all the steps required to build the eBPF probe <br/>
(hint: the kernel headers are already included in the VM) as you can see from the output snippet:
```
kubectl logs -n falco $(kubectl get po -n falco -l app.kubernetes.io/name=falco -o name) -c falco-driver-loader
```

And then, the falco pod should be running:
```
kubectl logs -n falco $(kubectl get po -n falco -l app.kubernetes.io/name=falco -o name) -c falco
```

display list of contexts
```
kubectl config get-contexts                          
```

display the current-context
```
kubectl config current-context 
```

set the default context to my-cluster-name
```
kubectl config use-context my-cluster-name           
```

## Running Falco

These commands should apply to all environments: <br/>
https://falco.org/docs/getting-started/running/

You can view the Falco logs using journalctl.
```
journalctl -fu falco
```
