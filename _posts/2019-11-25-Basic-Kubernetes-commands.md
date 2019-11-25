---
layout: post
title:  "Basic kubectl commands"
date:   2019-11-25
banner_image: master-git.jpg
tags: [kubernetes, kubectl, kubernetes-basics]
---

## Get information about your cluster
{% highlight shell %}
kubectl get nodes
kubectl get deployments
kubectl get pods
kubectl get all
{% endhighlight shell %}

## Run a container
{% highlight shell %}
kubectl run <name> --image=<image> --port=8080
{% endhighlight shell %}

## Get logs from a container
{% highlight shell %}
kubectl logs <pod_name>
{% endhighlight shell %}

## Execute command in container
{% highlight shell %}
kubectl exec <pod_name> env
{% endhighlight shell %}

## Execute interactive shell in the container
{% highlight shell %}
kubectl exec -it <pod_name> bash
{% endhighlight shell %}

## Run Kubernetes API
{% highlight shell %}
kubectl proxy
{% endhighlight shell %}

## Apply changes from a file
{% highlight shell %}
kubectl apply -f <file.yaml>
{% endhighlight shell %}

## Delete everything
{% highlight shell %}
kubectl delete all --all
{% endhighlight shell %}

## Forward a local port to a container in the cluster
{% highlight shell %}
kubectl port-forward <pod_name> <local_port>:<container_port>
{% endhighlight shell %}

# Config file location
{% highlight shell %}
~/.kube/config # Linux/MacOS
%userprofile%\.kube\config # Windows
{% endhighlight shell %}
