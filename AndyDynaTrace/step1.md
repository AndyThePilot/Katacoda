We will use minikube to control the K8S cluster, start it with `minikube start`{{execute}}

Deploy three simple web applications - called webapp1, webapp2, webapp3 with a service for each.

Review the deployment definition: `cat deployment.yaml`{{execute}}

Deploy the definitions with `kubectl apply -f deployment.yaml`{{execute}}

The status can be viewed with `kubectl get deployment`{{execute}} and with `kubectl get pods`{{execute}} 

