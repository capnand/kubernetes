🧠 Kubernetes Service of Type: ClusterIP (Default)
A Kubernetes Service is an abstraction that defines a logical set of Pods and a stable network endpoint to access them.

🔹NodePort
Scope: External access
Access: Exposes service on a static port on each Node’s IP
Range: Default 30000–32767
Use Case: Quick way to access a service from outside using <NodeIP>:<NodePort>

🛠️ Deployment & Testing Steps\
✅ 1. Apply the configuration:\
kubectl apply -f NodePort.yaml

✅ 2. Check that everything is running:\
kubectl get pods\
kubectl get deployments\
kubectl get svc\
Note the ExternalIp and port(exposed) from the service output.

✅ 3. Test service access using ClusterIP:
Run a test pod or use an existing pod to curl the service:\
curl http://\<ExternalIP>:port

You should see alternating responses:\
Hello from pod <pod-1>\
Hello from pod <pod-2>\
🎯 This proves that the NodePort service is successfully load-balancing traffic across the matching pods. You can access the service externally using the noted URL.