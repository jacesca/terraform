# Terraform Quick Review

## Quick steps (with dockers)
Initialize the project. It will look for main.tf
```
$ terraform init
```

To show the changes to apply
```
$ terraform plan
```

To apply changes
```
$ terraform apply
```

To stop the container
```
$ terraform destroy
```

To format terraform files
```
$ terraform fmt
```

To make sure your configuration is syntactically valid and internally consistent
```
$ terraform validate
```

To Inspect the current state
```
$ terraform show
```

To list of the resources in your project's state
```
$ terraform state list
```

## Terraform components
- When `terraform init` is executed, Terraform downloads the provider and install it in a hidden folder `.terraform` and create the file `.terraform.lock.hcl`, which specifies the exact provider versions used.
- When `terraform apply` is executed, Terraform wrote data into a file called `terraform.tfstate`.


## Steps to install it (Local Windows)
1. Install [Chocolatery](https://chocolatey.org/install)
    - Choose Individual
    - Open Powershell as administrator
    - Review that `Get-ExecutionPolicy` is not Restricted, by running
        ```
        $ Get-ExecutionPolicy
        ```
    - If restricted is returned, run
        ```
        Set-ExecutionPolicy Bypass -Scope Process
        ```
    - Run
        ```
        $ Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
        ```
    - Once it is installed, you can verify it by running:
        ```
        $ choco -?
        ```

2. Install Terraform
    ```
    choco install terraform
    ```

3. Verify the installation
    ```
    $ terraform -help
    $ terraform -help plan
    ```

4. Enable tab completion
    - Ensure that the configuration file exists. To create one, run 
        ```
        $ ni ~/.bashrc
        ```
    - Run
        ```
        $ terraform -install-autocomplete
        ```

5. Install docker

> For AWS specifically

6. Install [AWS Cli](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html). Once installed you can confirm it by runing
    ```
    $ aws --version
    ```

7. Configure an IAM user for accessing AWS since terraform. Follow [this guide](https://medium.com/@CloudTopG/discover-the-3-steps-to-creating-an-iam-user-with-access-secret-access-keys-for-terraform-scripts-28110e280460).
    - Go to IAM console in AWS and create a new user.
    - Provide a name and not enable console access.
    - Set permission by ataching it to a policy: Administrator Acess (AWS managed - job function)
    - Once it is created, enter to the user and select security credentials
    - Create access key and select Local code
    - Download the file with the Access key and Secret access key

8. Add access and secret access key to AWS CLI
    * Method 1: Configuring AWS Cli
        - Run
            ```
            $ aws configure
                AWS Access Key ID [None]: ...
                AWS Secret Access Key [None]: ...
                Default region name [None]: us-east-1  ← p.e.
                Default output format [None]: json
            ```

    * Method 2: Setting environment variables for the current session (temporary)
        - Run in powershell:
            ```
            $ $env:AWS_ACCESS_KEY_ID="..."
            $ $env:AWS_SECRET_ACCESS_KEY="..."
            $ $env:AWS_DEFAULT_REGION="us-west-2"
            ```

    * Method 3: Create a terraform env file:
        - File name: `variables.tf` (Do not save it to any repository)
        - File content:
            ```
            variable "access_key" {
                default = "..."
            }
            variable "secret_key" {
                default = "..."
            }
            ```

            We can call it in our implementation as follow:
            any terraform file.tf
            
            ```
            provider "aws" {
                region = "us-west-2"
                access_key = var.access_key
                secret_key = var.secret_key
            }
            ```

More information:
- Review other environments [here](https://developer.hashicorp.com/terraform/tutorials/docker-get-started/install-cli).
- [Terraform Registry](https://registry.terraform.io/)
- [Provider source documentation](https://developer.hashicorp.com/terraform/language/providers/requirements)