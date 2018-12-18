== Kubernetes Operator-Framework Workshop

SDEE team / service delivery ecosysteam enablement team

slides - 

Matt Dorn / John McKienze

== Operator framework

What is operator ?
 - resource (pod / config map / route)
 - contoller (deamonset / replicaset / deployment)
 - knowledge (Installing / Scale / self-healing / clean-up / back up )

Site Reliability Engineer

- oc proxy
- curl locahost:8001
- curl http://localhost:8001/api/v1 | jq .resources[].name

oc - just use API  commands

============================================

http://workshop.coreostrain.me/exercises/

============================================

kubernetes - etcd kubernetes shared state (persisted) - similar to reddis (keyvalue)

- Custom resource definition (CRD)

Kubernetes Controller

Observe -> analyze (compare current state to desired state) -> Act (cuurent state meet desired state)

EXPORT kubernetes API

== Operators = one click enabled


Support operators:

Chat
#kubernetes-operators
#forum-operators
Mailing List
operator-framework
GitHub Issues
operator-sdk
OpenShift Commons - Operator Framework
Every third Friday of the month at 12pm EST


== Kubernetes Overview

1. The project - github.com / kubernetes
2. community deployment
3. product OCP
4. Service

Dashboard
CLI
SDK/Client Libraries
Helm - package manager

All this things use Kubernetes API

Kubectl / oc - CLI tools


k8s auth

Client go -> Clientset -> Dynmic Client -> REST client ->

Watch is long-running GET

oc get pods -w

oc run busybox --image=busybox --restart=Never

Kubernetes Resource = declarative API with well defined schema

ReplicaSet:
- apiVersion
- kind

TypeMeta^ GVK(Group, Version, Kind )

metadata:
 name:
 namespace
 annotations:

ObjectData

Spec: 

Status:

oc explain deployments.spec --api-version="apps/v1beta1"

oc api-versions

Watch -> GET !

oc get pods -o yaml

resourceVersion: "45196" -> oc get pods

delete resource in kubernetes -> SIGTERM -> SIGKILL (grace termination period)

##Labels / Selectors 
grouping & relationships

oc get pods -L

oc get pods --all-namespaces

oc get nodes

oc get nodes -o wide


## ReplicaSet former known as ReplicaController (Reconsiliation loop)

oc scale replicaset myfirstreplicaset --replicas=6

kubelet talks with docker

https://github.com/kubernetes/kubernetes/blob/master/cmd/kube-controller-manager/app/controllermanager.go#L362 (SourceGraph)

oc -n kube-system logs kube-controller-manager-localhost -f

== Primary resources / secondary resources

- Primary => Che
- Secondary => 

== Deamosets 

pod on each node but handle their own scheduling instead of the default scheduler

primary resource = deamonset
secondary = pods, nodes

Rolling update / Recreate == deployment strategies  / maxUnavailability / MaxSurge = 100%

Blue-Green Deployments

== Deployments vs. DeploymentConfig

== oc get crd

oc adm policy  --as system:admin add-cluster-role-to-user cluster-admin developer

== etcd

== Operator

- sa / role / rolebinding

== Reconsiler Pattern 

- use data structure for all inputs & ouputs
- data structure is immutable
- keep the resource map simple
- ?
