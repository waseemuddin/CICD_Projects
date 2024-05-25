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
![EC2 Setup Step 1](img/2.png)
![EC2 Setup Step 2](img/03.png)
![EC2 Setup Step 3](img/04.png)
![EC2 Setup Step 4](img/05.JPG)



