Minikube Installation Guide for Ubuntu

This guide provides step-by-step instructions for installing Minikube on Ubuntu. Minikube allows you to run a single-node Kubernetes cluster locally for development and testing purposes.
Pre-requisites

    Ubuntu OS
    sudo privileges
    Internet access
    Virtualization support enabled (Check with egrep -c '(vmx|svm)' /proc/cpuinfo, 0=disabled 1=enabled)

Step 1: Update System Packages

Update your package lists to make sure you are getting the latest version and dependencies.

sudo apt update
![image](https://github.com/DineshA055/Kubernetes-starter-initial-setup/assets/101075223/fc3f704e-275b-479d-b67b-b45756057bbc)



image
Step 2: Install Required Packages

Install some basic required packages.

sudo apt install -y curl wget apt-transport-https

![image](https://github.com/DineshA055/Kubernetes-starter-initial-setup/assets/101075223/e0fda89d-28f9-468b-ae49-450f962076bd)


image
Step 3: Install Docker

Minikube can run a Kubernetes cluster either in a VM or locally via Docker. This guide demonstrates the Docker method.

sudo apt install -y docker.io
![image](https://github.com/DineshA055/Kubernetes-starter-initial-setup/assets/101075223/a4b01b4c-8305-4898-b2f5-914e88ce703b)



Start and enable Docker.

sudo systemctl enable --now docker

Add current user to docker group (To use docker without root)

sudo usermod -aG docker $USER && newgrp docker

Now, logout (use exit command) and connect again.
Step 4: Install Minikube

First, download the Minikube binary using curl:

curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

Make it executable and move it into your path:

chmod +x minikube
sudo mv minikube /usr/local/bin/

![image](https://github.com/DineshA055/Kubernetes-starter-initial-setup/assets/101075223/b23ff7ba-ad97-4091-8bd3-b260f0655290)

Step 5: Install kubectl

Download kubectl, which is a Kubernetes command-line tool.

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

Check above image ⬆️ Make it executable and move it into your path:

chmod +x kubectl
sudo mv kubectl /usr/local/bin/

![image](https://github.com/DineshA055/Kubernetes-starter-initial-setup/assets/101075223/b718598a-29db-4103-b066-d89c0a1f682f)

Step 6: Start Minikube

Now, you can start Minikube with the following command:

minikube start --driver=docker

This command will start a single-node Kubernetes cluster inside a Docker container.
Step 7: Check Cluster Status

Check the cluster status with:

minikube status
![image](https://github.com/DineshA055/Kubernetes-starter-initial-setup/assets/101075223/d84139f7-ad58-4f1c-b354-ab7ccf0d3b80)


You can also use kubectl to interact with your cluster:

kubectl get nodes

