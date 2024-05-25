# End to End CICD Project Pipeline  - Spring Boot based Java web application
 
This is a simple Sprint Boot based Java application that can be built using Maven. Sprint Boot dependencies are handled using the pom.xml 
at the root directory of the repository.

This is a MVC architecture based application where controller returns a page with title and message attributes to the view.


## Prerequisite for this projects

Ensure you have the following prerequisites before proceeding:
**Java application** : code hosted on a Git repository
1. **EC2 Machine**: t2.lage size preferred. (8/GB RAM and 2 Core Processor)
2. **Docker Setup** on EC2 Machine.
3. **Jenkins Setup**: You can either manually install Jenkins or use a Jenkins image.
4. **GitHub Account**: You need a GitHub account to automate the pipeline.
5. **Kubernetes cluster** : (Minikube is fine)
5. **Argo CD** : (usig Argo CD operator operatorhub.com)

For more updates and projects, visit:
- 💾 [shaikhwaseem.com](https://shaikhwaseem.com)
- 💾 [YouTube Channel](https://www.youtube.com/@waseeemuddin)


Here are the step-by-step details to set up an end-to-end Jenkins pipeline for a Java application using SonarQube, Argo CD, Helm, and Kubernetes:

## Architecture Diagram
![Architecture Diagram](img/pipelinediagram.png)

### Step 01 - Create EC2 Machine 
![EC2 Setup Step 1](img/01.png)
![EC2 Setup Step 2](img/02.png)
![EC2 Setup Step 3](img/03.png)

### Step 02 - Connect EC2 Machine  

Connect to your EC2 Ubuntu Machine using SSH. Make sure you're in the root user or use 'sudo'.

```shell
$ sudo ssh -i "key.pem" ubuntu@<ip-address>

```
![EC2 Setup Step 4](img/04.png)


### Step 03 - Installation of Jenkins

Install Jenkins either manually or using container-based installation. Here's the container-based installation command.

```shell
$ docker run -p 8080:8080 -p 50000:50000 -d \
-v jenkins_home:/var/jenkins_home \
-v /var/run/docker.sock:/var/run/docker.sock \
-v $(which docker):/usr/bin/docker jenkins/jenkins:lts
```
or you can install directly on server Ec2 machine.

```shell
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```
![EC2 Setup Step 4](img/05.png)

Here is the Jenkins Installation URL : https://www.jenkins.io/doc/book/installing/linux/

### Step 04 - Installation of Java - JDK

```shell
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version
openjdk version "17.0.8" 2023-07-18
OpenJDK Runtime Environment (build 17.0.8+7-Debian-1deb12u1)
OpenJDK 64-Bit Server VM (build 17.0.8+7-Debian-1deb12u1, mixed mode, sharing)

```

### Step 05 - Access Jenkins

```shell
Jenkins server access ur : <server-ip>:portno
e.g : http: 192.168.0.1:8080
```
Now, In order to access the Jenkins server, first you need to get the Jenkins password

![Jenkins server Step 6](img/06.png)
![Jenkins server Step 7](img/07.png)
![Jenkins server Step 8](img/08.png)

Now that we have setup our EC2 server, Docker, and Jenkins, let's create a simple Jenkins pipeline.

Before creating the pipeline, ensure your Git repository is up to date. Use the following links to update.

- 💾 [End-to-End-CICD](https://github.com/waseemuddin/CICD_Projects.git)

Log in to Jenkins using the password generated during setup


### Step 06 - Create Pipeline

![Jenkins server Step 9](img/09.png)

Pileline steps are same as we created in Project - 01 - [](https://github.com/waseemuddin/simple-cicd-project01.git)

![Jenkins server Step 10](https://github.com/waseemuddin/simple-cicd-project01/blob/main/img/13.JPG)
![Jenkins server Step 11](https://github.com/waseemuddin/simple-cicd-project01/blob/main/img/14.JPG)
![Jenkins server Step 12](https://github.com/waseemuddin/simple-cicd-project01/blob/main/img/15.JPG)
![Jenkins server Step 13](https://github.com/waseemuddin/simple-cicd-project01/blob/main/img/16.JPG)

### Step 07 - Install Plugins

Now next step is to install some pluings. Goto Manage jenkins and click plugin and install availabale plugins

1. **docker pipeline**: 
![Jenkins server Step 10](img/10.png)


2. **sinarqube scanner** 
![Jenkins server Step 11](img/11.png)


### Step 08 - Installation of SonarQube

``` shell
apt install unzip
adduser sonarqube
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.4.0.54424.zip
unzip *
chmod -R 755 /home/sonarqube/sonarqube-9.4.0.54424
chown -R sonarqube:sonarqube /home/sonarqube/sonarqube-9.4.0.54424
cd sonarqube-9.4.0.54424/bin/linux-x86-64/
./sonar.sh start

```
Now you can access the SonarQube Server on http://<ip-address>:9000

![Jenkins server Step 11](img/12.png)

Now in order to commnucate the Sonar-Server with Jenkins we need to create sonar-token id and made it available to jenkins credentails

Sonar - Server Token

![Jenkins server Step 11](img/13.png) 

Jenkins credentails for sonar-secret token

![Jenkins server Step 11](img/14.png) 




3. **Jenkins Setup**: You can either manually install Jenkins or use a Jenkins image.
4. **GitHub Account**: You need a GitHub account to automate the pipeline.
5. **Kubernetes cluster** : (Minikube is fine)
5. **Argo CD** : (usig Argo CD operator operatorhub.com)

