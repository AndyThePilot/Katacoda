We will use minikube to control the K8S cluster, start it with `minikube start`{{execute}}

Deploy three simple web applications - called webapp1, webapp2, webapp3 with a service for each. Review the deployment definition: `cat deployment.yaml`{{execute}}

Deploy those definitions with `kubectl apply -f deployment.yaml`{{execute}}

The status can be viewed with `kubectl get deployment`{{execute}} and with `kubectl get pods`{{execute}} 

Enable Nginx-based Ingress extension in minikube: `minikube addons enable ingress`{{execute}}

Review the routing `cat ingress.yaml`{{execute}}

Create Ingress in the clsuter `kubectl create -f ingress.yaml`{{execute}}

Verify that the ingress controller is running `kubectl get pods -n kube-system`{{execute}}

Verify which service host a given URL:

<pre>http://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/apple
http://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/banana
http://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/something
</pre>





