# k8s-aliases
Aliases and helpers to make the work in kubernetes environment easier.

## Prerequisites

Name    | Description       
------- | ------
[kubectl](https://kubernetes.io/docs/tasks/tools/) | The Kubernetes command-line tool that allows you to run commands against Kubernetes clusters. 
[kubectx](https://github.com/ahmetb/kubectx) | Tool to switch between contexts (clusters) on kubectl faster
[kubens](https://github.com/ahmetb/kubectx) | Tool to switch between Kubernetes namespaces (and configure them for kubectl) easily


## Installation and Usage


### Kubernetes commands aliases


To use my kubernetes commands aliases in your daily work with kubernetes, you have to copy the content of file `k8s-commands-aliases-bash`|`k8s-commands-aliases-zsh` into your terminal configuration file.

#### Bash terminal

```
git clone https://github.com/josericardomcastro/k8s-aliases
cat k8s-aliases/k8s-commands-aliases-bash >> ~/.bashrc
source ~/.bashrc
```

#### Zsh terminal

```
git clone https://github.com/josericardomcastro/k8s-aliases
cat k8s-aliases/k8s-commands-aliases-zsh >> ~/.zshrc
source ~/.zshrc
```


#### The logic behind the aliases

Tools:
- `k` - kubectl
- `kx` - kubectx
- `kns` - kubens

Commands verbs:
- `g` - get
- `e` - edit
- `d` - delete
- `desc` - describe

Resources:
- `n` - nodes
- `ns` - namespaces
- `p` - pods
- `dp` - deployments
- `ds` - daemonsets
- `rs` - replicasets
- `ss` - statefulsets
- `s` - services
- `i` - ingress
- `r` - routes
- `sc` - secrets
- `cm` - configmaps
- `pvc` - persistentvolumeclaims
- `pv` - persistentvolume
- `ep` - endpoints
- `e`  - events
- `rq` - resourcequotas
- `lr` - limitranges

Output
- `w` - wide
- `y` - yaml

#### Command usage examples:

Alias | Command description
------ | ------------------- 
kx minikube | Switch to the minikube cluster
kns app-prod | Switch to app-prod namespace
kgp | kubectl get pods
kgpw | kubectl get pods -o wide
kgpy my-pod | kubectl get pods my-pod -o yaml
kgs | kubectl get services
kgsy my-service | kubectl get services my-service -o yaml
kedp app-frontend | kubectl edit deployments app-frontend
kdns ns-test | kubectl delete namespaces ns-test

See the [k8s-commands-aliases-bash](./k8s-commands-aliases-bash) or [k8s-commands-aliases-zsh](./k8s-commands-aliases-zsh) file for the full list of aliases.


### Custom PS1 Prompt for bash

Custom $PS1 (Prompt Statement One) with information about kubernetes and git.

Download the `k8s-git-ps1` file
```
curl -LO https://raw.githubusercontent.com/josericardomcastro/k8s-aliases/main/k8s-git-ps1
```

Add the following command to your `.bashrc` file:

```
[ -f <path-to-file>/k8s-git-ps1 ] && source <path-to-file>/k8s-git-ps1
```


You will see a prompt like this:

![Custom Prompt PS1](./img/prompt-ps1.png "Custom Prompt PS1")

Format: [current time] [k8s context/cluster : k8s namespace] ~current location (git branch name)