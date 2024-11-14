# AWS EC2 Instance
- Go to AWS Console and luanch an instance.

# Install Jenkins
- Java(JDK) is needed.

### Install Java JDK and Jenkins
- Java JDK
```
sudo apt update
sudo apt install openjdk-17-jre
```
- Verify Java
```
java -version
```
- Install Jenkins on Ubuntu on AWS
```
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```
> [!NOTE]
> By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules

# Login to Jenkins

**http://<aws_instance_public_ip>:8080**

![unlock](/img/unlock.png)
![plugins](/img/plugins.png)
![get_started](/img/get_started.png)
![createAdmin](/img/createAdmin.png)
![ready](/img/ready.png)

# Jenkins plugin required: docker pipeline
- Log in to Jenkins
- Go to Manage Jenkins > Manage Plugins
- In the Available tab, search for 'docker pipeline'
- Select the plugin and click install
- Restart Jenkins after the plugin is installed
  
![jenkins_docker_pipeline_plugin](/img/jenkins_docker_pipeline_plugin.png)

# Install Docker 
- Run these commands
```
sudo apt update
sudo apt install docker.io
```
### grant Jenkins user and Ubuntu user permission to docker deamon
```
sudo su - 
usermod -aG docker jenkins
usermod -aG docker ubuntu
systemctl restart docker
```
Restart Jenkins
