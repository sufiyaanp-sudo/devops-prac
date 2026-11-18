# Practical 1: Git and GitHub – Basic Commands, Branching & Merging

## Aim
To install Git, connect it with GitHub, and perform basic Git commands, branching, and merging.

## Requirements
- Windows Computer
- Internet Connection
- Git
- GitHub Account

## Procedure

### 1. Install Git
1. Download Git from [https://git-scm.com/downloads](https://git-scm.com/downloads).
2. Run the Windows installer.
3. Keep the default installation options and complete the installation.

### 2. Verify Git Installation

Open Git Bash or Command Prompt and execute:

```bash
git --version
```

### 3. Configure Git Identity

Set your name and email address:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

### 4. Create a Project and Initialize Repository

Create a new project folder and initialize a Git repository:

```bash
mkdir myproject
cd myproject
git init
```

### 5. Create a File and Perform Basic Git Commands

Create a file named `index.txt`:

```bash
echo Hello DevOps > index.txt
```

Check the repository status:

```bash
git status
```

Add the file to the staging area:

```bash
git add .
```

Commit the changes:

```bash
git commit -m "First commit"
```

### 6. Create a GitHub Repository

1. Sign in to your GitHub account.
2. Click on **New Repository**.
3. Enter the repository name as `myproject`.
4. Click **Create Repository**.
5. Copy the HTTPS repository URL.

### 7. Connect Local Repository to GitHub and Push Code

Add the GitHub repository as a remote:

```bash
git remote add origin https://github.com/USERNAME/myproject.git
```

Rename the current branch to `main`:

```bash
git branch -M main
```

Push the code to GitHub:

```bash
git push -u origin main
```

**Note:** Replace `USERNAME` with your GitHub username.

### 8. Create a Branch and Perform Merging

Create a new branch named `feature` and switch to it:

```bash
git checkout -b feature
```

Add new content to the existing file:

```bash
echo Feature work >> index.txt
```

Stage and commit the changes:

```bash
git add .
git commit -m "Add feature"
```

Switch back to the main branch:

```bash
git checkout main
```

Merge the feature branch into the main branch:

```bash
git merge feature
```

## Result

Git was successfully installed and configured. A local Git repository was created, files were added and committed, the local repository was connected to GitHub, and branching and merging operations were successfully performed.



# Practical 2: Jenkins – Installation and Basic Job
## Aim
To install Jenkins, complete its initial configuration, and run a basic freestyle job.
## Requirements
- Windows Computer
- Internet Connection
- Supported Java JDK (Java 21 where supported)
## Procedure
### 1. Install Java JDK
1. Download and install JDK from [https://adoptium.net](https://adoptium.net).
2. Open Command Prompt and verify Java installation:
```bash
java -version
```
### 2. Install Jenkins
1. Download the Windows Jenkins installer (.msi) from [https://www.jenkins.io/download](https://www.jenkins.io/download).
2. Run the installer and follow the installation steps.
3. Keep the default web port `8080`.
4. Complete installation and start the Jenkins service.
### 3. Unlock Jenkins
1. Open a browser and visit:
```
http://localhost:8080
```
2. Enter the initial administrator password from:
```
C:\ProgramData\Jenkins\.jenkins\secrets\initialAdminPassword
```
3. Install suggested plugins.
4. Create the administrator account and finish setup.
### 4. Create a Freestyle Job
1. Select **New Item**.
2. Enter the job name: `MyFirstJob`.
3. Select **Freestyle project** and click **OK**.
4. Under Build Steps, select **Execute Windows batch command**.
5. Enter the following command:
```bat
echo Hello Jenkins
```
6. Click **Save → Build Now**.
7. Open the build's **Console Output** to view the result.
## Result
Jenkins was successfully installed and configured. A freestyle job was created and executed successfully.
---
# Practical 3: Docker – Installation and Basic Setup on Windows
## Aim
To install Docker Desktop on Windows and run a test container.
## Requirements
- Supported 64-bit Windows version
- Hardware virtualization enabled
- WSL 2
- Adequate memory and disk space
## Procedure
### 1. Install WSL 2
Open PowerShell as Administrator and execute:
```powershell
wsl --install
```
Restart Windows if prompted.
### 2. Verify WSL
```powershell
wsl --version
```
### 3. Install Docker Desktop
1. Download Docker Desktop from [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop).
2. Run the installer.
3. Select the **WSL 2 backend** when offered.
4. Complete installation and restart if required.
5. Open Docker Desktop and wait until Docker Engine is running.
### 4. Verify Docker Installation
```bash
docker --version
docker info
```
### 5. Run a Test Container
```bash
docker run hello-world
```
### 6. View Images and Containers
```bash
docker images
docker ps
docker ps -a
```
### 7. Run an Nginx Web Server
```bash
docker run -d -p 8080:80 --name mynginx nginx
```
Open the browser and visit:
```
http://localhost:8080
```
### 8. Stop and Remove the Container
```bash
docker stop mynginx
docker rm mynginx
```
## Result
Docker Desktop was successfully installed and verified. A test container and an Nginx web server were executed successfully.
---
# Practical 4: Docker Compose – Running an Application
## Aim
To define and run a containerized application using Docker Compose.
## Requirements
- Docker Desktop installed and running
- Docker Compose
## Procedure
### 1. Verify Docker Compose
```bash
docker compose version
```
### 2. Create a Project Directory
```bash
mkdir compose-project
cd compose-project
```
### 3. Create a compose.yaml File
Create a file named `compose.yaml` and add the following configuration:
```yaml
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```
### 4. Start the Application
```bash
docker compose up -d
```
### 5. Check Service Status
```bash
docker compose ps
```
### 6. Access the Application
Open the browser and visit:
```
http://localhost:8080
```
The Nginx welcome page should appear.
### 7. View Logs
```bash
docker compose logs
```
### 8. Stop and Remove the Application
```bash
docker compose down
```
### Important Docker Compose Commands
| Command | Description |
|---|---|
| `docker compose up` | Create and start services |
| `docker compose up -d` | Run services in background |
| `docker compose ps` | List services |
| `docker compose logs` | View logs |
| `docker compose stop` | Stop services |
| `docker compose down` | Stop and remove resources |
## Result
A service was defined in `compose.yaml`, started using Docker Compose, checked, accessed through a browser, and stopped successfully.
---
# Practical 5: Ansible – Installation and Basic Automation using Windows (WSL)
## Aim
To install Ansible inside Ubuntu on WSL and execute a simple playbook locally.
## Requirements
- Windows Computer
- WSL 2
- Ubuntu installed
## Procedure
### 1. Install WSL
Open PowerShell as Administrator:
```powershell
wsl --install
```
Restart Windows if prompted.
### 2. Install Ubuntu
1. Install Ubuntu from Microsoft Store if it is not already installed.
2. Open Ubuntu.
3. Create a Linux username and password.
### 3. Update Ubuntu and Install Ansible
```bash
sudo apt update
sudo apt upgrade -y
sudo apt install ansible -y
```
### 4. Verify Ansible Installation
```bash
ansible --version
```
### 5. Create a Working Directory and Inventory File
```bash
mkdir ansible-practical
cd ansible-practical
nano inventory
```
Enter the following inventory content:
```ini
[local]
localhost ansible_connection=local
```
Save the file using **Ctrl+O → Enter → Ctrl+X**.
### 6. Test the Local Connection
```bash
ansible all -i inventory -m ping
```
Expected output includes `SUCCESS` and `"ping": "pong"`.
### 7. Create an Ansible Playbook
```bash
nano setup.yml
```
Enter the following YAML configuration:
```yaml
---
- name: My First Ansible Playbook
  hosts: local
  connection: local
  tasks:
    - name: Display a message
      debug:
        msg: "Hello from Ansible"
```
Save the file using **Ctrl+O → Enter → Ctrl+X**.
### 8. Run the Playbook
```bash
ansible-playbook -i inventory setup.yml
```
## Result
Ansible was successfully installed in Ubuntu on WSL. A local inventory was tested, and a simple Ansible playbook was executed successfully.
---
# Practical 6: Kubernetes – Deploying a Simple Application
## Aim
To deploy an Nginx application on a local Kubernetes cluster and access it through port forwarding.
## Requirements
- Docker Desktop with Kubernetes enabled, or another working local Kubernetes cluster
- kubectl configured
## Procedure
### 1. Enable Kubernetes
1. Open Docker Desktop.
2. Go to **Settings → Kubernetes**.
3. Enable Kubernetes and select **Apply/Restart**.
4. Wait until the cluster becomes ready.
**Note:** If Kubernetes is unavailable in your Docker Desktop version, use a configured local cluster such as Minikube.
### 2. Verify kubectl and the Cluster
```bash
kubectl version --client
kubectl cluster-info
kubectl get nodes
```
### 3. Create an Nginx Deployment
```bash
kubectl create deployment myapp --image=nginx
```
### 4. Check Deployment and Pods
```bash
kubectl get deployments
kubectl get pods
```
Wait until the pod status shows `Running`.
### 5. Expose the Deployment as a Service
```bash
kubectl expose deployment myapp --type=NodePort --port=80
```
### 6. Check the Service
```bash
kubectl get services
```
### 7. Forward a Local Port to the Application
Keep this terminal open while accessing the application:
```bash
kubectl port-forward deployment/myapp 8080:80
```
### 8. Access the Application
Open the browser and visit:
```
http://localhost:8080
```
The Nginx welcome page should appear.
### 9. Stop Port Forwarding and Clean Up
Press **Ctrl+C** to stop port forwarding.
Delete the service and deployment:
```bash
kubectl delete service myapp
kubectl delete deployment myapp
```
## Result
An Nginx deployment and service were successfully created in Kubernetes. The application was accessed locally using `kubectl port-forward`.
