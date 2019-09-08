Start minikube and play around with Kubernetes!

`minikube start`{{execute}}

Deploy three simple web applications, one called webapp1, webapp2, webapp3 with a service for each.

Review the deployment definition: `cat deployment.yaml`{{execute}}

Deploy the definitions with `kubectl apply -f deployment.yaml`{{execute}}

The status can be viewed with `kubectl get deployment`{{execute}}

