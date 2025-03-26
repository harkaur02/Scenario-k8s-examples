# Scenario-k8s-examples
Scenario based Kubernetes examples
Scenario1: Want to deploy an application with 2 or more replica. Not sufficient!
Want to scale that application.
Deployment File - replica 2
Manual Scale Up
autoscale - HPA
Solution Scenario1:
created deployment1.yaml
created service1.yaml
Kubernetes commands:
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl edit service/python1appservice  /*here change service type from ClusterIP to LoadBalancer*/
kubectl get all

k8s commands to scale:
  Manual scaling:
    kubectl scale deployment simple-python-deployment --replicas=3
  HPA autoscaling: 
    kubectl autoscale deploy simple-python-deployment --cpu-percent=50 --min=4 --max=6

Scenario2: Pods aren’t in running in running state. May be it is in Crashloopback Off/Failed. What will you do to debug.
Solution Scenario2: 
created deployment2.yaml
created service2.yaml
Note: in order to make Crashloopback Off/Failed, image version is set to v2 which doesn't even exist. (To make it working change image version v2 to v1 in line 19 (eg. image: thethymca/python-flask-sample-app:v2))
Kubernetes commands:
  kubectl get ns
  kubectl get all
  kubectl create ns scenario2
  kubectl apply -f deployment.yaml -n scenario2
  kubectl apply -f service.yaml -n scenario2
  kubectl get all -n scenario2
  kubectl logs pod/scenario2-deployment-5f5bdb66b-c7f2v -n scenario2
  kubectl describe pod/scenario2-deployment-5f5bdb66b-c7f2v -n scenario2
commands to delete above deployment and service:
  kubectl delete -f deployment2.yaml -n scenario2
  kubectl delete -f service2.yaml -n scenario2

Scenario3: I want to expose an application externally. Check on the possibilities and provide a solution.
Solution Scenario3: 
There are two ways to expose an application externally:
1. using LoadBalancer service
2. using Ingress service
I will be using type ingress to expose my app externally for this Scenario3 example.

