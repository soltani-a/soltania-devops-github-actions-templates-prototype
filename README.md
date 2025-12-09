# 🚀 Soltania DevOps: Centralized GitHub Actions Templates

[![Status](https://img.shields.io/badge/Status-Active-success?style=flat-square)]()
[![Node.js CI](https://img.shields.io/badge/Node.js-CI-green?logo=nodedotjs&logoColor=white&style=flat-square)](.github/workflows/nodejs-ci-template.yml)
[![Python CI](https://img.shields.io/badge/Python-CI-blue?logo=python&logoColor=white&style=flat-square)](.github/workflows/python-ci-template.yml)
[![Terraform CI](https://img.shields.io/badge/Terraform-CI-purple?logo=terraform&logoColor=white&style=flat-square)](.github/workflows/terraform-ci-template.yml)
[![License](https://img.shields.io/badge/License-MIT-lightgrey.svg?style=flat-square)](LICENSE)

---

## 📖 Overview

Welcome to the **Soltania DevOps Centralized Library**. This repository functions as a Shared Service for CI/CD pipelines, acting as the **Single Source of Truth** for automation logic across the organization's ecosystem.

### 🎯 Objective
As a **Solutions Architect**, this repository allows me to:
* **Enforce Governance:** Ensure all projects adhere to the same security and testing standards.
* **Implement DRY Principles:** Define pipeline logic once, apply it everywhere.
* **Accelerate Delivery:** Developers focus on code, not on configuring YAML files.

---

## 🏗 Architecture

The following diagram illustrates the relationship between this centralized template repository and the consumer repositories ("Satellite Repos").

```mermaid
graph TD
    subgraph "Centralized Hub (This Repo)"
        HUB[<b>soltania-devops-templates</b>]:::hub
        NODE(Node.js Workflow):::templ
        PY(Python Workflow):::templ
        TF(Terraform Workflow):::templ
        
        HUB --- NODE
        HUB --- PY
        HUB --- TF
    end

    subgraph "Consumer Ecosystem"
        R1[<b>Functional Tests</b><br/>(Bruno/API)]:::consumer
        R2[<b>Infra Governance</b><br/>(GitHub Provider)]:::consumer
        R3[<b>Future Projects</b>]:::consumer
    end

    R1 -.->|Inherits| TF
    R2 -.->|Inherits| TF
    R3 -.->|Inherits| NODE

    classDef hub fill:#2c3e50,stroke:#fff,stroke-width:2px,color:#fff
    classDef templ fill:#34495e,stroke:#95a5a6,color:#fff
    classDef consumer fill:#27ae60,stroke:#fff,stroke-width:2px,color:#fff
````

-----

## 📦 Available Workflows & Usage

To use a workflow, create a YAML file in your repository (e.g., `.github/workflows/ci.yml`) and reference the specific template.

### 🟢 Node.js CI

*Standardizes linting, testing, and building for Node applications.*

| Input | Description | Default |
| :--- | :--- | :--- |
| `node-version` | The specific Node.js version to use. | `20` |
| `working-dir` | The directory containing package.json. | `.` |

```yaml
jobs:
  build:
    uses: soltani-a/soltania-devops-github-actions-templates-prototype/.github/workflows/nodejs-ci-template.yml@main
    secrets: inherit
    with:
      node-version: '20'
```

### 🔵 Python CI

*Handles Python dependency installation, Linting (Flake8), and Testing (Pytest).*

```yaml
jobs:
  test:
    uses: soltani-a/soltania-devops-github-actions-templates-prototype/.github/workflows/python-ci-template.yml@main
    secrets: inherit
    with:
      python-version: '3.10'
```

### 🟣 Terraform CI

*Manages the Infrastructure as Code lifecycle: Formatting, Validation, Linting, and Planning.*

```yaml
jobs:
  terraform:
    uses: soltani-a/soltania-devops-github-actions-templates-prototype/.github/workflows/terraform-ci-template.yml@main
    secrets: inherit
    with:
      tf-version: '1.5.0'
```

-----

## 🌍 Portfolio: Repositories Using This Template

This section demonstrates the **scalability** of this architecture. The following repositories currently rely on these centralized templates for their CI/CD:

| Repository | Domain | Template Used | Purpose |
| :--- | :--- | :---: | :--- |
| [**soltania-devops-tf-functional-test-bruno**](https://github.com/soltani-a/soltania-devops-tf-functional-test-bruno) | 🧪 QA / Testing | `Terraform` | Automating functional API testing using the Bruno CLI tool. |
| [**soltania-devops-tf-github-prototype**](https://github.com/soltani-a/soltania-devops-tf-github-prototype) | 🛡️ Governance | `Terraform` | Managing GitHub repositories, teams, and permissions via IaC. |

-----

## 🤝 Contributing & Governance

Contributions are welcome\! If you wish to add a new workflow or improve an existing one, please follow these steps:

1.  **Fork** the repository.
2.  Create a **Feature Branch** (`git checkout -b feature/new-template`).
3.  **Test Locally** using `nektos/act` or a private fork.
4.  Open a **Pull Request**.

-----

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](https://www.google.com/search?q=LICENSE) file for details.