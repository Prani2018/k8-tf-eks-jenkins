# k8-tf-eks-jenkins
.
|-- Jenkinsfile                                # This is the main build pipeline definition
|-- Kubernetes
|   |-- nginx-deployment.yaml                  # The Kubernetes deployment for the NGINX web server
|   |-- nginx-service.yaml                     # The Kubernetes service for the NGINX web server
|   |-- terraform.tfstate                      # State file for Kubernetes infrastructure (DO NOT MODIFY MANUALLY)
|   |-- tomcat-deployment.yaml                 # The Kubernetes deployment for the Tomcat application
|   `-- tomcat-service.yaml                    # The Kubernetes service for the Tomcat application
|-- README.md                                  # Project documentation
|-- backend.tf                                 # Terraform backend configuration for shared state
|-- eks-cluster
|   |-- backend.tf                             # Terraform backend for the EKS cluster
|   |-- eks.tf                                 # Defines the EKS cluster resources
|   |-- terraform.tfstate                      # State file for EKS cluster
|   |-- terraform.tfstate.backup               # Backup state file for EKS cluster
|   |-- terraform.tfvars                       # Variables for EKS cluster configuration
|   |-- variables.tf                           # Variable definitions for EKS cluster
|   `-- vpc.tf                                 # Defines the VPC for the EKS cluster
|-- jenkins-script.sh                          # Script executed by the Jenkins pipeline
|-- kk.pem                                     # SSH key pair for accessing instances
|-- outputs.tf                                 # Terraform outputs for infrastructure details
|-- provider.tf                                # Terraform provider configuration
|-- route.tf                                   # Terraform configuration for network routing
|-- security.tf                                # Terraform configuration for security groups
|-- server.tf                                  # Terraform configuration for compute resources
|-- terraform.tfvars                           # Terraform variables for this project
|-- variables.tf                               # Terraform variable definitions
`-- vpc.tf                                     # Terraform configuration for the VPC


Step1: Create s3 bucket to store the terraform statefile with the same name as in backed file.
Step2: From k8-tf-eks-jenkins directory, run commands
       terraform init
       terraform validate
       terraform plan
       terraform apply
Step3: Setup Jenkins and create Node and maven installation label, and run node agent on build server.
       Run Groovy scripts available to create them 
Step4: Create jenkins pipeline job using the JenkinsPipeline to create EKS-CLUSTER and deploy pods.
