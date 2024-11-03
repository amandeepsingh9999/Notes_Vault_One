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

