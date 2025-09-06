# Générer le README.md pour le repo soltania-devops-github-actions-templates-prototype

readme_content = """# soltania-devops-github-actions-templates-prototype

## Overview

This repository contains **reusable GitHub Actions workflows** designed to provide a consistent CI/CD experience across multiple repositories.  
By centralizing workflows here, you can ensure **DRY principles**, simplify updates, and maintain a **single source of truth** for your DevOps automation.

---

## Key Features

- 🛠️ **Reusable workflows**: Share the same CI/CD templates across many repositories.
- ⚡ **Simplified maintenance**: Update one workflow, and all consumers benefit instantly.
- 🔐 **Secure by design**: Supports `secrets: inherit` for seamless authentication.
- 🚀 **Node.js template ready**: Example workflow `nodejs-ci-template.yml` for Node.js projects.

---

## Repository Structure

/
├── .github/
│ └── workflows/
│ └── nodejs-ci-template.yml # Reusable Node.js CI workflow
├── README.md # Project documentation

Toujours afficher les détails


---


## How It Works

Other repositories can **call** these workflows using the `uses:` keyword.  
For example:

```yaml
jobs:
  nodejs-workflow:
    uses: soltani-a/soltania-devops-github-actions-templates-prototype/.github/workflows/nodejs-ci-template.yml@main
    secrets: inherit
    with:
      node-version: '20'
      working-directory: ''

    uses: Points to the reusable workflow hosted in this repository.

    secrets: inherit: Inherits secrets defined in the calling repository.

    with: Passes input variables to customize workflow behavior.

Architecture

The diagram below shows how this repository powers multiple other repositories:

Toujours afficher les détails

graph TD

    A[soltania-devops-github-actions-templates-prototype]:::template

    

    B[soltania-devops-tf-functional-test-bruno]:::repo

    C[soltania-devops-tf-github-prototype]:::repo



    B -->|Calls workflow| A

    C -->|Calls workflow| A



    classDef template fill=#0366d6,stroke=#fff,stroke-width=2px,color=white,font-weight:bold

    classDef repo fill=#28a745,stroke=#fff,stroke-width=2px,color=white

Repositories Using This Template
Repository	Description
soltania-devops-tf-functional-test-bruno
Runs Bruno CLI tests in CI/CD.
soltania-devops-tf-github-prototype
Manages GitHub repositories using Terraform.
Getting Started

    Add a GitHub Actions workflow in your repository (e.g., .github/workflows/main.yml):

Toujours afficher les détails

name: Run Node.js CI
on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  nodejs-workflow:
    uses: soltani-a/soltania-devops-github-actions-templates-prototype/.github/workflows/nodejs-ci-template.yml@main
    secrets: inherit

    Push your changes, and the workflow will execute using this template.

Benefits of a Centralized Workflow Repo

    ✅ Consistency: One source of truth for CI/CD pipelines.

    ✅ Scalability: Add more workflows (e.g., Terraform, Docker, AWS) for all projects.

    ✅ Maintainability: Fix bugs or upgrade tools in one place.

Contributing

Contributions are welcome!

    Fork the repository.

    Create a feature branch:

Toujours afficher les détails

git checkout -b feature/new-workflow

Commit changes:

Toujours afficher les détails

    git commit -m 'Add a new reusable workflow'

    Push and open a Pull Request.

License

This project is licensed under the MIT License - see the LICENSE

file for details.
"""
Écriture du fichier

file_path = "/mnt/data/README_github_actions_templates.md"
with open(file_path, "w") as f:
f.write(readme_content)

file_path
