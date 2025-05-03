---
created: 
tags:
  - programming
  - git
description: the recommended procedures and concepts for cases where you want to completely revamp your GitHub repository content while keeping the cherished repository name. 
reference:
---
## Requirement

* Want to maintain existing repository attributes (name, URL, Issue/PR history, stars, etc.)
* Need to completely rebuild the codebase from scratch (refactoring)

## Recommended Best Practice: Working with a New Development Branch

The safest and recommended approach is to create a new development branch (e.g., `refactor`) in the existing repository and conduct the refactoring work there.

**Benefits:**

* **Maintains repository name and URL:** No external impact (like broken links). GitHub Pages continues to function as normal.
* **Preserves history:** Retains all past commits, Issues, Pull Requests, and contributor information.
* **Safe work environment:** Build new code independently without affecting the stable code (`main` branch).
* **Smooth transition:** After refactoring is complete, the new branch can be set as the repository default.

## Specific Steps

1.  **Create new development branch:**
    In your local repository, create a new branch from the existing default branch (`main` or `master`).
    ```bash
    git checkout -b refactor origin/main # or origin/master
    ```
2.  **Delete existing code (optional):**
    If starting completely from scratch, delete all files except the `.git` directory on the new branch and commit this state.
    ```bash
    # Delete all files except .git (adjust command as needed for your environment)
    git rm -rf .
    git commit -m "Initial commit for refactoring: clearing old codebase"
    ```
    If you want to keep specific files (like `.gitignore`), delete files selectively.
3.  **Build new code:**
    Develop new code on the `refactor` branch and commit/push as appropriate.
    ```bash
    # Add code and commit
    git add .
    git commit -m "Implement new core structure"
    # Push to remote (use -u to set upstream on first push)
    git push -u origin refactor
    ```

## Post-Refactoring Steps

### 1. Switch Default Branch (Recommended)

After completing the refactoring, it is **strongly recommended to switch the repository's default branch to `refactor` instead of merging `refactor` into `main`**.

* **Reasons:**
    * A simple merge would mix old and new history, diluting the intent of "starting from scratch".
    * By switching the default branch, the repository's main history will start from the clean, post-refactoring state.
* **Steps (on GitHub):**
    1.  Go to `Settings` > `Branches` on your GitHub repository page.
    2.  In the `Default branch` section, select `refactor` from the dropdown and click the `Update` button.

### 2. Branch Name Cleanup (Rename `refactor` to `main`)

After setting `refactor` as the default branch, you can rename it to the more standard `main`.

* **Recommended Steps (on GitHub):**
    1.  (Required) First switch the default branch to `refactor` using the steps above.
    2.  Go to the branches list page on GitHub (click `branches` link under the `Code` tab).
    3.  Find and delete the **old `main` branch** (which should no longer be the default).
    4.  Click the edit icon (pencil) next to the **`refactor` branch** (current default).
    5.  Enter `main` as the new name and click the `Rename branch` button.
* **Update Local Repository:**
    After renaming the branch remotely, sync your local repository with these commands:
    ```bash
    # Get remote changes (branch deletions/renames)
    git fetch --prune origin

    # Delete old local main branch (if it exists and is not needed)
    git branch -d main

    # If your current local branch is still named refactor,
    # checkout and rename it
    git checkout refactor # checkout the branch if not already
    git branch -m refactor main # rename local branch

    # Set new local main branch to track remote main
    # Either run git push -u origin main or use this command
    git branch -u origin/main
    ```
* **Branch Rename Considerations:**
    * Renaming branches may affect open pull requests, CI/CD pipelines, and other integrated tools targeting that branch. Check and update these settings after the change. (GitHub will auto-update some things, but verification is needed)
    * If you have collaborators, it's crucial to notify everyone before renaming branches and share the local repository update procedures.

## Other Methods and Their Risks (Not Recommended)

* **Direct repository content overwrite (`git push --force`):** Avoid this as it has a very high risk of unintentionally losing history or causing inconsistencies with other developers' local repositories.
* **Repository deletion & recreation:** This will result in the **complete loss** of all non-code repository information including Issues, Pull Requests, Stars, Watches, Wiki, and settings.