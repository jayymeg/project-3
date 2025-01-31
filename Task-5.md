## Scenario
During the development process, two developers working on separate branches accidentally introduced conflicting changes into the `main` branch after a failed merge. Your task is to resolve the conflict, ensure code integrity, and identify how the team can prevent such issues in the future.

# Deliverable
Demonstrate how to resolve the merge conflict by:
- Pulling the latest code
- Identifying the conflicting files
- Merging the changes

After resolving the conflict, update the team’s Git workflow with measures to avoid future conflicts, such as:
- Better communication
- Smaller, more frequent pull requests



##To resolve the merge conflict and prevent future issues, follow these steps:

### Resolving the Merge Conflict:
1. **Pull the Latest Code**:  
   ```bash
   git checkout main
   git pull origin main  # Ensure main is up-to-date
   ```

2. **Switch to the Feature Branch**:  
   ```bash
   git checkout feature-branch
   ```

3. **Merge `main` into the Feature Branch**:  
   ```bash
   git merge main  # Triggers conflict if changes overlap
   ```

4. **Identify Conflicting Files**:  
   ```bash
   git status  # Lists files with conflicts under "Unmerged paths"
   ```

5. **Resolve Conflicts in Files**:  
   Open each conflicted file (marked with `<<<<<<<`, `=======`, `>>>>>>>`), edit to keep the correct changes, and remove conflict markers.

6. **Stage Resolved Files and Commit**:  
   ```bash
   git add <resolved-file>  # Repeat for all resolved files
   git commit -m "Resolve merge conflicts with main"
   ```

7. **Push the Updated Feature Branch**:  
   ```bash
   git push origin feature-branch
   ```

8. **Merge via Pull Request**:  
   Create a new pull request from `feature-branch` to `main`. Ensure no conflicts exist, then merge.

---

### Updating Git Workflow to Prevent Future Conflicts:
1. **Branch Protection Rules**:  
   - Require pull request (PR) reviews before merging into `main`.  
   - Enforce "Require branches to be up to date before merging" (prevents stale branches).  
   - Enable status checks (e.g., CI/CD pipelines) to pass before merging.

2. **Smaller, Frequent Pull Requests**:  
   Encourage developers to submit smaller PRs focused on specific tasks to reduce conflict scope.

3. **Regularly Rebase/Update Feature Branches**:  
   ```bash
   git checkout feature-branch
   git rebase main  # Keeps branch updated with main’s latest changes
   ```

4. **Pre-Merge Checks**:  
   - Developers must pull the latest `main` and merge/rebase it into their branch before creating a PR.  
   - Use pre-commit hooks or CI tools to run automated tests.

5. **Improved Communication**:  
   - Use a shared board (e.g., Jira, Trello) to track who is working on which files.  
   - Conduct daily standups to discuss ongoing work and potential overlaps.

6. **Enforce Commit Signing**:  
   Ensure all commits are signed to verify authenticity:  
   ```bash
   git commit -S -m "Signed commit message"
   ```

By resolving conflicts in the feature branch and implementing these workflow improvements, the team minimizes merge issues and maintains code integrity.
