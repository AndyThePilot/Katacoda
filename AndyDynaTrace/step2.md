Install OneAgent Operator 

Create the necessary objects for OneAgent Operator. OneAgent Operator acts on its separate namespace dynatrace. It holds the operator deployment and all dependent objects like permissions, custom resources and the corresponding DaemonSet. You can also observe the logs of OneAgent Operator.

Create the namespace

`kubectl create namespace dynatrace`{{execute}}

Get the latest release

`LATEST_RELEASE=$(curl -s https://api.github.com/repos/dynatrace/dynatrace-oneagent-operator/releases/latest | grep tag_name | cut -d '"' -f 4)`{{execute}}

Create resources

`kubectl create -f https://raw.githubusercontent.com/Dynatrace/dynatrace-oneagent-operator/$LATEST_RELEASE/deploy/kubernetes.yaml`{{execute}}

Create K8S secret holding API and PaaS tokens for authenticating to the Dynatrace cluster. Replace API_TOKEN and PAAS_TOKEN fields in the line below with the values taken from Dynatrace SaaS -> Deploy Dynatrace -> Start installation -> Linux

`kubectl -n dynatrace create secret generic oneagent --from-literal="apiToken=API_TOKEN" --from-literal="paasToken=PAAS_TOKEN"`{{copy}}

Download the customer resources file cr.yaml

`curl -o cr.yaml https://raw.githubusercontent.com/Dynatrace/dynatrace-oneagent-operator/$LATEST_RELEASE/deploy/cr.yaml`{{execute}}


Replace API_TOKEN and PAAS_TOKEN fields in `cr.yaml`{{open}} with the values taken from Dynatrace SaaS.

`nano cr.yaml`{{execute}}

Create resources

`kubectl create -f cr.yaml`{{execute}}

Check if OneAgent pods are running

`kubectl get pods -n dynatrace`{{execute}}

Go to the Dynatrace SaaS and verify the host monitoring
