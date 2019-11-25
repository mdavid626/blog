---
layout: post
title:  "Basic kubectl commands"
date:   2019-11-25
banner_image: basic-kubectl.jpg
tags: [kubernetes, kubectl, kubernetes-basics]
---

The following commands should help you get started with [Kubernetes](https://kubernetes.io/) and [kubectl](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands).

## Get information about your cluster
List the resources created in your cluster.
{% highlight shell %}
kubectl get nodes
kubectl get deployments
kubectl get pods
kubectl get all
{% endhighlight shell %}

## Run a container
It's like `docker run` with a little bit different syntax.
{% highlight shell %}
kubectl run <name> --image=<image> --port=8080
{% endhighlight shell %}

## Get logs from a container
{% highlight shell %}
kubectl logs <pod_name>
{% endhighlight shell %}

## Execute command in container
This executes the `env` command in the container and displays the result.
{% highlight shell %}
kubectl exec <pod_name> env
{% endhighlight shell %}

<!--more-->

## Execute interactive shell in the container
This will execute `bash` in the container and you'll be able to type commands interactively from your terminal.
{% highlight shell %}
kubectl exec -it <pod_name> bash
{% endhighlight shell %}

## Run Kubernetes API proxy
This will run a local HTTP service, which will proxy request to the cluster. Using this service you can access the Kubernetes API, so you can control the cluster using HTTP requests.
{% highlight shell %}
kubectl proxy
{% endhighlight shell %}

## Apply changes from a file
Describe what needs to be done in a `.yaml` file and let Kubernetes do the rest.
{% highlight shell %}
kubectl apply -f <file.yaml>
{% endhighlight shell %}

## Delete everything from your cluster
If you no longer need the resources you created in your cluster you can drop them with this command.
{% highlight shell %}
kubectl delete all --all
{% endhighlight shell %}

## Forward a local port to a container in the cluster
Either you expose the containers port and then you can access it from your local machine or you can use this command to temporarily forward traffic from your local machine to the container.
{% highlight shell %}
kubectl port-forward <pod_name> <local_port>:<container_port>
{% endhighlight shell %}

## Show version of kubectl
{% highlight shell %}
kubectl version --short
{% endhighlight shell %}

## Config file location
{% highlight shell %}
~/.kube/config # Linux/MacOS
%userprofile%\.kube\config # Windows
{% endhighlight shell %}
