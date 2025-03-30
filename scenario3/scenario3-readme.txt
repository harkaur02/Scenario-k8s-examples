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
