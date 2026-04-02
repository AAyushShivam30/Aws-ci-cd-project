Automated CI/CD Pipeline for VProfile Java Application on AWS
Overview

This project implements a complete CI/CD pipeline for a multi-tier Java application using the open-source repository:
vprofile-project

The application follows a microservices-style architecture with multiple components such as web server, application server, messaging system, caching layer, and database.

The pipeline automates the process from code commit to containerized deployment on AWS.

Project Objective
Automate build, test, and deployment lifecycle
Ensure code quality using static analysis tools
Store and manage artifacts efficiently
Deploy scalable containerized applications on cloud
Architecture
Application Architecture

The project is a multi-tier web application consisting of:

NGINX (Load Balancer)
Apache Tomcat (Application Server)
RabbitMQ (Messaging Queue)
Memcached (Caching Layer)
MariaDB (Database)
CI/CD Pipeline Flow

Developer → GitHub → Jenkins → Maven Build → SonarQube → Nexus → Docker → AWS ECR → Deployment

CI/CD Pipeline Workflow
1. Source Code Integration
Code is pushed to GitHub repository
Jenkins pipeline is triggered automatically
Branch-based builds are supported (e.g., docker, atom)
2. Build and Test
Maven compiles the project
Generates .war artifact
Executes unit tests to validate code
3. Code Quality Analysis
Checkstyle enforces coding standards
SonarQube performs static analysis
Detects bugs, vulnerabilities, and code smells
4. Quality Gate
Pipeline pauses until SonarQube returns status
Build fails if Quality Gate is not passed
Prevents bad code from progressing
5. Artifact Management
Artifacts are uploaded to Nexus Repository
Ensures version control and traceability
6. Docker Image Creation
Multi-stage Docker build is used
Generates optimized and lightweight image
7. AWS Integration
Jenkins authenticates with AWS
Docker image is pushed to Amazon ECR
Image tagging includes:
Build number
Latest version
8. Continuous Delivery
Local Docker images are removed after push
Deployment-ready images stored in ECR
9. Notifications
Slack integration sends:
Build success/failure status
Logs link for debugging
Tech Stack
CI/CD Tool: Jenkins
Build Tool: Maven
Language: Java (JDK 17)
Code Quality: SonarQube, Checkstyle
Containerization: Docker
Artifact Repository: Nexus
Cloud: AWS (ECR, IAM)
Version Control: Git, GitHub
Messaging: Slack
Prerequisites
Java JDK 17
Maven
Docker
Jenkins
SonarQube Server
Nexus Repository
AWS CLI configured
Git
Vagrant (for local multi-tier setup)
Setup Instructions
1. Clone Repository
git clone https://github.com/hkhcoder/vprofile-project.git
cd vprofile-project
2. Build Application
mvn clean install
3. Run Locally (Optional - Vagrant Setup)
cd vagrant/Manual_provisioning
vagrant up
4. Configure Jenkins Pipeline
Create new pipeline job
Connect GitHub repository
Add credentials (AWS, Nexus, GitHub)
Configure tools (JDK, Maven, Docker)
5. Run Pipeline
Trigger build manually or via commit
Monitor pipeline stages
Check logs for debugging
Project Structure
vprofile-project/
│
├── Jenkinsfile
├── pom.xml
├── Dockerfile
├── src/
│   ├── main/
│   └── test/
├── vagrant/
└── README.md
Key Learning Outcomes
Hands-on experience with CI/CD pipelines
Integration of DevOps tools in real workflow
Containerization and cloud deployment
Code quality enforcement in production pipeline
Future Enhancements
Deploy using Kubernetes (EKS)
Implement Blue-Green Deployment
Add monitoring (Prometheus, Grafana)
Infrastructure as Code using Terraform
Conclusion

This project demonstrates a real-world DevOps implementation using a production-like Java application.
It ensures automation, scalability, and reliability in software delivery.
