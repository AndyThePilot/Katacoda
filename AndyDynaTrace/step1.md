We will use minikube to control the K8S cluster, start it with `minikube start`{{execute}}

Deploy three simple web applications - called webapp1, webapp2, webapp3 with a service for each. Review the deployment definition: `cat deployment.yaml`{{execute}}

Deploy those definitions with `kubectl apply -f deployment.yaml`{{execute}}

The status can be viewed with `kubectl get deployment`{{execute}} and with `kubectl get pods`{{execute}} 

Enable Nginx-based Ingress extension in minikube: `minikube addons enable ingress`{{execute}}

Review the routing `cat ingress.yaml`{{execute}}

Create Ingress in the clsuter `kubectl create -f ingress.yaml`{{execute}}

Verify that the ingress controller is running `kubectl get pods -n kube-system`{{execute}}

Verify which service host a given URL:

https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/apple<pre>
</pre>https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/banana<pre>
</pre>
https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com<pre>
</pre>

The last URL is based on a  to a custom http server image  with embedded php code highly consuming the CPU, we gonna use it alter one.

Generate the load to your workload to <pre>
</pre>
`while true; do curl https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com; done`{{execute}}<pre>
</pre>
and verify the load `top`{{execute}}. Try to load the Apache pod with 60% of the CPU, add extra load if required.








