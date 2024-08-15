# Making changes in Terraform

1. Create the `main.tf` file
    ```
    terraform {
        required_providers {
            aws = {
                source  = "hashicorp/aws"
                version = "~>4.16"
            }
        }
        required_version = ">=1.2.0"
    }

    provider "aws" {
        region = "us-west-2"
    }

    resource "aws_instance" "app_server" {
        ami = "ami-830c94e3"
        instance_type = "t2.micro"

        tags = {
            Name = "ExampleAppServerInstance"
        }
    }
    ```
2. Apply the configuration
    ```
    $ terraform init
    $ terraform fmt
    $ terraform validate
    $ terraform plan
    $ terraform apply
    ```
3. Make changes to the `main.tf`
    ```

    ...
    resource "aws_instance" "app_server" {
        ami = "ami-08d70e59c07c61a3a"
    ...

    ```
4. After changing the configuration, run the following command again to see how Terraform will apply this change to the existing resources.
    ```
    $ terraform apply
    ```
5. Print out the new values associated with this instance.
    ```
    $ terraform show
    ```
6. Destroy the created resources
    ```
    $ terraform destroy
    ```