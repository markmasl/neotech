Nginx-proxy and nginx-backend server deployment in kubernetes and helm.

Host: Linux Mint 18
Virtualbox: Version 5.1.36 r122089 (Qt5.6.1)
vagrant: Installed Version: 2.0.4

Guest: Ubuntu 16.04.4 LTS

Packages:

Docker:

Client:
 Version:      18.03.1-ce
 API version:  1.37
 Go version:   go1.9.5
 Git commit:   9ee9f40
 Built:        Thu Apr 26 07:17:20 2018
 OS/Arch:      linux/amd64
 Experimental: false
 Orchestrator: swarm

Server:
 Engine:
  Version:      18.03.1-ce
  API version:  1.37 (minimum version 1.12)
  Go version:   go1.9.5
  Git commit:   9ee9f40
  Built:        Thu Apr 26 07:15:30 2018
  OS/Arch:      linux/amd64
  Experimental: false

How to install: https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1

kubernetes: 

Client Version: version.Info{Major:"1", Minor:"10", GitVersion:"v1.10.2", GitCommit:"81753b10df112992bf51bbc2c2f85208aad78335", GitTreeState:"clean", BuildDate:"2018-04-27T09:22:21Z", GoVersion:"go1.9.3", Compiler:"gc", Platform:"linux/amd64"}
Server Version: version.Info{Major:"1", Minor:"10", GitVersion:"v1.10.0", GitCommit:"fc32d2f3698e36b93322a3465f63a14e9f0eaead", GitTreeState:"clean", BuildDate:"2018-03-26T16:44:10Z", GoVersion:"go1.9.3", Compiler:"gc", Platform:"linux/amd64"}

How to install: https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-via-native-package-management

minikube

version: v0.26.1

How to install: https://github.com/kubernetes/minikube/releases

#minikube start --vm-driver=none

helm 

Client: &version.Version{SemVer:"v2.9.0", GitCommit:"f6025bb9ee7daf9fee0026541c90a6f557a3e0bc", GitTreeState:"clean"}
Server: &version.Version{SemVer:"v2.9.0", GitCommit:"f6025bb9ee7daf9fee0026541c90a6f557a3e0bc", GitTreeState:"clean"}

How to install: https://github.com/kubernetes/helm/releases

Caveats:
due to: https://github.com/kubernetes/helm/issues/3985
kubectl -n kube-system patch deployment tiller-deploy -p '{"spec": {"template": {"spec": {"automountServiceAccountToken": true}}}}'

#helm init

Run deployment:
To install nginx-backend - 

helm install -n nginx-back development/nginx-back

To install nginx-frontend - 

helm install -n nginx-front development/nginx-front

In order to verify that both services (servicea and serviceb) are running please curl from kubernetes host to port 31477:

But before that modify /etc/hosts file:

"minikube ip" serviceb	servicea

change "minikube ip" with real minikube ip address

curl servicea:31477
curl serviceb:31477
