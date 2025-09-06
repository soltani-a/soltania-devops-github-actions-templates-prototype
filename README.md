# 🚀 soltania-devops-github-actions-templates-prototype

[![Node.js CI](https://img.shields.io/github/actions/workflow/status/soltani-a/soltania-devops-github-actions-templates-prototype/.github/workflows/nodejs-ci-template.yml?branch=main\&label=Node.js%20CI\&logo=github)](https://github.com/soltani-a/soltania-devops-github-actions-templates-prototype/actions)
[![Reusable Workflow](https://img.shields.io/badge/Reusable-Workflow-green?logo=github-actions)](https://docs.github.com/en/actions/using-workflows/reusing-workflows)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## 📖 Overview

Centralize your CI/CD workflows with **reusable GitHub Actions templates**. This repository allows you to:

* ✅ Apply **DRY principles**
* ✅ Maintain a **single source of truth**
* ✅ Simplify updates across multiple repositories

---

## 📑 Table of Contents

* [Key Features](#-key-features)
* [Repository Structure](#-repository-structure)
* [How It Works](#-how-it-works)
* [Example Workflow](#-example-workflow)
* [Architecture](#-architecture)
* [Repositories Using This Template](#-repositories-using-this-template)
* [Benefits](#-benefits-of-a-centralized-workflow-repo)
* [Contributing](#-contributing)
* [License](#-license)

---

## 🔑 Key Features

* 🛠️ **Reusable workflows**: share CI/CD templates across multiple projects
* ⚡ **Simplified maintenance**: update once, benefit everywhere
* 🔐 **Secure**: supports `secrets: inherit`
* 🚀 **Node.js template ready** (`nodejs-ci-template.yml`)
* 🐳 **Docker-ready workflows**
* 🌍 **Terraform & Cloud workflows**
* 🎨 **Visual diagrams** to understand architecture

---

## 📂 Repository Structure

```text
/
├── .github/
│   └── workflows/
│       └── nodejs-ci-template.yml  # Reusable Node.js CI workflow
├── README.md                       # Project documentation
```

---

## ⚙️ How It Works

Call workflows from another repository:

```yaml
jobs:
  nodejs-workflow:
    uses: soltani-a/soltania-devops-github-actions-templates-prototype/.github/workflows/nodejs-ci-template.yml@main
    secrets: inherit
    with:
      node-version: '20'
      working-directory: ''
```

* **`uses`**: reference the reusable workflow
* **`secrets: inherit`**: automatically uses secrets from the calling repository
* **`with`**: input variables for workflow customization

[View Node.js CI Template](.github/workflows/nodejs-ci-template.yml)

---

## ⚡ Example Workflow

Add this to `.github/workflows/main.yml` in your repository:

```yaml
name: Run Node.js CI
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  nodejs-workflow:
    uses: soltani-a/soltania-devops-github-actions-templates-prototype/.github/workflows/nodejs-ci-template.yml@main
    secrets: inherit
    with:
      node-version: '20'
```

Push your changes and watch the workflow execute automatically.

---

## 🏛 Architecture

```mermaid
graph TD
    A[Workflow Template Repo]:::template
    B[Repo A]:::repo
    C[Repo B]:::repo
    D[Terraform Workflows]:::workflow
    E[Docker Workflows]:::workflow

    B -->|Calls workflow| A
    C -->|Calls workflow| A
    B -->|Calls workflow| D
    C -->|Calls workflow| E

    classDef template fill=#0366d6,stroke=#fff,stroke-width=2px,color=white,font-weight:bold
    classDef repo fill=#28a745,stroke=#fff,stroke-width=2px,color=white
    classDef workflow fill=#f1c40f,stroke=#fff,stroke-width=2px,color=white,font-weight:bold
```

---

## 📦 Repositories Using This Template

| Repository                                                                                                        | Description                                 |
| ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [soltania-devops-tf-functional-test-bruno](https://github.com/soltani-a/soltania-devops-tf-functional-test-bruno) | Runs Bruno CLI tests in CI/CD               |
| [soltania-devops-tf-github-prototype](https://github.com/soltani-a/soltania-devops-tf-github-prototype)           | Manages GitHub repositories using Terraform |

---

## 🌟 Benefits of a Centralized Workflow Repo

* ✅ **Consistency**: one source of truth for pipelines
* ✅ **Scalability**: easily add new workflows (Terraform, Docker, Node.js, AWS)
* ✅ **Maintainability**: fix bugs or upgrade tools in one place
* ✅ **Security**: centralize secrets and authentication best practices

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch:

```bash
git checkout -b feature/new-workflow
```

3. Commit your changes:

```bash
git commit -m 'Add a new reusable workflow'
```

4. Push and open a Pull Request

---

## 📜 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

> 💡 **Tip:** Make your repository “Reusable Workflow Ready” by following GitHub’s [documentation](https://docs.github.com/en/actions/using-workflows/reusing-workflows).
