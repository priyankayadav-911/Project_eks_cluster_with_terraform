<img width="940" height="395" alt="image" src="https://github.com/user-attachments/assets/33641fea-de42-4f3f-9e9f-8e75af868177" />


### Terraform code 

Complete terraform files to create EKS in AWS VPC is available in the `eks-install` folder of this repo. This includes remote backend and statelocking implementation as well.

- `eks-install`: Folder that holds the complete terraform hcl files.
- `backend`: Folder that holds hcl files for s3 bucket and dynamodb creation.
- `modules`: Terraform Modules for VPC and EKS.
- `main.tf`: Main file that invokes the modules to create EKS in VPC.
- `variables.tf`: Variables for main.tf
- `outputs.tf`: Output values you wish to see post terraform execution, For example - `VPC ID`.


### Connect to Jenkins EC2 Server
  `ssh -i your-key.pem ec2-user@your-ec2-ip`
  
### Storing AWS Access & Secret Keys in Jenkins Using Secret Text
### Step 1: Add AWS Credentials as Secret Text
1.	Go to your Jenkins Dashboard
2.	Navigate to:
Manage Jenkins ➝ Credentials ➝ (global) ➝ Add Credentials

### Step 2: Add 1st Credential (AWS Access Key)
-	`Kind`: Secret text
-	`Secret`: <your AWS access key>
-	`ID`: aws-access-key
-	`Description`: AWS Access Key
Click OK

### Add 2nd Credential (AWS Secret Key)
-	`Kind`: Secret text
-	`Secret`: <your AWS secret key>
-	`ID`: aws-secret-key
-	`Description`: AWS Secret Access Key
     Click OK
     
### Setup Jenkins Pipeline
A. Go to Jenkins ➝ New Item ➝ Pipeline
B. Choose “Pipeline” and name it
C. In the pipeline config, choose:

-	Pipeline script from SCM
-	`SCM`: Git
-	`Repository URL`: https://github.com/priyankayadav-911/Project_eks_cluster_with_terraform.git
-	`Script Path`: eks-install/Jenkinsfile

### Trigger the Pipeline
Click “Build Now” in Jenkins to provision the EKS cluster.

### Check:
-	EKS cluster in AWS Console
-	Nodes are in Ready state
-	Jenkins console output shows public IPs and cluster status
