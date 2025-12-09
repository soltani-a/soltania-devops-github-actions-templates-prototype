# Contributing to Soltania DevOps Templates

First off, thank you for considering contributing to this repository! 🚀

As a **Centralized CI/CD Library**, this repository serves multiple downstream projects. Therefore, stability, backward compatibility, and clear documentation are our top priorities.

This document outlines the guidelines for contributing to these templates to ensure a high standard of quality and governance.

---

## 📋 The Development Lifecycle

### 1. Discuss First
Before writing code, please **open an issue** to discuss the proposed change.
* **For new workflows:** Explain the use case and the inputs/outputs.
* **For modifications:** Explain why the change is necessary and if it introduces breaking changes.

### 2. Local Development & Linting
Since testing GitHub Actions can be slow (requires pushing to test), we highly recommend using local tools to validate your syntax before pushing.

* **Linting:** We use [actionlint](https://github.com/rhysd/actionlint) to ensure YAML syntax is valid.
  ```bash
  # Example usage
  docker run --rm -v "$(pwd):$(pwd)" -w "$(pwd)" rhysd/actionlint:latest
````

### 3\. Branching Strategy

Please use descriptive branch names following this convention:

  * `feature/description` (e.g., `feature/add-docker-workflow`)
  * `fix/description` (e.g., `fix/terraform-input-typo`)
  * `docs/description` (e.g., `docs/update-readme`)

-----

## 🛡️ Versioning Policy (Critical)

As an Architect, we must ensure **Consumer Stability**. Downstream repositories rely on these templates.

### Semantic Versioning

We follow [Semantic Versioning 2.0.0](https://semver.org/):

  * **Major (v2.0.0):** Breaking changes (e.g., renaming a required input, removing a job).
  * **Minor (v1.1.0):** New features (e.g., adding a new optional input, adding a new workflow).
  * **Patch (v1.0.1):** Bug fixes or internal logic improvements that do not change the interface.

> ⚠️ **Important:** If you modify an input name or a secret requirement, this is a **Breaking Change**. You must update the major version.

-----

## 📝 Commit Convention

We use **Conventional Commits** to streamline our history and changelogs.

```text
<type>(<scope>): <subject>
```

**Types:**

  * `feat`: A new workflow or feature.
  * `fix`: A bug fix.
  * `docs`: Documentation only changes.
  * `style`: Formatting, missing semi-colons, etc.
  * `refactor`: A code change that neither fixes a bug nor adds a feature.
  * `ci`: Changes to our own CI configuration.

**Example:**

> `feat(node): add caching support for npm dependencies`

-----

## 🚀 Pull Request Checklist

When you open a Pull Request, please ensure the following:

1.  [ ] **Documentation:** The `README.md` is updated with new inputs/outputs if applicable.
2.  [ ] **Linting:** The YAML files pass `actionlint`.
3.  [ ] **Backward Compatibility:** You have verified that existing projects using `@main` will not break (unless discussed).
4.  [ ] **Test Plan:** Describe how you verified that the workflow works (e.g., "Tested on a private fork").

-----

## 🤝 Code of Conduct

This project is intended to be a safe, welcoming space for collaboration. 
Please review and abide by our [Code of Conduct](CODE_OF_CONDUCT.md).

Happy Automating!