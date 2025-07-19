🧠 Kubernetes Service of Type: ClusterIP (Default)
A Kubernetes Service is an abstraction that defines a logical set of Pods and a stable network endpoint to access them.

🔹 ClusterIP Service:
Scope: Internal only (within the cluster)
Access: Accessible only from other pods or nodes inside the cluster
Use Case: Internal communication between microservices (e.g., backend ↔ DB)

🛠️ Deployment & Testing Steps
✅ 1. Apply the configuration:
kubectl apply -f clusterip.yaml

✅ 2. Check that everything is running:
kubectl get pods
kubectl get deployments
kubectl get svc
Note the ClusterIP from the service output.

✅ 3. Test service access using ClusterIP:
Run a test pod or use an existing pod to curl the service:
curl http://<ClusterIP>
🧠 You’ll see the default NGINX index.html page.

✅ 4. Modify index.html in each pod to identify them:
kubectl exec -it <pod-1> -- /bin/bash
cd /usr/share/nginx/html/
echo "POD-1 of Service type CLUSTER-IP" > index.html
exit

kubectl exec -it <pod-2> -- /bin/bash
cd /usr/share/nginx/html/
echo "POD-2 of Service type CLUSTER-IP" > index.html
exit

✅ 5. Test round-robin load balancing:
Run the following command multiple times inside a test pod:
curl http://<ClusterIP>

You should see alternating responses:
POD-1 of Service type CLUSTER-IP
POD-2 of Service type CLUSTER-IP
🎯 This proves that the ClusterIP service load-balances traffic across the matching pods but useful for internal process.
