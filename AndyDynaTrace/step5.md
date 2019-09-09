Explore the Dynatrace SaaS platform and test the autoscaling.

Log in to your Dynatrace trial, explore the K8S processes CPU consumption. Find the Apache PHP pod and verify its resource consumption.

Generate the load to your workload to <pre>
</pre>
`while true; do curl https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com; done`<pre>
</pre>
and verify the load again. Try to load the Apache pod with 60% of the CPU, add extra load if required.





