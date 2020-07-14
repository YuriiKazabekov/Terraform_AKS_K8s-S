 <h1 align="center"> terraform-aks-k8s
 </h1>
 
GL DevOps Pro Camp
Terraform code that deploys Azure Kubernetes Service

## Set up Azure storage to store Terraform state
Terraform tracks state locally via the terraform.tfstate file.

## Select Storage accounts.
On the Storage accounts tab, select the name of the storage account into which Terraform is to store state. 
On the storage account tab, select Access keys.
Make note of the key1 key value. (Selecting the icon to the right of the key copies the value to the clipboard.)

## Create the Kubernetes cluster
In Cloud Shell, initialize Terraform. Replace the placeholders with appropriate values for your environment:

*terraform init -backend-config="storage_account_name=<YourAzureStorageAccountName>" -backend-config="container_name=tfstate" -backend-config="access_key= <YourStorageAccountAccessKey>" -backend-config="key=codelab.microsoft.tfstate"*
  
 Export your service principal credentials. Replace the placeholders with appropriate values from your service principal.
 
 *export TF_VAR_client_id=<service-principal-appid>*
 *export TF_VAR_client_secret=<service-principal-password>*
  
 Run the terraform plan command to create the Terraform plan that defines the infrastructure elements
 
 *terraform plan -out out.plan*
  
 Apply the plan to create the Kubernetes cluster
 
 *terraform apply out.plan*
  
 #### In the Azure portal, select All resources in the left menu to see the resources created for your new Kubernetes cluster.
