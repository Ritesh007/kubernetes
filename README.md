# Kubernetes ([CHEAT SHEET](https://kubernetes.io/docs/reference/kubectl/cheatsheet/))
## Set the config:
-  aws eks update-kubeconfig --region us-east-1 --name <eks_cluster_name> --no-verify-ssl

## Events
### Get events for name space:
- kubectl -n <name_space> get events


## CPU
### CPU utilization:
- kubectl top node

## cronjob
### Get the cronjob description:
- kubectl -n <name_space> describe cronjob/<cron_job_name> 

## daemonsets
### List daemonsets
- kubectl get daemonsets -n <name_space>

## Config map
### View config map
- kubectl get configmap <config_map_name> -n  <name_space> -o yaml

### List config maps for a namespace
- k get configmaps -n <name_space>

## HPA
### Edit HPA
- example: k edit hpa -n <name_space>

## Restarts and deployment
### Restart rollout 
- example: kubectl rollout restart daemonset/<daemonset_name> -n <name_space>

### Rolling deployment on a nampespace
- example: kubectl rollout restart -n <name_space> deploy

### Edit deployment
- kubectl edit deployment -n <name_space>

## Services
### list services 
- kubectl get svc -n <namespace_name>

## Namespaces
### list namespaces 
- k get namespaces

### Get the jobs for the namespace:
- kubectl get jobs -n <name_space>

## Nodes and Node groups
### Scale nodes
- example: eksctl scale nodegroup --cluster=<cluster_name> --nodes=4 --name=<node_group_name>

### Node group delete, create and update
- eks managed node groups can't be updated
- create example: eksctl create nodegroup -f <node_group_config_yaml_file_location>
- delete example: eksctl delete nodegroup -f <node_group_config_yaml_file_location> --approve

### Delete node
- First drain it: kubectl drain <node name>
- delete node: kubectl delete node <node-name>

## helm
### helm delete
- helm delete <helm_chart_name> -n <namespace>

### helm describe
- helm describe helmrelease <helm_chart_name> -n <namespace>

### Helm upgrade
- 

### helm status
- helm status <helm_chart_name> -n <namespace>

### helm logs
- - kubectl logs -n NAMESPACE-OF-HELM-OPERATOR POD-NAME-OF-HELM-OPERATOR

## pods
### pods describe 
- kubectl describe pod <pod_name> -n <namespace_name>

### Get pods list for name space:
- kubectl get pod -n <name_space>

### Get logs for a pod for name space:
- kubectl logs -n <name_space> <pod_name>

### Wide view for pods
- kubectl get pod -o wide -n <name_space>

### View pod logs
- kubectl logs <pod_name> -n <name_space>

### Port forward
- kubectl -n <name_space> port-forward <pod_name> 14269:14269

### log in to the pod with an interactive bash terminal
- kubectl exec -n <name_space> -it <pod_name> -- /bin/bash

### delete pod
- kubectl delete pod <pod_name> -n <name_space>
