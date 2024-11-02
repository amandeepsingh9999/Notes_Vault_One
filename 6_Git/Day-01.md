### Step 1: Set Up Git Username and Email

To commit changes, Git requires a username and email address.

1. **Set Username**:
   ```sh
   git config --global user.name "username1234"
   ```

2. **Set Email**:
   ```sh
   git config --global user.email "emailid1234@gmail.com"
   ```

> **Levels of Configuration**:
> - `System`: Applies to all users on the system.
> - `Global`: Applies to all repositories of the current user.
> - `Local`: Applies only to the current repository.

3. **Set Default Code Editor for Git**:
   ```sh
   git config --global core.editor "nvim"
   ```

4. **View Configurations**:
   ```sh
   git config --global -e
   ```

### Handling Line Endings

Git can automatically convert line endings for different OS environments. To set this up:

```sh
git config --global core.autocrlf input
```

- **`input`**: Converts `CRLF` to `LF` on commit, which is helpful for macOS/Linux users who want consistent `LF` line endings in the repository. Files remain in `LF` format when checked out.

---

### Example: Pushing a Repository to GitHub

1. **Initialize the Repository**:
   ```sh
   git init
   ```

2. **Check the Status**:
   ```sh
   git status
   ```

3. **Stage Changes**:
   - **Add All Files**:
     ```sh
     git add .
     ```
   - **Add Specific Files**:
     ```sh
     git add file1.txt
     ```

4. **Commit the Changes**:
   ```sh
   git commit -m "This action is added"
   ```

5. **Directly Commit All Changes**:
   ```sh
   git commit -am "The bug is fixed!!"
   ```
   > The `-a` flag stages and commits all updated files in one step.

---

### Removing Files from a Git Repository

If a file is removed from the directory but still appears in Git, you can untrack it.

1. **Remove the File from Git**:
   ```sh
   rm file1.txt
   ```

2. **List Tracked Files**:
   ```sh
   git ls-files
   ```

3. **View Repository Status**:
   ```sh
   git status
   ```

4. **Remove and Untrack File in One Step**:
   ```sh
   git rm file1.txt
   ```

---

### Future Topics

1. **Browsing History**
2. **Branching and Merging**
3. **Collaboration with Others**
4. **Rewriting History**