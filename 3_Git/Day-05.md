# Git Branching and Merging Guide

This guide provides quick and concise commands for managing Git branches and resolving conflicts. It is aimed at helping both new and experienced users navigate Git efficiently.

---

## Branching

Creating a new branch allows you to work on changes in isolation without affecting the main codebase. To create and switch to a new branch, follow these steps:

1. **Create a New Branch**  
    Use the following command to create a new branch:
    
    ```sh
    git branch newBranch
    ```
    
    Replace `newBranch` with the desired name for your branch.
    
2. **Switch to the New Branch**  
    Once the branch is created, switch to it using:
    
    ```sh
    git checkout newBranch
    ```
    
    Alternatively, from Git version 2.23 onwards, you can use:
    
    ```sh
    git switch newBranch
    ```
    

---

## Merging

Merging allows you to combine changes from one branch into another. It’s often used to bring new feature branches into the main branch.

1. **Switch to the Main Branch**  
    Before merging, navigate to the branch where you want to integrate the changes:
    
    ```sh
    git checkout main
    ```
    
    Or, if your primary branch is named `master`:
    
    ```sh
    git checkout master
    ```
    
    (Branch names vary by repository. `main` is the default for newer repositories.)
    
2. **Merge the New Branch**  
    Once on the desired branch, use the following command to merge the changes from `newBranch`:
    
    ```sh
    git merge newBranch
    ```
    
    Replace `newBranch` with the name of the branch being merged.
    

---

## Resolving Merge Conflicts

Merge conflicts occur when changes from two branches overlap or contradict. Git will pause the merge process and highlight the conflicting code. To resolve conflicts:

1. **Identify Conflicted Files**  
    After a merge conflict occurs, Git will list the files with conflicts. Open these files in your editor.
    
2. **Manually Resolve Conflicts**  
    In the conflicted files, Git will mark the conflicts like this:
    
    ```plaintext
    <<<<<<< HEAD
    code from the current branch
    =======
    code from the merging branch
    >>>>>>> newBranch
    ```
    
    - Changes from the current branch are shown under `HEAD`.
    - Changes from the branch being merged are under `newBranch`.
    
    Edit the file to resolve the conflict by choosing or combining the changes.
    
3. **Mark the Conflicts Resolved**  
    Once resolved, add the files back to the staging area:
    
    ```sh
    git add <file>
    ```
    
4. **Complete the Merge**  
    Finish the merge process by committing:
    
    ```sh
    git commit
    ```
    

---

## Additional Tips and Best Practices

1. **Naming Branches**  
    Use descriptive names for branches to make their purpose clear, e.g., `feature/user-auth`, `bugfix/ui-error`.
    
2. **Check Branch Status**  
    View the branches and their status:
    
    ```sh
    git branch
    ```
    
3. **Keep Branches Up to Date**  
    Regularly sync your feature branch with the main branch to minimize conflicts:
    
    ```sh
    git pull origin main
    ```
    
4. **Using Rebase Instead of Merge**  
    For a cleaner commit history, you can use rebase:
    
    ```sh
    git rebase main
    ```
    
5. **Undoing Merges**  
    If a merge goes wrong, you can reset to a previous commit:
    
    ```sh
    git reset --merge
    ```
    
