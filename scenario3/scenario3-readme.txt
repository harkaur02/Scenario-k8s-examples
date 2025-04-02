Scenario3: I want to expose an application externally. Check on the possibilities and provide a solution.

Solution:
created deployment2.yaml, service3.yaml and ingress3 .yaml files
In Kubernetes cluster, installed helm chart for nginx ingress controller using following commands:  
  helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
  helm repo ls
  helm repo update
  helm install my-ingress-nginx ingress-nginx/ingress-nginx --version 4.12.1

  kubectl get all
  kubectl apply -f  deployment3.yaml 
  kubectl apply -f service3.yaml 
  kubectl apply -f ingress3.yaml 
  kubectl get all
Now we can access the application externally on our web-browser using External-ip address of the LoadBalancer from ingress-controller:
for example: http://104.155.142.82/test-path

Deleting above installed manifests:
  kubectl delete -f  deployment3.yaml 
  kubectl delete -f service3.yaml 
  kubectl delete -f ingress3.yaml

Deleting helm Repo:
 helm delete my-ingress-nginx
