Install OneAgent Operator 

Create the necessary objects for OneAgent Operator. OneAgent Operator acts on its separate namespace dynatrace. It holds the operator deployment and all dependent objects like permissions, custom resources and the corresponding DaemonSet. You can also observe the logs of OneAgent Operator.

Create the namespace

`kubectl create namespace dynatrace`{{execute}}

Get the latest release

`LATEST_RELEASE=$(curl -s https://api.github.com/repos/dynatrace/dynatrace-oneagent-operator/releases/latest | grep tag_name | cut -d '"' -f 4)`{{execute}}

Create resources

`kubectl create -f https://raw.githubusercontent.com/Dynatrace/dynatrace-oneagent-operator/$LATEST_RELEASE/deploy/kubernetes.yaml`{{execute}}

Create K8S secret holding API and PaaS tokens for authenticating to the Dynatrace cluster. Replace API_TOKEN and PAAS_TOKEN fields in `cr.yaml`{{open}} with the values taken from Dynatrace SaaS. 

`kubectl -n dynatrace create secret generic oneagent --from-literal="apiToken=API_TOKEN" --from-literal="paasToken=PAAS_TOKEN"`{{copy}}

Replace API_TOKEN and PAAS_TOKEN fields in `cr.yaml`{{open}} with the values taken from Dynatrace SaaS.

`nano cr.yaml`{{execute}}

Create resources

`kubectl create -f cr.yaml`{{execute}}
