# NGINX Server deployment with terraform
Objective: 
> Provision an NGINX server using Docker on Windows.

1. Open the powershell as administrator
2. Go to this directory
3. Initiate the project
    ```
    $ terraform init
    ```
4. Show changes to apply
    ```
    $ terraform plan
    ```
5. Apply changes
    ```
    $ terraform apply
    ```
6. Verify the existence of the NGINX container by visiting http://localhost:8000 in your web browser or running:
    ```
    docker ps
    ```

7. Stop the container:
    ```
    terraform destroy
    ```