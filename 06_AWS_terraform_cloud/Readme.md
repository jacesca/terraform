# Setting ouputs in the terraform configuration

1. Modify the `main.tf` to include the cloud configuration

2. Login to HCP terraform cloud
    ```
    $ terrafon login
    ```
    A token will be required, follow the instructions, copy and paste the token (no caracteres will be shown), and then enter.
    Final lines in response:
    ```
    New to HCP Terraform? Follow these steps to instantly apply an example configuration:
        $ git clone https://github.com/hashicorp/tfc-getting-started.git
        $ cd tfc-getting-started
        $ scripts/setup.sh
   ```

3. After configure the remote backend, reinitialize the project configuration
    ```
    $ terraform init
    ```

4. Now that terraform has migrated your state file to terraform cloud, delete your local state file with 
    ```
    $ rm terraform.tfstate
    ```

5. Complete the configuration of the workspace `Example-Workspace` created in `jacesca` organization in HCP Terraform (Cloud)
    - Go to [HCP Terraform](https://cloud.hashicorp.com/products/terraform)
    - Enter to `jacesca` organization
    - Enter to `Example-Workspace` workspace
    - Select variables and add `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`

6. Run
    ```
    $ terraform apply
    ```

7. Destroy your infrastructure
    ```
    $ terraform destroy
  ```


# Creating an account in HCP Terraform

1. Create an account in [HCP Terraform](https://cloud.hashicorp.com/products/terraform)
2. Create an organization