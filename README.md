# Scenario-k8s-examples
Scenario based Kubernetes examples
Scenario1:
deployment1.yaml
service1.yaml
k8s commands to scale:
  Manual scaling:
    kubectl scale deployment simple-python-deployment --replicas=3
  HPA autoscaling: 
    kubectl autoscale deploy simple-python-deployment --cpu-percent=50 --min=4 --max=6

