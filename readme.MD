# How to use basic Helm

First get your minikube up TBD
then go create a namespace in your kube so you can mess around
go into your namespace

`helm create <name-of-chart>`
boiler plate for your charts/templates
* Helm uses a packaging format called charts. 
  * A chart is a collection of files that describe a related set of Kubernetes resources. A single chart deploys a simple thing or a vry complex thing.
* Templates:
  * 

ignore this
`kubectl create deployment hello-node --image=gcr.io/hello-minikube-zero-install/hello-node`

* A Kubernetes Pod is a group of one or more Containers, tied together for the purposes of administration and networking. 
* A Kubernetes Deployment checks on the health of your Pod and restarts the Pod’s Container if it terminates. 
* Deployments manage the creation and scaling of Pods.


## START HERE

helm install installs a chart archive
'helm install --name <release-name> <directory-of-config-files> --set service.type=NodePort
(ie helm install --name example ./ --set service.type=NodePort) 
* I did this from within my kubectl-hello-world directory so i'm pulling from the current directory i'm in.


Then run the stuff in NOTES 
 ``` export NODE_PORT=$(kubectl get --namespace jenkins-sandbox -o jsonpath="{.spec.ports[0].nodePort}" services example-hello-world)
  
  export NODE_IP=$(kubectl get nodes --namespace jenkins-sandbox -o jsonpath="{.items[0].status.addresses[0].address}")
  echo http://$NODE_IP:$NODE_PORT```

----

kubectl get pods
check your pods > somethings are under the purvey of kubectl

helm ls --all --namespace <namespace>
check your releases 

a lot of weird stuff
If you want to delete a pod
you have to first delete the deployment.
kubectl delete deployments <deployment>

Once you delete your deployment, your release is still there
if you do helm ls you get all your minikubes releases

deleting a release
helm delete --purge <release-name>
(if you just delete it, it's still there you really gotta purge it)

deleting the deployment deletes the pods


you can delete a pod but it'll refresh