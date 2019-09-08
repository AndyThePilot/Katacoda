Configure K8S cluster monitoring

Create a service account and cluster role for accessing the K8S API

`wget https://www.dynatrace.com/support/help/codefiles/kubernetes/kubernetes-monitoring-service-account.yaml`{{execute}}

`kubectl apply -f kubernetes-monitoring-service-account.yaml`{{execute}}

Store the bearer token

`kubectl get secret $(kubectl get sa dynatrace-monitoring -o jsonpath='{.secrets[0].name}' -n dynatrace) -o jsonpath='{.data.token}' -n dynatrace | base64 --decode`{{execute}}

Open Dynatrace Saas -> Monitor -> Kubernetes

Paste the URL https://[[HOST_SUBDOMAIN]]-8443-[[KATACODA_HOST]].environments.katacoda.com and the bearer token.




