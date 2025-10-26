# Contributing to DevOps Project Demo

Thank you for your interest in contributing to this project! This guide will help you understand our development workflow and best practices.

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ranji790/devops-project-demo.git
cd devops-project-demo
```

### 2. Set Up Your Environment

```bash
# Create virtual environment
python -m venv venv

# Activate it
venv\Scripts\activate  # Windows
source venv/bin/activate  # Mac/Linux

# Install dependencies
pip install -r requirements.txt
```

## Branching Strategy (GitFlow)

### Main Branches
- **main**: Production-ready code (protected branch)
- **dev**: Development integration branch (protected branch)

### Supporting Branches
- **feature/feature-name**: New features (branch from dev)
- **bugfix/bug-name**: Bug fixes (branch from dev)
- **hotfix/hotfix-name**: Emergency production fixes (branch from main)
- **release/version**: Release preparation (branch from dev)

## Development Workflow

### Step 1: Create Feature Branch

```bash
git checkout dev
git pull origin dev
git checkout -b feature/your-feature-name
```

### Step 2: Make Changes and Commit

```bash
# Make your changes
git add .
git commit -m "feat(scope): describe your change

Add details about what you changed
Explain why you made this change
Reference issue number if applicable

Closes #123"
```

### Step 3: Push and Create Pull Request

```bash
git push -u origin feature/your-feature-name
```

Then create a PR on GitHub and ask for review.

### Step 4: Code Review and Merge
- Wait for at least 1 approval
- Address any feedback
- Merge to dev branch
- Delete your feature branch

## Commit Message Convention

Use the format: `<type>(<scope>): <subject>`

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation
- `style`: Code formatting
- `refactor`: Code refactoring
- `test`: Adding tests
- `chore`: Maintenance
- `ci`: CI/CD changes

**Examples:**

```bash
git commit -m "feat(auth): add JWT authentication"
git commit -m "fix(api): resolve timeout issue"
git commit -m "docs(readme): update setup instructions"
```

## Release Process

### Creating a Release

```bash
# Create release branch
git checkout -b release/v1.1.0 dev

# Update version numbers, changelog, etc.
# Test thoroughly

# Merge to main
git checkout main
git merge --no-ff release/v1.1.0
git tag -a v1.1.0 -m "Release v1.1.0"
git push origin main --tags

# Merge back to dev
git checkout dev
git merge release/v1.1.0
git push origin dev

# Delete release branch
git branch -d release/v1.1.0
```

## Emergency Hotfix

```bash
# Create hotfix from main
git checkout -b hotfix/critical-issue main

# Fix the issue
git commit -m "fix(security): patch critical issue"

# Merge to main and tag
git checkout main
git merge --no-ff hotfix/critical-issue
git tag -a v1.0.1 -m "Hotfix v1.0.1"

# Merge to dev
git checkout dev
git merge hotfix/critical-issue

# Clean up
git branch -d hotfix/critical-issue
```

## Best Practices

✓ Commit frequently with meaningful messages  
✓ Keep branches short-lived (< 1 week)  
✓ Never force push to main or dev  
✓ Always create pull requests for code review  
✓ Delete branches after merging  
✓ Keep README.md updated  
✓ Use semantic versioning for tags  
✓ Write descriptive PR descriptions  

## Git Commands Reference

```bash
# View branches
git branch -a

# View commit history
git log --oneline --graph --all

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Discard local changes
git restore <file>

# Sync with remote
git fetch origin
git pull origin dev

# View differences
git diff
git diff <branch>
```

## Questions or Issues?

Contact the DevOps team or create an issue on GitHub.

---

## How to Add This File to Your Project

1. Open Notepad or VS Code
2. Copy the content above
3. Save as `CONTRIBUTING.md` in your project folder
4. Commit it:

```bash
git add CONTRIBUTING.md
git commit -m "docs: add contribution guidelines"
git push origin main
```