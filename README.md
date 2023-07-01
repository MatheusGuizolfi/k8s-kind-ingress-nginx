# k8s-kind-ingress-nginx
Example code to deploy an nginx and httpd deployment into a kind kubernetes cluster using nginx ingress controller

## How to run this example
First you need to create the kubernetes cluster, we are gonna use kind tool to do it.
Make sure you have kind installed in your computer. You can check how to do it in the link below.  
[Kind website](https://kind.sigs.k8s.io/).

Once you have kind installed, you need to run this command:  
`kind create cluster --name lab --config kind/config.yaml`
This command will take some time to finish, so you can get a coffee :)


Once you have your coffee and it is done, you need to install the NGINX ingress resources for kubernetes.   
`kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml`

Steps to setup your test websites:
* First you need to create your deployments and services. `kubectl apply  -f k8s/deployment.yaml -f k8s/service.yaml`  
* Second you need to create the ingress resources. `kubectl apply -f ingress/ingress.yaml`  
* Last step is setup your hosts file, you need to add this code into hosts file:   
  127.0.0.1 example1.com  
  127.0.0.1 example2.com  

**Hosts path for windows: C:\Windows\System32\drivers\etc\hosts**  
**Hosts path for linux based: /etc/hosts**  

Once this command finishes and you setup your hosts, you can go to your browser and access your websites on port 80.  
[example1.com](http://example1.com)  
[example2.com](http://example2.com)
