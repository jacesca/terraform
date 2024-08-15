# Using variables with terraform

1. Create `variables.tf` to have the variable `instance_name`
2. Create `main.tf`, and call the variable `instance_name` for the component we need.
3. Apply changes
    ```
    $ terraform init
    $ terraform apply
    ```
4. Override the instance name again but in the command line
    ```
    $ terraform apply -var "instance_name=YetAnotherName"
    ```
5. Destroy the instance
    ```
    $ terraform destroy
    ```