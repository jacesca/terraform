# Single AWS EC2 instance

Objective: 
> Define a single AWS EC2 instance.

The ID for the EC2 instance defined in the terraform file will be `aws_instance.app_server`.

1. Open the powershell as administrator
2. Go to this directory
3. Initiate the project
    ```
    $ terraform init
    ```
4. Format all terraform files
    ```
    terraform fmt
    ```
5. Validate your configuration
    ```
    $ terraform validate
    ```
6. Examinate changes to apply
    ```
    $ terraform plan
    ```
7. Apply changes
    ```
    $ terraform apply
    ```
8. Visit the [EC2 console](https://console.aws.amazon.com/ec2/v2/home?region=us-west-2#Instances:sort=instanceId) and find your new EC2 instance.
9. Inspect the current state
    ```
    $ terraform show
    ```
10. List of the resources in your project's state
    ```
    $ terraform state list
    ```
7. Stop the container:
    ```
    $ terraform destroy
    ```

Others:
    - In this configuration, the aws provider's source is defined as `hashicorp/aws`, which is shorthand for `registry.terraform.io/hashicorp/aws`.