# Kubernetes DevSecOps CICD Project Using Github Actions and ArgoCD

## Start by building the infrastrcuture which can be seen in the terraform/ 

![gif2](https://github.com/cloudcore-hub/reactjs-quiz-app/assets/88560609/a0dfce93-3bde-45af-b82a-d7c9e2c47294)


- [Step 1: SSH Exchange between local computer and Github account.](#step-1-ssh-exchange-between-local-computer-and-github-account)
- [Step 2: CREATE AWS Resources.](#step-2-create-aws-resources)
- [Step 3: Install Terraform & AWS CLI.](#step-3-install-terraform--aws-cli)
- [Step 4: Deploy the Jumphost Server(EC2) using Terraform on Github Actions.](#step-4-deploy-the-jumphost-server-ec2-using-terraform-on-github-actions)
- [Step 5: Configure the Jumphost.](#step-5-configure-the-jumphost)
- [Step 6: Setup Docker Repositories to allow image push for Frontend & Backend images.](#step-6-setup-docker-repositories-to-allow-image-push-for-frontend--backend-images)
- [Step 7: Configure Sonar Cloud for our app_code Pipeline.](#step-7-configure-sonar-cloud-for-our-app_code-pipeline)
- [Step 8: Setup Synk Token for the app code pipeline.](#step-8-setup-synk-token-for-the-app-code-pipeline)
- [Step 9: Review and Deploy Application Code.](#step-9-review-and-deploy-application-code)
- [Step 10: Configure ArgoCD.](#step-10-configure-argocd)
- [Step 11: Set up the Monitoring for our EKS Cluster using Prometheus and Grafana.](#step-11-set-up-the-monitoring-for-our-eks-cluster-using-prometheus-and-grafana)
- [Step 12: Deploy Quiz Application using ArgoCD.](#step-12-deploy-quiz-application-using-argocd)
- [Step 13: Creating an A-Record in AWS Route 53 Using ALB DNS.](#step-13-creating-an-a-record-in-aws-route-53-using-alb-dns)
- [Step 14: Clean up.](#step-14-clean-up)
- [Conclusion](#conclusion)


## Project Introduction:
Welcome to my End-to-End DevSecOps Kubernetes Project! In this project, I set up a solid Three-Tier architecture on AWS, combining Kubernetes, DevOps best practices, and security measures. This guide reflects my hands-on experience in deploying, securing, and monitoring a scalable application environment. It's designed to offer practical knowledge for anyone looking to build secure and efficient cloud-based systems.

### Project Overview:
In this project, I explored several key areas:

1. **IAM User Setup:** I created an IAM user on AWS with the permissions needed for deployment and management tasks.
2. **Infrastructure as Code (IaC):** I utilized Terraform and the AWS CLI to set up a Jumphost server (EC2 instance) on AWS.
3. **GitHub Actions Configuration:** I configured essential GitHub Actions workflows, incorporating Snyk, Docker, SonarQube, Terraform, kubectl, AWS CLI, and Trivy.
4. **EKS Cluster Deployment:** I employed `eksctl` commands to create an Amazon EKS cluster, a managed Kubernetes service on AWS.
5. **Load Balancer Configuration:** I set up an AWS Application Load Balancer (ALB) for the EKS cluster.
6. **Docker Hub Repositories:** I automated the creation of repositories for both frontend and backend Docker images on Docker Hub.
7. **ArgoCD Installation:** I installed and configured ArgoCD to enable continuous delivery and GitOps.
8. **SonarQube Integration:** I integrated SonarQube to analyze code quality in the DevSecOps pipeline.
9. **Snyk Integration:** I incorporated Snyk for vulnerability scanning and dependency management analysis within the pipeline.
10. **Trivy Integration:** I added Trivy to scan container images and filesystems for vulnerabilities in the pipeline.
11. **GitHub Action Pipelines:** I created GitHub Action pipelines for deploying the backend and frontend code to the EKS cluster.
12. **Monitoring Setup:** I implemented monitoring for the EKS cluster using Helm, Prometheus, and Grafana.
13. **ArgoCD Application Deployment:** I used ArgoCD to deploy the Three-Tier application, which includes the database, backend, frontend, and ingress components.
14. **DNS Configuration:** I configured DNS settings to make the application accessible via custom subdomains.
15. **Data Persistence:** I implemented persistent volumes and persistent volume claims for the database pods to ensure data persistence.
16. **Conclusion and Monitoring:** I wrapped up the project by summarizing the key achievements and monitored the performance of the EKS cluster using Grafana.

### Prerequisites:
Before starting this project, make sure you have the following:

- An AWS account with the necessary permissions to create resources.
- Terraform and AWS CLI installed on your local machine.
- - Basic familiarity with Kubernetes, Docker, CICD pipelines, Github Actions, Terraform, and DevOps principles.







### Create Infrastrcture Branch
This branch checks and ensures the enture infarstructure of the application is running successfully. 

```
git add .
git commit -m "Adding infrastrcuture code"
git push origin infrastructure
```


### Connect To The Jumperhost Instance
- Ensure you have created your key pair and downloaded it to your local machine
- Change the permissions of the key pair
```
chmod 400 /path/to/your-key-file.pem

ssh -i  /path/to/your-key-file.pem
```