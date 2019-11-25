---
layout: post
title:  "Basic kubectl commands"
date:   2019-11-25
banner_image: master-git.jpg
tags: [kubernetes, kubectl, kubernetes-basics]
---

{% highlight shell %}
# Get information about your cluster
kubectl get nodes
kubectl get deployments
kubectl get pods
kubectl get all

# Run a container
kubectl run <name> --image=<image> --port=8080

# Get logs from a container
kubectl logs <pod_name>

# Execute command in container
kubectl exec <pod_name> env

# Execute interactive shell in the container
kubectl exec -it <pod_name> bash

# Run Kubernetes API
kubectl proxy

# Apply changes from a file
kubectl apply -f <file.yaml>
kubectl delete all --all

# Forward a local port to a container in the cluster
kubectl port-forward <pod_name> <local_port>:<container_port>

# Config file location
~/.kube/config

{% endhighlight shell %}
