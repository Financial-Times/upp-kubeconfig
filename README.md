# UPP kubeconfig

## Description
This repo contains:
- a multi-context kubeconfig file for connecting to UPP Kubernetes clusters
- skeleton credentials directories for EU and US clusters
- instructions on how to connect and switch clusters

## Accessing k8s clusters

1. Clone this repository
1. Go to lastpass and search for the following secure notes:
    1. UPP - k8s Prod EU Delivery, Publishing & Neo4j Login credentials
    1. UPP - k8s Prod US Delivery, Publishing & Neo4J Login credentials
1. Download the attachments from the secure notes, and unzip them into in the EU and US credentials directories.
    1. To download attachments, you need to install [LP binary plugin](https://lastpass.com/support.php?cmd=showfaq&id=3206) and access the vault through the add-on/extension.
1. Set the environment variable `KUBECONFIG` to point to the path of the file:
    1. `export KUBECONFIG=~/k8s-aws-delivery-poc/kubeconfig`
1. Set your context:
    1. `kubectl config use-context upp-prod-delivery-eu`

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
