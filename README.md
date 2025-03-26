# Scenario-k8s-examples
Scenario based Kubernetes examples
Scenario1: Want to deploy an application with 2 or more replica. Not sufficient!
Want to scale that application.
Deployment File - replica 2
Manual Scale Up
autoscale - HPA
Solution Scenario1:
deployment1.yaml
service1.yaml
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
