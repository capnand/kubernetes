# 1. Create app1 Deployment and Service\
kubectl apply -f IngressDeployment1.yaml\
check deployment and svc\
kubectl get svc\
use ClusterIP to test deployment and svc\

# 2. Create app2 Deployment and Service\
kubectl apply -f IngressDeployment2.yaml\
check deployment and svc\
kubectl get svc\
use ClusterIP to test deployment and svc\

# 3. Install NGINX Ingress Controller (bare-metal)\
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.3.0/deploy/static/provider/baremetal/deploy.yaml\

# 4. Wait for ingress controller pods to be ready and create Ingress Resource\
kubectl apply -f IngressRule.yaml\
kubectl get ingress\
kubectl describe ingress\

# 6. Get NodePort of ingress controller (port 80)\
kubectl get svc -n ingress-nginx\

# 7. Test access using curl (replace 30710 with your actual NodePort)\
curl localhost:30710/app1\
curl localhost:30710/app2
