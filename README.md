# Terraform GitHub Repository Demo Project

This project demonstrates how to use Terraform modules to create actual GitHub repositories and generate a Markdown information page.

## Prerequisites

1. **GitHub Personal Access Token**: Create a token with `repo` permissions at https://github.com/settings/tokens
2. **Terraform**: Install Terraform CLI

## Project Structure

```
terraform-demo-project/
├── main.tf              # Main configuration with GitHub provider
├── variables.tf         # Root variables
├── outputs.tf          # Root outputs
├── README.md           # This file
└── modules/
    ├── repositories/   # Creates actual GitHub repositories
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    └── infopage/      # Creates GitHub repository with Markdown info page
        ├── main.tf
        ├── variables.tf
        └── outputs.tf
```

## How it works

1. **repositories module**: Creates real GitHub repositories with README and main files
2. **infopage module**: Takes repository data and creates a GitHub repository with a Markdown information page
3. **Module interaction**: Outputs from repositories module are passed as inputs to infopage module

## Setup

1. Set your GitHub token as an environment variable:
   ```bash
   export GITHUB_TOKEN="your_github_token_here"
   ```

2. Initialize Terraform:
   ```bash
   terraform init
   ```

## Usage

1. Plan the deployment:
   ```bash
   terraform plan
   ```

2. Apply the configuration:
   ```bash
   terraform apply
   ```

3. Check your GitHub account for the created repositories:
   - `backend-repo`
   - `frontend-repo` 
   - `infra-repo`
   - `docs-repo`
   - `information-page`

## What gets created

- **4 GitHub repositories** with appropriate files for each language (backend, frontend, infra, docs)
- **GitHub Pages** enabled for frontend and backend repos
- **Information page repository** with Markdown table showing all repository details
- **README files** in each repository explaining the project

## Key Learning Points

- How to use the GitHub provider in Terraform
- How to pass outputs from one module to another
- Using local variables and dynamic blocks
- Template generation with real data
- Handling null values in templates

## Clean up

To remove all created resources:
```bash
terraform destroy
```

**Note**: This will delete the GitHub repositories permanently!