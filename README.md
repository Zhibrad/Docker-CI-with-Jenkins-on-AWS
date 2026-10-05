# 🚀 Docker CI with Jenkins on AWS

### Automating Docker Image Builds and Publishing to Amazon ECR

![AWS](https://img.shields.io/badge/AWS-EC2-orange?logo=amazonaws)
![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-red?logo=jenkins)
![Docker](https://img.shields.io/badge/Docker-Containerization-2496ED?logo=docker)
![Amazon ECR](https://img.shields.io/badge/Amazon-ECR-FF9900?logo=amazonaws)
![AWS CLI](https://img.shields.io/badge/AWS%20CLI-Command%20Line-orange?logo=amazonaws)
![GitHub](https://img.shields.io/badge/GitHub-Source%20Control-181717?logo=github)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-E95420?logo=ubuntu)
![DevOps](https://img.shields.io/badge/Domain-DevOps-purple)

> **A practical Docker CI/CD project demonstrating how Jenkins can build a Docker image from application source code and publish the image to Amazon Elastic Container Registry (ECR), creating the foundation for automated container deployment on AWS.**

---
<img width="1254" height="1254" alt="image" src="https://github.com/user-attachments/assets/b54ce6cc-9002-49b0-b8c3-2f73c3307cf7" />

# 📌 Project Overview

Traditional Jenkins CI often ends at:

```text
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
WAR Artifact
```

This project extends that workflow into containerized delivery:

```text
GitHub
   ↓
Jenkins
   ↓
Maven Build
   ↓
Docker Build
   ↓
Docker Image
   ↓
Amazon ECR
```

The purpose of this project is to demonstrate the transition from a traditional Java build artifact to a **portable, versioned container image** that can later be deployed to services such as Amazon ECS.

The project combines:

- Jenkins CI/CD
- Docker Engine
- AWS CLI
- AWS IAM
- Amazon ECR
- GitHub
- Maven
- Linux
- Jenkins Credentials
- AWS Security principles

---

# 🎯 Project Objectives

The project objectives were to:

- Provision AWS permissions for Jenkins.
- Install AWS CLI on the Jenkins server.
- Install Docker Engine.
- Configure Jenkins to execute Docker commands.
- Configure AWS credentials securely in Jenkins.
- Create a private Amazon ECR repository.
- Build a Docker image from the application source.
- Authenticate Docker to Amazon ECR.
- Tag the Docker image correctly.
- Push the image to Amazon ECR.
- Validate the image in the ECR repository.
- Establish the foundation for ECS-based deployment.

---

# 💼 Business Scenario

Imagine a development team maintaining a Java application.

The existing CI process already produces a successful application build:

```text
Developer
   ↓
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
WAR
```

The next requirement is to standardize how the application is packaged and deployed.

Instead of transporting a WAR file between environments, the organization wants a portable container image:

```text
Application
   ↓
Dockerfile
   ↓
Docker Image
   ↓
Amazon ECR
   ↓
ECS / Kubernetes / Other Runtime
```

This creates a clean separation between:

```text
Build
Packaging
Registry
Deployment
```

---

# 🏗️ Solution Architecture

```text
                         DEVELOPER
                             |
                             v
                          GitHub
                             |
                             v
                    +-------------------+
                    | Jenkins Controller|
                    |                   |
                    | CI/CD Pipeline    |
                    +---------+---------+
                              |
                              v
                       Maven Build/Test
                              |
                              v
                        Docker Build
                              |
                              v
                      Docker Image
                              |
                              v
                  AWS ECR Authentication
                              |
                              v
                    Amazon ECR Registry
                              |
                              v
                    Container Deployment
                         (Future)
                              |
                              v
                           ECS
```

---

# 🌐 AWS Architecture

```text
                           AWS ACCOUNT
                                |
             +------------------+------------------+
             |                                     |
             v                                     v
        Jenkins EC2                         Amazon ECR
             |                                     |
        Docker Engine                        Docker Images
             |                                     |
        AWS CLI / IAM ----------------------------+
             |
             v
        Jenkins Pipeline
```

---

# 🔄 End-to-End Flow

```text
1. Fetch Source Code
        ↓
2. Build Application
        ↓
3. Unit Test
        ↓
4. Build Docker Image
        ↓
5. Authenticate with AWS
        ↓
6. Authenticate Docker with ECR
        ↓
7. Tag Image
        ↓
8. Push Image
        ↓
9. Verify Image in ECR
```

---

# 🧩 Core Components

| Component | Purpose |
|---|---|
| AWS EC2 | Jenkins infrastructure |
| Jenkins | CI/CD orchestration |
| GitHub | Source-code repository |
| Maven | Java build process |
| Docker Engine | Container image creation |
| AWS CLI | AWS service interaction |
| IAM | AWS authorization |
| Amazon ECR | Private Docker image registry |
| Jenkins Credentials | Secure secret storage |
| Docker Pipeline | Jenkins Docker integration |

---

# 🛠️ Technology Stack

### Cloud

- Amazon EC2
- Amazon ECR
- AWS IAM
- AWS Security Groups

### CI/CD

- Jenkins
- Jenkins Pipeline
- Jenkins Credentials

### Build

- Maven
- Java
- Git

### Containerization

- Docker Engine
- Docker CLI
- Docker Pipeline

### Source Control

- GitHub

---

# 📚 Table of Contents

1. [Project Overview](#-project-overview)
2. [Project Objectives](#-project-objectives)
3. [Business Scenario](#-business-scenario)
4. [Solution Architecture](#-solution-architecture)
5. [AWS Architecture](#-aws-architecture)
6. [End-to-End Flow](#-end-to-end-flow)
7. [Core Components](#-core-components)
8. [Technology Stack](#-technology-stack)
9. [Construction Rules](#-construction-rules)
10. [Prerequisites](#-prerequisites)
11. [Phase 1 — Prepare AWS IAM](#phase-1--prepare-aws-iam)
12. [Phase 2 — Install AWS CLI](#phase-2--install-aws-cli)
13. [Phase 3 — Install Docker Engine](#phase-3--install-docker-engine)
14. [Phase 4 — Configure Jenkins for Docker](#phase-4--configure-jenkins-for-docker)
15. [Phase 5 — Create Amazon ECR Repository](#phase-5--create-amazon-ecr-repository)
16. [Phase 6 — Configure Jenkins AWS Credentials](#phase-6--configure-jenkins-aws-credentials)
17. [Phase 7 — Validate Pipeline Variables](#phase-7--validate-pipeline-variables)
18. [Phase 8 — Build the Docker Image](#phase-8--build-the-docker-image)
19. [Phase 9 — Authenticate with ECR](#phase-9--authenticate-with-ecr)
20. [Phase 10 — Push Image to ECR](#phase-10--push-image-to-ecr)
21. [Complete Jenkins Pipeline](#-complete-jenkins-pipeline)
22. [Image Lifecycle](#-image-lifecycle)
23. [Security Architecture](#-security-architecture)
24. [Verification Checklist](#-verification-checklist)
25. [Troubleshooting](#-troubleshooting)
26. [Cost Considerations](#-cost-considerations)
27. [Production Improvements](#-production-improvements)
28. [Skills Demonstrated](#-skills-demonstrated)
29. [Project Structure](#-project-structure)
30. [Lessons Learned](#-lessons-learned)
31. [Future CI/CD Evolution](#-future-cicd-evolution)
32. [Official Documentation](#-official-documentation)
33. [Project Author](#-project-author)

---

# 📐 Construction Rules

## Rule 1 — Build Once, Promote the Same Image

The Docker image produced by CI should become the artifact promoted through environments.

```text
Build
  ↓
Image
  ↓
ECR
  ↓
Dev
  ↓
Test
  ↓
Production
```

Avoid rebuilding different images for each environment when the same immutable artifact can be promoted.

---

## Rule 2 — Do Not Hardcode AWS Credentials

Never put:

```text
AWS Access Key
AWS Secret Key
```

inside:

```text
Jenkinsfile
Dockerfile
GitHub
Shell scripts
README.md
```

Store credentials in Jenkins Credentials or, preferably for an AWS-hosted Jenkins workload, use an IAM role with temporary credentials.

AWS explicitly recommends IAM roles and temporary credentials for workloads where possible. :contentReference[oaicite:3]{index=3}

---

## Rule 3 — Use Least Privilege

The lab implementation may use broad managed policies for learning.

Production should narrow permissions to the ECR repository and actions Jenkins actually requires.

Amazon ECR supports repository-level resource policies and granular ECR actions for this purpose. :contentReference[oaicite:4]{index=4}

---

## Rule 4 — Docker Access Is Sensitive

The Jenkins build user must have permission to execute Docker commands.

Adding a Linux user to the `docker` group is convenient, but Docker daemon access is highly privileged.

Therefore, Docker access should be treated as a powerful administrative capability.

---

## Rule 5 — Validate Registry Configuration

Before running the pipeline, verify:

```text
AWS Region
ECR Registry URL
ECR Repository Name
Jenkins Credential ID
Image Name
Image Tag
```

A mismatch in any of these values can cause an otherwise healthy pipeline to fail.

---

# ✅ Prerequisites

Before starting:

- AWS account
- Existing Jenkins server
- Jenkins Pipeline support
- GitHub repository
- Java/Maven application
- Dockerfile in the application repository
- AWS IAM access
- Jenkins administrator access
- Amazon ECR access

---

# PHASE 1 — Prepare AWS IAM

## 1. Create IAM User for the Lab

For the original learning implementation, create:

```text
IAM User:
jenkins
```
<img width="1823" height="489" alt="image" src="https://github.com/user-attachments/assets/8e1f54ef-bdb1-43b0-b712-8b08d870cc27" />

Enable programmatic access by creating an access key.

The access key consists of:

```text
Access Key ID
+
Secret Access Key
```

> **Security note:** This is suitable for demonstrating the credential flow, but AWS recommends temporary credentials and IAM roles for workloads where possible. For a Jenkins EC2 server in production, use an instance profile/role rather than long-lived IAM user keys. :contentReference[oaicite:5]{index=5}

---
<img width="1442" height="506" alt="image" src="https://github.com/user-attachments/assets/46fdb847-8e5a-4543-9f80-0c6a0b54675e" />
<img width="1402" height="752" alt="image" src="https://github.com/user-attachments/assets/176508fb-a970-4463-8ee5-a99eadd9aed0" />
<img width="1289" height="490" alt="image" src="https://github.com/user-attachments/assets/bad4842f-e412-4a1f-8a54-ac698fe34be6" />

# 2. IAM Permissions

For the lab, you may encounter configurations using:

```text
AmazonEC2ContainerRegistryFullAccess
AmazonECSFullAccess
```
<img width="1633" height="582" alt="image" src="https://github.com/user-attachments/assets/c396c66a-1e1d-4ae8-8a61-899daf6fb603" />

The first provides broad ECR permissions.

The second is not required merely to build and push an image to ECR; it becomes relevant only when the pipeline also manages ECS resources.

A production implementation should use a narrowly scoped ECR policy.

---

# Recommended Production ECR Policy

For Jenkins to push into one repository, the permissions should be constrained to the required repository actions.

Typical push operations involve permissions such as:

```text
ecr:GetAuthorizationToken
ecr:BatchCheckLayerAvailability
ecr:InitiateLayerUpload
ecr:UploadLayerPart
ecr:CompleteLayerUpload
ecr:PutImage
```

AWS documents the ECR API actions and their resource scopes. :contentReference[oaicite:6]{index=6}

---

# PHASE 2 — Install AWS CLI

SSH into the Jenkins server:

```bash
ssh -i "jenkins-key.pem" ubuntu@<JENKINS-PUBLIC-IP>
```

Update packages:

```bash
sudo apt update
```

---

# Install AWS CLI

The original lab implementation uses Snap:

```bash
sudo snap install aws-cli --classic
```

Verify:

```bash
aws --version
```

AWS officially supports the Snap installation method; for teams that need version pinning, AWS recommends the command-line installer instead. :contentReference[oaicite:7]{index=7}

---
<img width="1325" height="343" alt="image" src="https://github.com/user-attachments/assets/b4dbfded-428f-4cb2-8d64-359b657408dd" />

# PHASE 3 — Install Docker Engine

Docker's current Ubuntu documentation recommends configuring Docker's official `apt` repository. :contentReference[oaicite:8]{index=8}

Install prerequisites:

```bash
sudo apt update
sudo apt install -y ca-certificates curl
```

Create Docker keyring directory:

```bash
sudo install -m 0755 -d /etc/apt/keyrings
```

Download Docker's signing key:

```bash
sudo curl -fsSL \
https://download.docker.com/linux/ubuntu/gpg \
-o /etc/apt/keyrings/docker.asc
```

Set permissions:

```bash
sudo chmod a+r /etc/apt/keyrings/docker.asc
```
Add Docker repository:

```bash
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF
```

Update:

```bash
sudo apt update
```

Install Docker Engine:

```bash
sudo apt install -y \
docker-ce \
docker-ce-cli \
containerd.io \
docker-buildx-plugin \
docker-compose-plugin
```

Verify Docker:

```bash
sudo systemctl status docker
```

Run:

```bash
sudo docker run hello-world
```

Docker documents `hello-world` as the basic installation verification test. :contentReference[oaicite:9]{index=9}

---
<img width="1336" height="986" alt="image" src="https://github.com/user-attachments/assets/84bb772c-3c91-449a-995b-d700136ea448" />
<img width="1503" height="988" alt="image" src="https://github.com/user-attachments/assets/39a77421-75f3-4c7f-b945-01fc81e5c1fd" />
<img width="1611" height="635" alt="image" src="https://github.com/user-attachments/assets/609ce135-7807-4db5-bb2f-a71135e18fb7" />
<img width="1216" height="546" alt="image" src="https://github.com/user-attachments/assets/ec3cfb5b-6fec-4c2c-9e32-835aec59b32b" />

# PHASE 4 — Configure Jenkins for Docker

## 3. Switch to the Jenkins User

Attempt:

```bash
su - jenkins
```

If you receive:

```text
Permission denied
```

that is not necessarily a problem; system service users are commonly configured without interactive login shells.

Return to your administrative shell:

```bash
exit
```

---

# 4. Add Jenkins to the Docker Group

Run:

```bash
sudo usermod -aG docker jenkins
```

Verify:

```bash
id jenkins
```

You should see:

```text
docker
```

among the groups.

---
<img width="1119" height="437" alt="image" src="https://github.com/user-attachments/assets/559e822e-244d-497c-a4fb-5c9a7f3df25f" />

# 5. Restart the Server

Reboot the Jenkins EC2 instance:

```bash
sudo reboot
```

After the server returns, reconnect.

Verify:

```bash
id jenkins
```

Then test Docker as Jenkins:

```bash
sudo -u jenkins docker ps
```

If the command works without `sudo`, the Jenkins user can communicate with the Docker daemon.

---

# PHASE 5 — Create Amazon ECR Repository

Amazon ECR acts as the private registry for the Docker image.

Navigate to:

```text
AWS Console
   ↓
Elastic Container Registry
   ↓
Repositories
   ↓
Create repository
```

Example:

```text
Repository name:
vprofileappimg
```
<img width="1673" height="184" alt="image" src="https://github.com/user-attachments/assets/d0352600-610e-4d7e-990e-f7aff52dfe88" />

After creation, ECR provides a registry URL similar to:

```text
354918367765.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg
```

The repository must exist before a normal Docker image push, unless a repository creation template is configured. :contentReference[oaicite:10]{index=10}

---

# PHASE 6 — Configure Jenkins AWS Credentials

Go to:

```text
Jenkins
   ↓
Manage Jenkins
   ↓
Credentials
   ↓
System
   ↓
Global credentials
   ↓
Add Credentials
```

Select:

```text
Kind:
AWS Credentials
```

Use:

```text
ID:
awscreds
```

Then enter:

```text
Access Key ID:
<YOUR ACCESS KEY>

Secret Access Key:
<YOUR SECRET ACCESS KEY>
```

The Jenkins AWS Credentials plugin supports storing IAM access keys through the Jenkins Credentials API. :contentReference[oaicite:11]{index=11}

---
<img width="1913" height="911" alt="image" src="https://github.com/user-attachments/assets/01831e03-4a42-45fb-b994-fd7699f54b03" />
<img width="737" height="842" alt="image" src="https://github.com/user-attachments/assets/71e899a7-e6ab-4431-8788-75a30c7e4157" />

# Production Recommendation

For production Jenkins running on EC2:

```text
Jenkins EC2
    |
    v
IAM Instance Profile
    |
    v
Temporary Credentials
    |
    v
ECR
```

rather than:

```text
Jenkins
   |
   v
Long-lived IAM User Access Key
```

AWS explicitly recommends temporary credentials and IAM roles for workloads wherever possible. :contentReference[oaicite:12]{index=12}

---

# PHASE 7 — Install Jenkins Plugins

Go to:

```text
Manage Jenkins
   ↓
Plugins
   ↓
Available Plugins
```

Install the plugins required by the pipeline.

Recommended:

```text
Amazon Web Services SDK :: All
Docker pipeline
AWS Credentials
CloudBees Docker Build and Publish
```

Depending on your Jenkins version and pipeline design, additional Docker plugins may be installed automatically as dependencies.

The Amazon ECR plugin integrates Amazon credentials with Docker-related Jenkins plugins and supports ECR authentication through the `ecr:` credential provider. :contentReference[oaicite:13]{index=13}

---

# Plugin Responsibilities

| Plugin | Purpose |
|---|---|
| Docker Pipeline | Docker image build/push operations |
| Amazon ECR | ECR authentication integration |
| AWS Credentials | Store AWS credentials |
| Pipeline: AWS Steps | AWS service operations from Pipeline |

The Pipeline: AWS Steps plugin also exposes an `ecrLogin` step for ECR authentication. :contentReference[oaicite:14]{index=14}

---
<img width="1889" height="919" alt="image" src="https://github.com/user-attachments/assets/4382ebb2-4004-4674-9e7a-86f2e2e0655f" />

# PHASE 8 — Validate Pipeline Variables

Before executing the pipeline, confirm:

## AWS Region

```text
us-east-1
```

---

## ECR Registry

```text
<ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com
```

---

## ECR Repository

```text
vprofileappimg
```

---

## Full Image Reference

```text
<ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg:<TAG>
```

Example:

```text
<ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg:42
```

---

# PHASE 9 — Build the Docker Image

The Jenkins pipeline should first build the image locally on the Jenkins server or build agent.

Example:

```bash
docker build -t vprofileappimg:latest .
```

Then inspect:

```bash
docker images
```

---

# Tag the Image

Tag the image with the ECR registry:

```bash
docker tag \
vprofileappimg:latest \
354918367765.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg:latest
```

A versioned tag is preferable for traceability:

```bash
docker tag \
vprofileappimg:latest \
354918367765.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg:${BUILD_NUMBER}
```
<img width="669" height="122" alt="image" src="https://github.com/user-attachments/assets/0d27582c-8fbc-4f53-bc60-2199c9eb41f3" />

---

# PHASE 10 — Authenticate with ECR

AWS's current authentication pattern is:

```bash
aws ecr get-login-password \
--region us-east-1 \
| docker login \
--username AWS \
--password-stdin \
354918367765.dkr.ecr.us-east-1.amazonaws.com
```

The ECR authentication token is valid for 12 hours. :contentReference[oaicite:15]{index=15}

After authentication:

```text
Jenkins
   |
   v
AWS CLI
   |
   v
ECR Authentication Token
   |
   v
Docker Login
```

---
<img width="1360" height="779" alt="image" src="https://github.com/user-attachments/assets/aa4f1103-a6a3-4fd4-be4d-72dede24465f" />

# PHASE 11 — Push the Image

Push:

```bash
docker push \
<ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg:latest
```

Or use the immutable build number:

```bash
docker push \
<ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg:${BUILD_NUMBER}
```

AWS ECR accepts Docker image pushes after the registry authentication has been established and the IAM principal has the necessary permissions. :contentReference[oaicite:16]{index=16}

---
<img width="1898" height="764" alt="image" src="https://github.com/user-attachments/assets/d1f4fda2-0aeb-4e5c-8978-c056f4d55e48" />
<img width="1889" height="884" alt="image" src="https://github.com/user-attachments/assets/3cedac3d-a786-40f6-9951-07a165e592db" />

# 📦 Recommended Image Tagging Strategy

Instead of relying only on:

```text
latest
```

use:

```text
BUILD_NUMBER
```

or:

```text
GIT_COMMIT
```

Examples:

```text
vprofileappimg:42
vprofileappimg:abc1234
```

This creates traceability:

```text
Git Commit
    ↓
Jenkins Build
    ↓
Docker Image Tag
    ↓
ECR
```

---

# 🚀 Complete Jenkins Pipeline

The following is a transparent CLI-based implementation and is often easier to troubleshoot than hiding the ECR authentication inside a plugin.

Replace:

```text
<ACCOUNT_ID>
<REPOSITORY>
<USERNAME>
```

with your values.

```groovy
pipeline {
    agent any

    tools {
        maven "MAVEN3.9"
        jdk "JDK17"
    }

    environment {
        registryCredential = 'ecr:us-east-1:awscreds'
        imageName = "354918367765.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg"
        vprofileRegistry = "https://354918367765.dkr.ecr.us-east-1.amazonaws.com"
    }

    stages {

        stage('Fetch code') {
            steps {
                git branch: 'docker', url: 'https://github.com/hkhcoder/vprofile-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn install -DskipTests'
            }
            post {
                success {
                    echo 'Now Archiving it...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('UNIT TEST') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Checkstyle Analysis') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }

        stage("Sonar Code Analysis") {
            environment {
                scannerHome = tool 'sonar8.0'
            }
            steps {
                withSonarQubeEnv('sonarserver') {
                    sh '''${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=vprofile \
                       -Dsonar.projectName=vprofile \
                       -Dsonar.projectVersion=1.0 \
                       -Dsonar.sources=src/ \
                       -Dsonar.java.binaries=target/test-classes/com/visualpathit/account/controllerTest/ \
                       -Dsonar.junit.reportsPath=target/surefire-reports/ \
                       -Dsonar.jacoco.reportsPath=target/jacoco.exec \
                       -Dsonar.java.checkstyle.reportPaths=target/checkstyle-result.xml'''
                }
            }
        }

        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }

        stage('Build App Image') {
            steps {
                script {
                    dockerImage = docker.build(
                        imageName + ":$BUILD_NUMBER",
                        "./Docker-files/app/multistage/"
                    )
                }
            }
        }

        stage('Upload App Image') {
            steps {
                script {
                    docker.withRegistry(vprofileRegistry, registryCredential) {
                        dockerImage.push("$BUILD_NUMBER")
                        dockerImage.push('latest')
                    }
                }
            }
        }

    }   
}       
```

The AWS credentials binding shown above is supported by the Jenkins AWS Credentials plugin, and the ECR login sequence follows AWS's documented Docker authentication method. :contentReference[oaicite:17]{index=17}

---

# 🔐 Alternative: Jenkins ECR Plugin

If you prefer Jenkins-managed Docker registry integration, the Amazon ECR plugin supports:

```groovy
docker.withRegistry(
    "https://${ECR_REGISTRY}",
    "ecr:us-east-1:awscreds"
) {
    def image = docker.build(
        "${ECR_REGISTRY}/${ECR_REPOSITORY}:${BUILD_NUMBER}"
    )

    image.push()
}
```

The current Amazon ECR Jenkins plugin documents this `ecr:<region>:<credential-id>` pattern. :contentReference[oaicite:18]{index=18}

For learning and troubleshooting, the explicit AWS CLI method can make the authentication flow easier to understand.

---

# 🔄 Docker Image Lifecycle

```text
GitHub
   |
   v
Jenkins
   |
   v
Application Source
   |
   v
Maven Build/Test
   |
   v
Docker Build
   |
   v
Docker Image
   |
   v
Docker Tag
   |
   v
ECR Authentication
   |
   v
Amazon ECR
   |
   v
Future ECS Deployment
```

---

# 🏷️ Image Versioning

Recommended:

```text
vprofileappimg:42
```

rather than only:

```text
vprofileappimg:latest
```

A build-number tag allows:

```text
Jenkins Build #42
        =
Docker Image :42
        =
ECR Image :42
```

This improves traceability and rollback.

---

# 🔐 Security Architecture

```text
                         AWS
                          |
               +----------+----------+
               |                     |
               v                     v
          Jenkins EC2              ECR
               |                     |
          Docker Engine              |
               |                     |
               +------ IAM ----------+
```

The Jenkins pipeline requires:

```text
Authentication
        +
Authorization
        +
Docker Access
```

---

# Security Controls

## 1. Jenkins Credentials

AWS secrets belong in:

```text
Jenkins Credentials
```

not source code.

---

## 2. IAM Least Privilege

Instead of:

```text
AmazonEC2ContainerRegistryFullAccess
+
AmazonECSFullAccess
```

for a production Docker-CI-only pipeline, scope permissions to ECR actions and the specific repository where possible.

AWS supports granular ECR actions and resource-level controls. :contentReference[oaicite:19]{index=19}

---

## 3. Prefer IAM Roles

Production:

```text
Jenkins EC2
      |
      v
IAM Role / Instance Profile
      |
      v
Temporary Credentials
      |
      v
Amazon ECR
```

Lab:

```text
Jenkins
      |
      v
IAM User Access Key
      |
      v
ECR
```

AWS recommends the role-based approach for workloads. :contentReference[oaicite:20]{index=20}

---

## 4. Docker Group Security

Adding Jenkins to:

```text
docker
```

allows Jenkins to interact with the Docker daemon.

This is useful for CI, but access to Docker is highly privileged.

Production deployments should therefore:

- restrict who can modify Jenkins jobs,
- protect Jenkins credentials,
- restrict agent access,
- avoid unnecessary root access,
- monitor Docker workloads.

---

# 🧪 Verification Checklist

```text
[✓] Jenkins EC2 running

[✓] AWS CLI installed

[✓] AWS CLI version verified

[✓] Docker Engine installed

[✓] Docker service running

[✓] Docker hello-world successful

[✓] Jenkins added to docker group

[✓] Jenkins Docker access verified

[✓] IAM access configured

[✓] ECR repository created

[✓] AWS credential stored in Jenkins

[✓] Jenkins plugins installed

[✓] AWS region verified

[✓] ECR registry verified

[✓] Docker image built

[✓] Image tagged

[✓] ECR authentication successful

[✓] Image pushed to ECR

[✓] Image visible in ECR

[✓] SonarQube stage completed
```

---

# 🚨 Troubleshooting

## Docker Permission Denied

If Jenkins returns:

```text
permission denied while trying to connect to the Docker daemon
```

check:

```bash
id jenkins
```

Verify:

```text
docker
```

appears in the group list.

Then restart the server:

```bash
sudo reboot
```

After reconnecting:

```bash
sudo -u jenkins docker ps
```

---

# AWS CLI Not Found

Check:

```bash
aws --version
```

If missing:

```bash
sudo snap install aws-cli --classic
```

Then:

```bash
aws --version
```

AWS supports this Snap installation method. :contentReference[oaicite:21]{index=21}

---

# ECR Login Failed

Check:

```text
AWS Region
AWS Credentials
ECR Registry
IAM Permissions
```

Test manually:

```bash
aws sts get-caller-identity
```

Then:

```bash
aws ecr get-login-password \
--region us-east-1 \
| docker login \
--username AWS \
--password-stdin \
<ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com
```

The ECR login token is temporary and is valid for 12 hours. :contentReference[oaicite:22]{index=22}

---

# Image Push Denied

Typical causes:

```text
Wrong AWS Region
Wrong ECR Registry
Wrong Repository Name
Missing ECR Permissions
Expired Credentials
```

Check:

```bash
aws ecr describe-repositories \
--repository-names vprofileappimg \
--region us-east-1
```

---

# Repository Not Found

Check:

```bash
aws ecr describe-repositories \
--repository-names vprofileappimg \
--region us-east-1
```

The repository must exist in the target registry/region before the normal push flow. :contentReference[oaicite:23]{index=23}

---

# Docker Build Failed

Run locally on the Jenkins server:

```bash
docker build -t test-image .
```

Check:

```text
Dockerfile
Application files
Build context
Dependencies
```

---

# SonarQube Stage Fails

Because this project builds on your previous Jenkins + SonarQube work, check:

```text
SonarQube Server
SonarQube Token
Webhook
Quality Gate
Private IP
Security Group
```

Confirm the SonarQube server is running before executing the pipeline.

---

# 💰 Cost Considerations

The core AWS resources are:

```text
Jenkins EC2
+
ECR
+
EBS
+
Network Traffic
```

Potential costs include:

- EC2 runtime
- EBS storage
- ECR image storage
- Data transfer
- CloudWatch if enabled

ECR costs also depend on image storage and data transfer.

Repeatedly pushing large images can increase storage and transfer usage, so image optimization matters.

---

# 🧹 Docker Image Optimization

A production Docker CI environment should keep images small.

Consider:

```text
Multi-stage builds
Smaller base images
.dockerignore
Dependency caching
Layer ordering
```

Example:

```dockerfile
FROM eclipse-temurin:17-jre

WORKDIR /app

COPY target/*.war app.war

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.war"]
```

The exact Dockerfile should match the application's runtime architecture.

---

# 📈 Production Improvements

## 1. Replace IAM User Keys

Current lab:

```text
IAM User
   ↓
Access Key
   ↓
Jenkins
```

Production:

```text
EC2
   ↓
IAM Instance Role
   ↓
Temporary Credentials
   ↓
ECR
```

AWS recommends this role-based approach for workloads. :contentReference[oaicite:24]{index=24}

---

## 2. Use Least Privilege

Limit Jenkins to:

```text
ECR authentication
+
Repository push
+
Repository inspection
```

Only add ECS permissions when the pipeline actually deploys to ECS.

---

## 3. Use Immutable Tags

Prefer:

```text
image:42
```

or:

```text
image:<git-sha>
```

rather than relying entirely on:

```text
image:latest
```

---

## 4. Enable Image Scanning

Configure ECR image scanning according to your security requirements.

Pipeline:

```text
Docker Build
   ↓
Push ECR
   ↓
Scan Image
   ↓
Security Decision
```

---

## 5. Add Dockerfile Security Scanning

Future options include:

```text
Trivy
Docker Scout
SonarQube
ECR scanning
```

---

## 6. Deploy to ECS

Once ECR is working:

```text
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
SonarQube
   ↓
Quality Gate
   ↓
Docker
   ↓
ECR
   ↓
ECS
```

This becomes a complete AWS container CI/CD platform.

---

# 🧠 Skills Demonstrated

## AWS

- Amazon EC2
- Amazon ECR
- IAM
- AWS CLI
- AWS Security Groups
- VPC networking
- AWS credentials
- Cost awareness

## Jenkins

- Jenkins Pipeline
- Jenkins Credentials
- Docker Pipeline
- AWS credentials integration
- CI/CD automation

## Docker

- Docker Engine
- Docker CLI
- Dockerfile
- Docker image build
- Docker tagging
- Docker registry authentication
- Docker push

## Linux

- Ubuntu
- APT
- systemd
- Linux groups
- User permissions
- Docker daemon access

## Source Control

- Git
- GitHub
- Branch-based builds

## DevOps

- Continuous Integration
- Containerization
- Artifact management
- Cloud infrastructure
- Security
- Automation
- Deployment readiness

---

# 📂 Project Structure

```text
docker-ci-jenkins/
│
├── README.md
│
├── Jenkinsfile
│
├── Dockerfile
│
├── .dockerignore
│
├── docs/
│   ├── aws-iam.md
│   ├── ecr.md
│   ├── docker.md
│   ├── jenkins.md
│   └── troubleshooting.md
│
├── architecture/
│   └── docker-ci-jenkins-aws.png
│
└── screenshots/
    ├── ec2.png
    ├── docker-status.png
    ├── iam.png
    ├── ecr.png
    ├── jenkins-credentials.png
    ├── pipeline.png
    └── ecr-image.png
```

---

# 🔐 Recommended `.gitignore`

```gitignore
# AWS / SSH
*.pem
*.key
id_rsa
id_ed25519

# Environment variables
.env
.env.*

# AWS credentials
.aws/
credentials

# Jenkins secrets
secrets/
credentials/

# Logs
*.log

# Docker
docker-compose.override.yml
```

---

# 🧠 Lessons Learned

## 1. CI Does Not End at Compilation

A successful Maven build produces an application artifact.

Docker CI converts that artifact into a portable runtime image:

```text
Source
   ↓
Build
   ↓
Artifact
   ↓
Container
```

---

## 2. ECR Becomes the Image Source of Truth

Once the image is pushed:

```text
Amazon ECR
   |
   +-- image:41
   +-- image:42
   +-- image:43
```

each image can become a versioned deployment artifact.

---

## 3. AWS Authentication Is Part of the Pipeline

Jenkins needs an AWS identity capable of:

```text
Authenticate
     ↓
ECR
     ↓
Push Image
```

The authentication mechanism must therefore be designed as part of the CI/CD architecture, not added as an afterthought.

---

## 4. Jenkins Credentials Are Critical

A CI/CD server often has access to:

```text
GitHub
AWS
Docker
ECR
ECS
SonarQube
Nexus
```

A compromise of the Jenkins environment can therefore have significant consequences.

Protecting Jenkins credentials is as important as building the pipeline itself.

---

# 🏆 Portfolio Value

This project demonstrates the transition from a traditional Java CI workflow:

```text
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
WAR
```

to a container-focused CI workflow:

```text
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
Docker
   ↓
Amazon ECR
```

It demonstrates practical knowledge across:

```text
Cloud Infrastructure
+
Linux
+
Jenkins
+
Docker
+
AWS IAM
+
Amazon ECR
+
GitHub
+
CI/CD
```

The next logical step is container deployment.

---

# 🔮 Future CI/CD Evolution

## Current

```text
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
Docker
   ↓
ECR
```

## Next

```text
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
SonarQube
   ↓
Quality Gate
   ↓
Docker
   ↓
ECR
   ↓
ECS
```

## Target Architecture

```text
                        DEVELOPER
                            |
                            v
                         GitHub
                            |
                            v
                     Jenkins Controller
                            |
                  +---------+---------+
                  |                   |
                  v                   v
                Maven              Tests
                  |
                  v
              SonarQube
                  |
                  v
             Quality Gate
                  |
                  v
              Docker Build
                  |
                  v
                 ECR
                  |
                  v
                 ECS
                  |
                  v
             Production
                  |
                  v
                Slack
```

---

# 📌 Project Summary

### Project

**Docker CI with Jenkins**

### Source

```text
GitHub
```

### CI/CD

```text
Jenkins
```

### Application Build

```text
Maven
```

### Containerization

```text
Docker
```

### Registry

```text
Amazon ECR
```

### Authentication

```text
AWS IAM
+
Jenkins Credentials
```

### AWS Region

```text
us-east-1
```

---

# 📚 Official Documentation

### Docker Engine
Docker's current Ubuntu installation documentation.

### AWS CLI
AWS CLI installation and authentication documentation.

### Amazon ECR
Private repository and Docker push documentation.

### IAM
AWS IAM security and workload credential guidance.

### Jenkins
Jenkins Pipeline, Docker and credentials documentation.

### Amazon ECR Jenkins Plugin
Jenkins ECR integration documentation.

---

# 👨‍💻 Project Author

## Zhibrad

**Cloud & DevOps Portfolio**

Focus areas:

```text
AWS
Docker
Jenkins
Linux
CI/CD
Maven
GitHub
Amazon ECR
Cloud Security
Infrastructure Automation
DevOps
```

---

# ⭐ Final Architecture

```text
                         DEVELOPER
                             |
                             v
                          GitHub
                             |
                             v
                    +----------------+
                    |    Jenkins     |
                    | CI/CD Server   |
                    +-------+--------+
                            |
                            v
                        Maven Build
                            |
                            v
                       Unit Testing
                            |
                            v
                      Docker Build
                            |
                            v
                       Docker Image
                            |
                            v
                      AWS IAM Auth
                            |
                            v
                   Amazon ECR Registry
                            |
                            v
                    Versioned Image
                            |
                            v
                   Future ECS Deploy
```

> **Built to demonstrate real-world container CI: source-code automation, Docker image creation, AWS authentication, private ECR publishing and the infrastructure foundation required for automated container deployment.**
