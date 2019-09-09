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

The last URL is based on a custom http server image  with embedded php code highly consuming the CPU.
<pre>

  $x = 0.0001;
  for ($i = 0; $i <= 1000000; $i++) {
    $x += sqrt($x);
  }
  echo "OK!";
  
</pre>

Generate the load to your Apache workload <pre>
</pre>
`while true; do curl https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com; done`{{execute}}<pre>
</pre>
and verify the CPU load `top`{{execute}}. Try to load the process with 60% of the CPU, add extra load if required.

Scale the Apache deployment manually `kubectl scale --replicas=3 deployment/webapp3`{{execute}} and verify the pods `kubectl get deployment webapp3`{{execute}}


Run the autoscaler `kubectl autoscale deployment webapp3 --cpu-percent=30 --min=1 --max=10`{{execute}} and verify the number of pods again `kubectl get hpa`{{execute}}





