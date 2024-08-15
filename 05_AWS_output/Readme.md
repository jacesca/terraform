# Setting ouputs in the terraform configuration

1. Create `variables.tf` to have the variable `instance_name`
2. Create `main.tf`, and call the variable `instance_name` for the component we need.
3. Create `output.tf` with the data we need to print out when `terraform apply` is executed.
4. Appy the changes, by running 
    ```
    terraform init
    terraform apply
    ```
5. Run the following code to have the data in any moment.
```
$ terraform output
```
6. Destroy the instance
    ```
    $ terraform destroy
    ```
