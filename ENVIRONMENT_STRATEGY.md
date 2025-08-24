# [ENVIRONMENT STRATEGY]

**Date:** YYYY-MM-DD
**Owner:** DevOps Engineer
**Status:** Accepted

## 1. Chosen Strategy
A clear statement of the selected approach.
> *Example: "This project will use a single monorepo with separate directories for each environment to ensure maximum isolation and clarity."*

## 2. Justification
The reasoning behind the choice, linking back to project requirements.
> *Example: "The separate directory approach was chosen over Terraform Workspaces to prevent accidental application of dev variables to production and to allow for structural differences between environments (e.g., no HA setup in dev)."*

## 3. Implementation Details

### Directory Structure:
A visual representation of the Terraform file organization.
`
terraform/
├── environments/
│   ├── dev/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── backend.tfvars
│   └── prod/
│       ├── main.tf
│       ├── variables.tf
│       └── backend.tfvars
└── modules/
    ├── vpc/
    └── fargate/
`

### State Management:
How Terraform state files will be isolated.
> *Example: "The S3 backend key will be prefixed with the environment name, e.g., `tfstate/auth-service/dev/terraform.tfstate`."*

### Variable Management:
How environment-specific variables will be handled.
> *Example: "Each environment directory will contain its own `.tfvars` file. No default values will be set in the module `variables.tf` files."*

## 4. Trade-offs
A brief acknowledgement of the downsides of this approach.
> *Example: "This approach leads to some code duplication between environment configurations, but this is an acceptable trade-off for the safety and isolation it provides."*
