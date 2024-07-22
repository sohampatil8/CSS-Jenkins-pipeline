# Download CSS-TEMPLATE files(index.html,CSS,images,JS)
```shell
curl -O https://www.free-css.com/assets/files/free-css-templates/download/page296/healet.zip
```
## upload all CSS-Template files to github Repository

# Create Dockerfile
```shell
FROM nginx:latest
COPY . /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

# Create Jenkins Server(java-17-openjdk)
```shell
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install Jenkins
##INSTALL JAVA PACK
sudo apt update
sudo apt install fontconfig openjdk-17-jre
sudo java -version
sudo alternatives --config java   #update java version to openjdk version "17.0.8" 2023-07-18
sudo java -version
#openjdk version "17.0.8" 2023-07-18
sudo systemctl enable Jenkins
sudo systemctl start Jenkins
sudo systemctl status Jenkins
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
# Now, hit PulicIP:8080 on Browser to start Jenkins-server
### PASSWORD >>> cat /var/lib/jenkins/secrets/initialAdminPassword
## ADD Plugins
1.Git
2.Docker
3.Kubernetes
4.Aws-Credential
## ADD Credentials
1.Docker-creds
2.aws-creds

# connect jenkins server use its Terminal
```shell
sudo yum install docker -y
sudo yum install git -y
sudo systemctl docker start
sudo systemctl start docker
sudo systemctl enable docker 
sudo chmod 666 /var/run/docker.sock
sudo gpasswd -aG jenkins docker
sudo gpasswd -a jenkins docker
sudo chown jenkins /var/run/docker.sock
sudo ll /var/run/docker.sock
```
# Set-Up Kubernetes on Jenkins server
## Create cluster and node
```shell
aws configure
aws eks update-kubeconfig --region ap-south-1 --name my-cluster --kubeconfig /tmp/config
chown jenkins:jenkins /tmp/config
```
## Install kubectl commands on jenkins server
```
sudo curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
sudo chmod +x kubectl
      mkdir -p ~/.local/bin
      mv ./kubectl ~/.local/bin/kubectl
      # and then append (or prepend) ~/.local/bin to $PATH
sudo kubectl cluster-info
