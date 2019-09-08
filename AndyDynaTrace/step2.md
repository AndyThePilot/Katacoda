Install OneAgent Operator 

Create the necessary objects for OneAgent Operator. OneAgent Operator acts on its separate namespace dynatrace. It holds the operator deployment and all dependent objects like permissions, custom resources and the corresponding DaemonSet. You can also observe the logs of OneAgent Operator.

`kubectl create namespace dynatrace`{{execute}}

`LATEST_RELEASE=$(curl -s https://api.github.com/repos/dynatrace/dynatrace-oneagent-operator/releases/latest | grep tag_name | cut -d '"' -f 4)`{{execute}}

`kubectl create -f https://raw.githubusercontent.com/Dynatrace/dynatrace-oneagent-operator/$LATEST_RELEASE/deploy/kubernetes.yaml`{{execute}}

`kubectl -n dynatrace logs -f deployment/dynatrace-oneagent-operator`{{execute}}

Create the secret holding API and PaaS tokens for authenticating to the Dynatrace cluster. The name of the secret is important in a later step when you configure the custom resource (.spec.tokens). In the following code-snippet the name is oneagent. Be sure to replace API_TOKEN and PAAS_TOKEN with the values explained above.

`kubectl -n dynatrace create secret generic oneagent --from-literal="apiToken=API_TOKEN" --from-literal="paasToken=PAAS_TOKEN"`{{execute}}

`AndyDynaTrace/cr.yaml`{{open}}

`$ curl -o cr.yaml https://raw.githubusercontent.com/Dynatrace/dynatrace-oneagent-operator/$LATEST_RELEASE/deploy/cr.yaml`{{execute}}
