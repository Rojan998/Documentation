# Setting Up Terraform

Terraform is an open-source infrastructure as code (IaC) tool that allows you to define and provision infrastructure using a declarative configuration language.

## Prerequisites

1. **Install Terraform**:

   - Download Terraform from the [official website](https://www.terraform.io/downloads.html).
   - Follow the installation instructions for your operating system.

2. **Verify Installation**:

   ```bash
   terraform --version
   ```

3. **Install a Cloud Provider CLI** (e.g., AWS CLI, Azure CLI, or Google Cloud SDK) if you plan to manage cloud resources.

## Steps to Set Up Terraform

### 1. Create a Working Directory

Create a directory for your Terraform configuration files:

```bash
mkdir terraform-setup
cd terraform-setup
```

### 2. Write a Configuration File

Create a file named `main.tf`:

```hcl
provider "aws" {
  region = "us-west-2"
}

resource "aws_s3_bucket" "example" {
  bucket = "my-unique-bucket-name"
  acl    = "private"
}
```

### 3. Initialize Terraform

Run the following command to initialize the working directory:

```bash
terraform init
```

### 4. Format and Validate Configuration

- Format the configuration:
  ```bash
  terraform fmt
  ```
- Validate the configuration:
  ```bash
  terraform validate
  ```

### 5. Plan the Infrastructure

Generate an execution plan:

```bash
terraform plan
```

### 6. Apply the Configuration

Apply the changes to create the resources:

```bash
terraform apply
```

### 7. Destroy the Infrastructure

To clean up resources, run:

```bash
terraform destroy
```

## Additional Resources

- [Terraform Documentation](https://www.terraform.io/docs)
- [Terraform Registry](https://registry.terraform.io/)
