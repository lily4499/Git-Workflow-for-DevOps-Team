# Git-Workflow-for-DevOps-Team


```markdown
# 🚀 Git Workflow for DevOps Team

## ✅ Objective

Set up a professional Git workflow that includes:

- GitHub repository creation  
- Branch protection rules  
- GitHub Actions for validation  
- Pre-commit hooks  
- Semantic versioning and tags  

---

## 🛠️ Tech Stack

- **GitHub**: Repository hosting and collaboration  
- **Git**: Version control via CLI  
- **pre-commit**: Automate checks before commits  
- **GitHub Actions**: CI workflows like linting or tests  

---

## 🧱 Step-by-Step Implementation

### 🧩 Step 1: Create the GitHub Repo

This is the central place where your DevOps team stores and collaborates on code. Using GitHub also allows integration with CI/CD tools, issue tracking, and automation.

🔗 [Create New Repo](https://github.com/new)  
Manually create a new repository named `devops-git-workflow`. Or use CLI:

```bash
gh repo create devops-git-workflow \
  --public \
  --description "Git workflow for DevOps with protection rules, GitHub Actions, and pre-commit hooks" \
  --confirm
```

---

### 🧩 Step 2: Clone the Repo Locally

This copies the GitHub repository to your local machine so you can work on files, commit changes, test, and push updates. It’s the standard way developers interact with the repo.

```bash
git clone https://github.com/<your-username>/devops-git-workflow.git
cd devops-git-workflow
```

---

### 🧩 Step 3: Set Up Branch Protection Rules
Branch protection ensures no one can directly push to the main branch without code reviews and passing automated tests. This:
  - Prevents breaking changes
  - Enforces team collaboration
  - Ensures code quality via CI checks
Example rule: ✅ "Require pull request review before merging"


On GitHub:

1. Go to **Settings → Branches**
2. Click “Add rule”
3. Set branch name pattern: `main`
4. Enable:
   - ✅ Require pull request reviews before merging  
   - ✅ Require status checks to pass before merging  
   - ✅ Require branches to be up to date before merging  

🔐 *This enforces code quality and team collaboration.*

---

### 🧩 Step 4: Add a GitHub Action for Linting/Validation
This step sets up automated CI that runs every time someone pushes code or creates a pull request. It:  
  - Automatically checks code for syntax issues, formatting, or style errors (like eslint, flake8, or shellcheck)  
  - Helps maintain clean and error-free code  
  - Prevents bad code from entering the main branch  

Create a CI workflow file:

```bash
mkdir -p .github/workflows
nano .github/workflows/lint.yml
```

Paste:

```yaml
name: Lint Check

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install ESLint
        run: npm install eslint --save-dev
      - name: Run Lint
        run: npx eslint . || true
```

You can replace `eslint` with Python (`flake8`), YAML (`yamllint`), Shell (`shellcheck`), etc.

Initialize Node + ESLint:

```bash
npm init -y
npm install eslint --save-dev
npx eslint --init
```

---

### 🧩 Step 5: Add Pre-Commit Hooks

Pre-commit hooks run before you commit code locally to catch small errors like:  
  - Trailing whitespace  
  - Missing end-of-file newlines  
  - Malformed YAML or JSON  
This helps avoid careless mistakes and keeps code clean before it even reaches GitHub.  

#### 1. Install pre-commit:

```bash
pip install pre-commit
```

#### 2. Create `.pre-commit-config.yaml`:

```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
```

#### 3. Install the hook scripts:

```bash
pre-commit install
```

#### 4. Run hooks on all files:

```bash
pre-commit run --all-files
```

---

### 🧩 Step 6: Semantic Versioning and Git Tags

Tags are like version numbers (e.g., v1.0.0) that let you:
  - Mark stable releases
  - Roll back to older versions if needed
  - Use in automated deployments (CI/CD can trigger on tags)

Semantic versioning helps organize changes:  
  - v1.0.0 — major release
  - v1.1.0 — new features
  - v1.1.1 — bug fixes only

#### 🌱 Commit best practices:

Use meaningful commit prefixes:
```bash
feat: add new feature
fix: fix bug in workflow
chore: update config
```

#### 🏷️ Tag a Release:

```bash
git tag -a v1.0.0 -m "Initial stable release"
git push origin v1.0.0
```

🔁 Use `v1.1.0`, `v2.0.0`, etc. for feature/breaking changes.

---

## ✅ Final Outcome

| Feature                     | Implemented |
|----------------------------|-------------|
| GitHub Repo                | ✅           |
| Branch Protection          | ✅           |
| GitHub Actions CI          | ✅           |
| Pre-commit Hooks           | ✅           |
| Semantic Versioning & Tags | ✅           |

---

## 🧾 Summary

This project provides a **collaborative, secure, and automated Git workflow** tailored for DevOps teams.  
It enforces:
- Peer-reviewed pull requests  
- Automated linting via GitHub Actions  
- Local pre-commit checks  
- Release tracking via version tags  

A best-practice workflow ready for CI/CD and production!

---
```

