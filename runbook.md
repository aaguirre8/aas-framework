# RUNBOOK: [Action-Oriented Title, e.g., Manually Scale Fargate Service]

**Owner:** [e.g., DevOps Engineer]
**Last Updated:** YYYY-MM-DD

## 1. When to Use This Runbook
The specific conditions or alerts that would trigger this procedure.
> *Example: "Use this runbook when CloudWatch CPU Utilization alarms for the Fargate service have been triggered for more than 5 minutes."*

## 2. Pre-requisites
- **Tools:** [e.g., AWS CLI v2, Terraform v1.5+]
- **Permissions:** [e.g., Assumed IAM Role `MyProject-DevOps-Role`]
- **Context:** [e.g., You must know the `cluster_name` and `service_name` to target.]

## 3. Step-by-Step Procedure
A numbered list of commands to run and actions to take.

1.  **Authenticate with AWS:**
    ```bash
    # Ensure your local environment is configured with the correct credentials.
    aws sts get-caller-identity
    ```
2.  **Update the Terraform Variable:**
    Navigate to the correct environment directory (e.g., `terraform/environments/prod/`) and update the `desired_count` variable in the `fargate.tfvars` file.
3.  **Apply the Terraform Change:**
    ```bash
    # Initialize and apply the change.
    terraform init
    terraform apply -var-file="prod.tfvars"
    ```

## 4. Verification
How to confirm the procedure was successful.
> *Example: "Check the AWS ECS console to confirm that the 'desired task count' for the service has been updated and new tasks are spinning up."*

## 5. Rollback Plan
How to undo the changes if something goes wrong.
> *Example: "Revert the change to the `desired_count` variable in the `.tfvars` file and re-run `terraform apply`."*
