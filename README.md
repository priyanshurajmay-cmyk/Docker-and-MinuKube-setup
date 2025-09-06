# Hosting a website in EC2 AWS, SSL certification can't be initiated due to an unknown error
## Steps for Ec2 server Deployment

Quick Deployment Steps
1. Log in to AWS Console: Go to the AWS Management Console and sign in.
2. Navigate to EC2: Search for and select EC2 from the services list.
3. Launch Instance: Click the Launch Instance button.
4. Choose AMI & Type: Select your desired AMI (e.g., Ubuntu, Amazon Linux) and an Instance Type (e.g., t2.micro).
5. Configure: Leave most settings as default, but ensure Auto-assign Public IP is enabled if needed.
6. Add Storage & Tags: Adjust the storage size and add a Name tag to identify your instance.
7. Configure Security Group: Set up firewall rules to allow traffic on specific ports like SSH (22) and HTTP (80).
8. Review & Launch: Confirm your settings, then click Launch.
9. Select Key Pair: Choose an existing key pair or create a new one to securely connect to your instance.
![](https://github.com/priyanshurajmay-cmyk/Docker-and-MinuKube-setup/blob/main/docker%20screenshot-20250906T132528Z-1-001/docker%20screenshot/Screenshot%202025-09-06%20184901.png)
![](https://github.com/priyanshurajmay-cmyk/Docker-and-MinuKube-setup/blob/main/docker%20screenshot-20250906T132528Z-1-001/docker%20screenshot/Screenshot%202025-09-06%20184710.png)

# DOCKER.md
# docker-install


### Quick Install
```bash
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```
---

install packages:
```bash
sudo apt update
sudo apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    jq
```

Add Docker’s official GPG key:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

setup repository:
```bash
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker Engine:
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

Add your user to the docker group:
```bash
sudo usermod -aG docker $USER
```

### Docker Compose

download the current stable release of Docker Compose:
```bash
COMPOSE_VERSION=$(curl -s "https://api.github.com/repos/docker/compose/tags" | jq -r '.[0].name')
sudo curl -L "https://github.com/docker/compose/releases/download/${COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose
```

Apply executable permissions to the binary:
```bash
sudo chmod +x /usr/local/bin/docker-compose
```
# PULL IMAGES 
```bash
 docker pull hello-world
```
```bash
 docker pull nginx
```
```bash
docker pull ubuntu/apache2
```
# SEE IMGAGES/INSPECT
```bash
 docker images
```
```bash
 docker inspect
```
```bash
  docker ps
```
# PORT FORWADING 
```bash
docker run --name mynginxl -p 80:80 -d nginx
```
```bash
docker run --name myapache -p 80:80 -d ubuntu/apache2
```
# KILLING IMAGE
```bash
docker kill mynginxl
```
![](https://github.com/priyanshurajmay-cmyk/Docker-and-MinuKube-setup/blob/main/docker%20screenshot-20250906T132528Z-1-001/docker%20screenshot/Screenshot%202025-09-06%20175243.png)


# To install the latest minikube stable release on x86-64 Linux using binary download:

``curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64``

![](https://github.com/priyanshurajmay-cmyk/Docker-and-MinuKube-setup/blob/main/docker%20screenshot-20250906T132528Z-1-001/docker%20screenshot/Screenshot%202025-09-06%20175218.png)

# 2.Start your cluster
From a terminal with administrator access (but not logged in as root), run:
```minikube start```
# Interact with your cluster
If you already have kubectl installed (see documentation), you can now use it to access your shiny new cluster:

```kubectl get po -A```
Alternatively, minikube can download the appropriate version of kubectl and you should be able to use it like this:

```minikube kubectl -- get po -A```
You can also make your life easier by adding the following to your shell config: (for more details see: kubectl)

```alias kubectl="minikube kubectl --"```
Initially, some services such as the storage-provisioner, may not yet be in a Running state. This is a normal condition during cluster bring-up, and will resolve itself momentarily. For additional insight into your cluster state, minikube bundles the Kubernetes Dashboard, allowing you to get easily acclimated to your new environment:

```minikube dashboard```

![](https://github.com/priyanshurajmay-cmyk/Docker-and-MinuKube-setup/blob/main/docker%20screenshot-20250906T132528Z-1-001/docker%20screenshot/Screenshot%202025-09-06%20175438.png)
![](https://github.com/priyanshurajmay-cmyk/Docker-and-MinuKube-setup/blob/main/docker%20screenshot-20250906T132528Z-1-001/docker%20screenshot/Screenshot%202025-09-06%20182615.png)
# minikube dashboard with no errors
![](https://github.com/priyanshurajmay-cmyk/Docker-and-MinuKube-setup/blob/main/docker%20screenshot-20250906T132528Z-1-001/docker%20screenshot/Screenshot%202025-09-06%20184041.png)

#killing Everything

##Manage your cluster
Pause Kubernetes without impacting deployed applications:

```minikube pause```
Unpause a paused instance:

```minikube unpause```
Halt the cluster:

```minikube stop```
Change the default memory limit (requires a restart):

```minikube config set memory 9001```
Browse the catalog of easily installed Kubernetes services:

```minikube addons list```
Create a second cluster running an older Kubernetes release:

```minikube start -p aged --kubernetes-version=v1.34.0```
Delete all of the minikube clusters:

```minikube delete --all```


![](https://github.com/priyanshurajmay-cmyk/Docker-and-MinuKube-setup/blob/main/docker%20screenshot-20250906T132528Z-1-001/docker%20screenshot/Screenshot%202025-09-06%20184412.png)


