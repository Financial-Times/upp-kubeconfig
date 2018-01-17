# UPP kubeconfig

## Description
This repo contains:
- a multi-context kubeconfig file for connecting to UPP Kubernetes clusters
- skeleton credentials directories for EU and US clusters
- instructions on how to connect and switch clusters

## Install kubectl
Instructions are [here](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

For MacOS users, [installing kubectl via Homebrew](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-homebrew-on-macos) is preferred.

## First time configuration
1. Clone this repository
1. Go to lastpass and search for the following secure notes:
    - UPP - k8s Prod EU Delivery, Publishing & Neo4j Login credentials
    - UPP - k8s Prod US Delivery, Publishing & Neo4J Login credentials
1. Download the attachments from the secure notes, and unzip them into in the EU and US credentials directories.
    - To download attachments, you need to install [LP binary plugin](https://lastpass.com/support.php?cmd=showfaq&id=3206) and access the vault through the add-on/extension.
1. Create a `.kube` directory in your home, if it doesn't already exist:  
    `mkdir -p ~/.kube`
1. Copy the config & credentials into your `.kube` directory:  
    `cp -r config credentials-* ~/.kube`

## Accessing k8s clusters
Set your context to the appropriate cluster:
```
kubectl config use-context upp-prod-delivery-eu
```

Available clusters are:
```
upp-prod-delivery-eu
upp-prod-publish-eu
upp-prod-neo4j-eu
upp-prod-delivery-us
upp-prod-publish-us
upp-prod-neo4j-us
```

Test your setup by running:
```
kubectl cluster-info
```

You should get something like:
```
$ kubectl cluster-info
Kubernetes master is running at https://upp-prod-delivery-eu-api.ft.com
Heapster is running at https://upp-prod-delivery-eu-api.ft.com/api/v1/namespaces/kube-system/services/heapster/proxy
KubeDNS is running at https://upp-prod-delivery-eu-api.ft.com/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
$
```

To switch to a different cluster, re-run the use-context command:
```
kubectl config use-context upp-prod-publish-us
```

## [OPTIONAL] Display the current context in your shell prompt
If you're switching between clusters regularly, you may want to show the current context in your shell prompt.

See here for examples:
https://pracucci.com/display-the-current-kubelet-context-in-the-bash-prompt.html  
https://github.com/eyalev/kubectl-context-prompt  
http://blog.cloud66.com/kubernetes-and-gcloud-bash-prompts/  

