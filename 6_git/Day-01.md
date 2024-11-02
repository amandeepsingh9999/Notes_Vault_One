Step - 1 
-- 
Setup Username and email for the git

##### For setting up User name
```sh
git config --global user.name "amandeepsingh9999"
```
##### For Setting up email in global config
```sh
git config --global user.email amandeepsinghbhogal002@gmail.com
```

`System` - All user
`Global` - All repositories of current user
`Local` - The Current Repository 

##### For Setting up default code editor for git

```sh
git config --global core.editor "nvim"
```

##### For Seeing the settings we made earlier in the code

```sh
git config --global -e
```

##### This is a Git setting that controls how line endings are handled in the repository.

```sh
git config --global core.autocrlf input
```

**`input`**: This specific value for `core.autocrlf` tells Git to:

- **Convert CRLF to LF** when files are committed to the repository. This is useful for macOS/Linux users who don't want Windows-style line endings (`CRLF`) in the repository.
- **Leave line endings as-is** when files are checked out, meaning that if you're on macOS/Linux, files stay in the `LF` format when you open them.

## Now we will Take example to push a repo in github

1. Initializing a repo
```sh
git init
```

2. Check the status of a repo
```sh
git status
```

3. Staging the changes 

for adding all file to the stage
```sh
git add .
```

for adding selected files for staging
```sh
git add file1.txt
```

4. Commiting the changes
```sh
git commit -m "This action is added"
```

5. Directly commiting code
```sh
git commit -am "The bug is fixed !!"
# We give -a flag for all files that are updated !!
```


### Removing files from a git repo

suppose we removed a file from git repo 
```sh
rm file1.txt
```

now we can see still see the file1.txt in the stage 
the command which will show staged file is 
```sh
git ls-files
```

Now we will see the status of our git repo 
```sh
git status
```

Another way to do it
```sh
git rm file1.txt
```

for future - 
1. browsing history
2. branching and merging 
3. collaboration
4. rewriting history