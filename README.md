There are 2 deployments with nginx and configmaps for them:
  deployment-nginx.yaml
  deployment-nginx-canary.yaml
  configmap-main.yaml
  configmap-canary.yaml

Nodeport for each deployment:
  nodeport.yaml
  nodeport-canary.yaml
  
And ingresses:
  ingress.yaml
  ingress-canary.yaml
  
After applying all yamls we can go to minikube ssh and check that 30% of queries go to canary deployment:
  for i in {1..10}; do curl http://127.0.0.1/; echo ; done

Also we can reach canary deployment using header canary:always:
  for i in {1..10}; do curl -H "canary:always" http://127.0.0.1; echo ; done
