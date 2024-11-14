# CICD_Project
This is a CICD project for a Java application using Maven, SonarQube, Argo CD, Helm and Kubernetes.

![Project Diagram](/img/project_diag.png)

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

### Prerequisites:
- Java application code hosted on a Git repository
- Jenkins server
- Kubernetes cluster
- Helm package manager
- Argo CD
### Steps

    1. Install the necessary Jenkins plugins:
       1.1 Git plugin
       1.2 Maven Integration plugin
       1.3 Pipeline plugin
       1.4 Kubernetes Continuous Deploy plugin

    2. Create a new Jenkins pipeline:
       2.1 In Jenkins, create a new pipeline job and configure it with the Git repository URL for the Java application.
       2.2 Add a Jenkinsfile to the Git repository to define the pipeline stages.

    3. Define the pipeline stages:
        Stage 1: Checkout the source code from Git.
        Stage 2: Build the Java application using Maven.
        Stage 3: Run unit tests using JUnit and Mockito.
        Stage 4: Run SonarQube analysis to check the code quality.
        Stage 5: Package the application into a JAR file.
        Stage 6: Deploy the application to a test environment using Helm.
        Stage 7: Run user acceptance tests on the deployed application.
        Stage 8: Promote the application to a production environment using Argo CD.

    4. Configure Jenkins pipeline stages:
        Stage 1: Use the Git plugin to check out the source code from the Git repository.
        Stage 2: Use the Maven Integration plugin to build the Java application.
        Stage 3: Use the JUnit and Mockito plugins to run unit tests.
        Stage 4: Use the SonarQube plugin to analyze the code quality of the Java application.
        Stage 5: Use the Maven Integration plugin to package the application into a JAR file.
        Stage 6: Use the Kubernetes Continuous Deploy plugin to deploy the application to a test environment using Helm.
        Stage 7: Use a testing framework like Selenium to run user acceptance tests on the deployed application.
        Stage 8: Use Argo CD to promote the application to a production environment.

    5. Set up Argo CD:
        Install Argo CD on the Kubernetes cluster.
        Set up a Git repository for Argo CD to track the changes in the Helm charts and Kubernetes manifests.
        Create a Helm chart for the Java application that includes the Kubernetes manifests and Helm values.
        Add the Helm chart to the Git repository that Argo CD is tracking.

    6. Configure Jenkins pipeline to integrate with Argo CD:
       6.1 Add the Argo CD API token to Jenkins credentials.
       6.2 Update the Jenkins pipeline to include the Argo CD deployment stage.

    7. Run the Jenkins pipeline:
       7.1 Trigger the Jenkins pipeline to start the CI/CD process for the Java application.
       7.2 Monitor the pipeline stages and fix any issues that arise.
   

