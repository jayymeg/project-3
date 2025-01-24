### Step-by-Step Guide: Git Workflow for a Team Project

#### **Scenario Overview**:
The team is developing a web application. The goal is to enable multiple developers to work on features simultaneously while maintaining a stable `main` branch. This guide ensures:
- Smooth collaboration
- High code quality
- Automated integration testing

---

### **Git Workflow Guide**

#### **1. Setting Up the Repository**
1. **Create the Repository**: If not already done, create a repository in GitHub/GitLab/Bitbucket. Set `main` as the default branch. Enable branch protection rules for the `main` branch to: require pull requests for merging and enable status checks (e.g., automated testing) before merging.
2. **Clone the Repository**: Each developer clones the repository to their local machine:
   ```bash
   git clone <repository_url>
   cd <repository_name>
   ```

#### **2. Branching Strategy**
1. **Use a Feature Branching Model**: All work is done in separate branches based on the `main` branch. Naming convention for branches: **Feature branch**: `feature/<description>`, **Bugfix branch**: `bugfix/<description>`, **Enhancement branch**: `enhancement/<description>`.
2. **Create a Feature Branch**:
   ```bash
   git checkout main        # Switch to the main branch
   git pull origin main     # Ensure it's up-to-date
   git checkout -b feature/<feature-name>  # Create and switch to the feature branch
   ```

#### **3. Implementing Features**
1. Make your changes in the feature branch. 
2. Stage and commit changes:
   ```bash
   git add .
   git commit -m "Add: <description of the changes>"
   ```
3. Push the branch to the remote repository:
   ```bash
   git push origin feature/<feature-name>
   ```

#### **4. Code Reviews with Pull Requests**
1. **Submit a Pull Request**: Go to the repository on GitHub/GitLab. Open a Pull Request (PR) from your feature branch to the `main` branch. Add a descriptive title and summary: what the feature does and steps to test it. Assign reviewers to the PR.
2. **Conduct the Code Review**: Reviewers check for: code quality, readability, and adherence to standards; any potential issues or bugs. Provide feedback, suggest changes, or approve the PR.

#### **5. Continuous Integration (CI) Testing**
1. **Automated Tests**: Set up CI pipelines (e.g., GitHub Actions, Jenkins, CircleCI) to run tests for every pull request. Typical tests include: linting for code style checks, unit tests to verify the functionality of individual components, and integration tests to ensure new changes don’t break existing code.
2. Ensure the PR passes all automated tests before approval.

#### **6. Merging into `main`**
1. Once the PR is approved and tests pass: merge the branch into `main` via the PR interface using "Squash and Merge" or "Rebase and Merge." Ensure the branch is deleted after merging to keep the repository clean.
2. If merging manually:
   ```bash
   git checkout main
   git pull origin main      # Ensure main is up-to-date
   git merge feature/<feature-name>
   git push origin main
   ```

#### **7. Keeping Feature Branches Updated**
1. Regularly rebase the feature branch with `main` to avoid conflicts:
   ```bash
   git checkout feature/<feature-name>
   git pull --rebase origin main
   git push origin feature/<feature-name> --force
   ```

---

### **Best Practices**
1. **Collaborative Development**: Keep PRs small and focused on a single feature or fix. Use descriptive commit messages.
2. **Avoid Merge Conflicts**: Regularly sync feature branches with `main`.
3. **Protect the `main` Branch**: Only allow merging via PRs. Require tests to pass before merging.
4. **Maintain Clean History**: Use rebase instead of merge during development to keep the Git history linear and easy to read.

---

### **How This Workflow Facilitates Collaboration**
- **Parallel Development**: Feature branches allow multiple developers to work independently.
- **Code Quality**: Code reviews ensure every change is vetted before merging.
- **Automation**: CI pipelines catch bugs early through automated testing.
- **Stable `main` Branch**: Ensures only tested and reviewed code reaches production.
