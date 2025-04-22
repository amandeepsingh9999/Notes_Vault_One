### Renaming a File in a Git Repository

Renaming files in Git is straightforward. Here’s how:

#### Step-by-Step Method

1. **Rename the file**:
   ```sh
   mv old_file_name new_file_name
   ```

2. **Stage the new file**:
   ```sh
   git add new_file_name
   ```

3. **Remove the old file from tracking**:
   ```sh
   git rm old_file_name
   ```

4. **Commit the change**:
   ```sh
   git commit -m "Rename file from old_file_name to new_file_name"
   ```

#### Automatic Way

Alternatively, Git provides an automatic way to rename files:

```sh
git mv old_file_name new_file_name
git commit -m "Rename file from old_file_name to new_file_name"
```

### Ignoring Files in Git

Sometimes, you might want Git to ignore certain files or directories, such as configuration files or logs. This is done using a `.gitignore` file.

#### 1. Creating a `.gitignore` File

1. Create the file:
   ```sh
   touch .gitignore
   ```

2. Add patterns to specify files or directories to ignore. For example:
   - To ignore all `.log` files: `*.log`
   - To ignore a directory named `logs/`: `logs/`

#### 2. Tracking Changes to `.gitignore`

After setting up `.gitignore`, commit it to your repository:

```sh
git add .gitignore
git commit -m "Add .gitignore file"
```

#### 3. Removing Already Tracked Files from Git

If you already committed a file that you now want Git to ignore, remove it from tracking:

1. **View tracked files**:
   ```sh
   git ls-files
   ```

2. **Untrack a single file**:
   ```sh
   git rm --cached path/to/file
   ```

3. **Untrack an entire directory**:
   ```sh
   git rm --cached -r path/to/directory
   ```

### Handy Git Commands

1. **Compact Git Status**
   ```sh
   git status -s
   ```
   This shows a short version of the Git status.

2. **View Staged Changes**
   ```sh
   git diff --staged
   ```
   This command shows differences in files that are staged for commit.