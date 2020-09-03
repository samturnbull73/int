1. [Docker](https://github.com/samturnbull73/int/blob/master/NOTES.md#docker), [Sample Docker File](https://github.com/samturnbull73/Simple-DevOps-Project/blob/master/Jenkins_Jobs/Dockerfile.txt)
2. [CI/CD](https://github.com/samturnbull73/int/blob/master/NOTES.md#ci-and-cd)

## Ansible
1. [Ansible Directory](https://github.com/samturnbull73/ansible-directory#about-this-repo)
2. [Simple Docker Ansible Playbook](https://github.com/samturnbull73/Simple-DevOps-Project/blob/master/Jenkins_Jobs/simple-docker-project.yml)
3. [Deploy on a docker container using Ansible](https://github.com/samturnbull73/Simple-DevOps-Project/blob/master/Jenkins_Jobs/Deploy_on_Container_using_Ansible.MD#deploy-on-a-docker-container-using-ansible)
4. [Sample ansible file for http](https://github.com/samturnbull73/int/blob/master/NOTES.md#ansible-sample-http-installation-file)

## Kubernetes
1. [Integration Kubernetes with Jenkins](https://github.com/samturnbull73/Simple-DevOps-Project/blob/master/Kubernetes/Integrating_Kubernetes_with_Jenkins.MD#integration-kubernetes-with-jenkins)
2. [Azure Kubernetes](https://github.com/samturnbull73/int/blob/master/NOTES.md#kubernetes-on-azure)

### Docker

| Tag           | Description | Example |
| ------------- | ------------- |----|
| MAINTAINER  | who is maintaining this Dockerfile  | |
| FROM | tell who is maintaining this Dockerfile | |
| CMD |  The command executed when running a Docker container based on this image |  | 
| COPY | install software and copy files into the image. | |
| ADD | same way as the COPY instruction, tar or pull file from over http/s  | |
| ENV |  set an environment variable inside the Docker image  | |
| RUN | execute command line executables, executed during build time, exe once | |
| ARG | lets you define an argument which can be passed to Docker when you build the Docker image | ARG tcpPort=8080 |
| WORKDIR | specifies what the working directory should be inside the Docker image | |
| EXPOSE | opens up network ports in the Docker container to the outside world | EXPOSE   8080/tcp 9999/udp |
| VOLUME | creates a directory inside the Docker image which you can later mount a volume (directory) to from the Docker host  | VOLUME   /data|
| ENTRYPOINT | application or command that is executed when the Docker container is started up | |
| HEALTHCHECK | health check interval --interval=60s, Health Check Start Period --start-period=300s, Health Check Retries --retries=5| |

### CI and CD

CI when a developer checks in his code into git, with the help of git-hook, a build will be triggered in Jenkins, which will test for build
we do unit testing like jmeter(they had their own custom unit testing tool) 

In CD- we do build, static code analysis using Sonarcube, deploy the artefact to Artificatory and do Functional testing using Selenium

If it passes the test, we deploy the code to next environment from Artifactory as do further testing

We do performance testing in Preprod environment

For performance testing, you may use tools like Appdynamics, New Relic, we were using load runner.

#### Plugin 
1. GitHub Plugin
2. Command Agent Launched plugin
3. Maven Integration plugin
4. Maven Invoker plugin and configure Maven path
5. Public over SSH
6. Deploy to container
7. Creditials(stores credentials) and 
8. Credentials Binding plugin(store them in environment variable)

### Ansible Sample http installation file
![Sample ansible file for http](https://github.com/samturnbull73/int/blob/master/images/ansible_http.png?raw=true)

### Kubernetes on Azure

The app.yml and service.yml file are added to a zip file added as a resource to this chapter

You can use the below commands to work with Azure Kubernetes

// Create a **new resource group**

az group create --name kubernetes --location eastus

// Create a **new Kubernetes cluster**

az aks create --resource-group kubernetes --name companycluster --node-count 1 --enable-addons monitoring --generate-ssh-keys

// Install the **kubectl tool**

az aks install-cli --install-location=./kubectl

// Get the **credentials of the cluster**

az aks get-credentials --resource-group kubernetes --name companycluster

// Get the **nodes running in the cluster**

kubectl get nodes

// Apply the **application configuration file**

kubectl apply -f app.yml

// Apply the **service configuration file**

kubectl apply -f service.yml

// Get the list of **services running in Kubernetes**

kubectl get services

Two ways networking on Azure is setup, 

**kubenet plugin(default)**, PODs have different IP addresses

**Azure Container Networking Interface plugin** -> every pod in the cluster gets an IP address from the subnet. These make the pods directly accessible.
