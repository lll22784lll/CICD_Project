# CICD_Project
This is a CICD project for a Java application using Maven, SonarQube, Argo CD, Helm and Kubernetes.

![Project Diagram](../img/project_diag.png)

### Project Summary
1. **Git Repository & Pull Requests:**
   - The Java application source code is hosted in a Git repository
   - Webhooks trigger Jenkins pipelines upon a pull request.

2. **Jenkins CI Pipeline (Declarative):**
   - **Build Stage**: Uses Maven to compile the code and run unit tests.
   - **Static Code Analysis**: Ensures code quality and identifies potential issues.
   - **Security Scanning**: Utilizes SAST and DAST tools to detect vulnerabilities.
   - **Notifications**: Sends alerts via email or Slack if any stage fails.
   - **Docker Image Creation**: A Docker image is built from the Dockerfile in the repo, then pushed to a container registry (e.g., AWS ECR, DockerHub).
3. **Continuous Delivery with Kubernetes:**
   - **Argo Image Updater**: Monitors the registry for new images and updates a separate Git repository containing the image manifest (Helm charts or Kubernetes manifests)
   - **Argo CD**: Monitors the updated manifest repository and deploys the new image to a Kubernetes cluster.
   

