## Creating a Custom Git Diff Tool with Neovim

If you frequently use Git and want to view diffs in Neovim instead of the default viewer, you can easily set up a custom diff tool using a simple script. This script will allow Git to open file diffs directly in Neovim, with side-by-side views when comparing files. Here’s how to set it up:

### Step 1: Create the Diff Script

1. Open a new file in Neovim to create the script. We’ll name it `mydiff`, but feel free to choose any name that suits you:

   ```sh
   nvim mydiff
   ```

2. Inside `mydiff`, add the following script:

   ```sh
   #!/bin/bash
   if [ "$2" = "/dev/null" ]; then
       nvim "$1"
   else
       nvim -d "$1" "$2"
   fi
   ```

   **Explanation**:
   - This script checks if a second file (`$2`) is provided. 
   - If only one file (`$1`) is given, it opens that file in Neovim.
   - If both files are provided, it launches Neovim in "diff mode" (`nvim -d`), allowing a side-by-side comparison.

3. Save and close the file. Now, make this script executable so it can be used as a command:

   ```sh
   chmod +x mydiff
   ```

4. Move the script to `/usr/local/bin` so it’s accessible system-wide:

   ```sh
   sudo mv mydiff /usr/local/bin/
   ```

   By placing `mydiff` in `/usr/local/bin`, any user on the system can run it from the terminal.

### Step 2: Set Up Git to Use the Custom Diff Tool

Next, configure Git to use this script as its diff tool. Open your global Git configuration file:

```sh
git config --global -e
```

Add the following lines to specify `mydiff` as the external diff tool for Git:

```ini
[diff]
    external = mydiff
```

### Step 3: Test the Setup

Now, whenever you use `git diff` on modified files, Git will invoke the `mydiff` script, which opens Neovim in diff mode. Here’s a quick example:

```sh
git diff file1.txt file2.txt
```

This command will launch Neovim with `file1.txt` and `file2.txt` in diff mode, making it easier to visualize changes side-by-side.

Here’s a breakdown of useful Git commands for viewing history and restoring files:

---

## Viewing Git History

Git offers several ways to examine the history of your commits and view changes at different stages in your project. Here are some commands to help with that:

### Basic Commit Log
```sh
git log
```
Shows the full commit history, including details like author, date, and commit message.

### Condensed Log View
```sh
git log --oneline
```
Displays each commit in a single line, showing only the commit hash and message. This is useful for a quick overview.

### Reverse Order Log
```sh
git log --oneline --reverse
```
Shows the condensed commit history in reverse chronological order, which can be helpful when you want to start with the earliest commit.

## Viewing Specific Commits

1. **Show details of the latest commit**:
   ```sh
   git show HEAD
   ```
   Shows changes made in the most recent commit (`HEAD`), including the modified files and diffs.

2. **View changes in the previous commit**:
   ```sh
   git show HEAD~
   ```
   
   or equivalently:
   ```sh
   git show HEAD~1
   ```
   This shows changes in the commit just before the latest.

3. **Explore the tree structure of a commit**:
   ```sh
   git ls-tree HEAD~1
   ```
   Lists all files and directories tracked by Git in the specified commit (e.g., `HEAD~1`), providing a snapshot of the repository structure at that point.

---

## Restoring Files in Git

Sometimes, you may need to unstage or restore files to a previous state. The `git restore` command is versatile for this purpose:

### Unstage a Specific File
```sh
git restore --staged file.js
```
Removes `file.js` from the staging area without affecting its working directory changes. This is useful if you added a file to the staging area by mistake.

### Restore Multiple Files or Patterns
You can specify multiple files or use patterns to restore a group of files:

```sh
git restore --staged "*.js"  # Unstages all JavaScript files
git restore --staged .       # Unstages all files in the current directory
```

---

## Discarding Local Changes

When working with Git, you may sometimes need to discard uncommitted changes or remove untracked files. Here’s how:

### Discard All Local Changes in Tracked Files
```sh
git restore .
```
This command discards all modifications in tracked files (those already in Git) in the current directory. It reverts tracked files back to their last committed state, effectively undoing any uncommitted changes.

### Remove Untracked Files and Directories
```sh
git clean -fd
```
This command removes untracked files (`-f`) and directories (`-d`). It’s helpful for clearing out files that Git is not tracking, which might be cluttering your working directory.

**Note**: Use `git clean -fd` with caution, as it permanently deletes untracked files and directories.

---

## Restoring Files with Git

If you’ve deleted a file and committed that change but want to restore it, here’s how you can handle it.

### Step 1: Remove a File and Commit the Change

For example, you may delete a file with `git rm` and then commit the deletion:

```sh
git rm file1.js
git commit -m "Deleted one file"
```

### Step 2: Undo the Deletion by Reverting the Commit

To undo a commit that deleted a file, you can use `git revert` to create a new commit that restores the file:

```sh
git revert HEAD
```

or we can check our log see where our files have been deleted

```sh
git log --oneline
```

Now we know where our file have been changed i know that my file has been changed in last commit ,
we can also specify our file name so it only recovers that .

```sh
git restore --source=HEAD~1 file1.js
```

This will create a new commit that undoes the last commit (`HEAD`), bringing back `file1.js`. Using `git revert` is beneficial as it preserves the commit history while still reversing changes.