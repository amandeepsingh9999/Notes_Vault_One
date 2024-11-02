# Renaming file in git repo

Step - 01 
```sh
mv old_file_name new_file
```

Step - 02
```sh
git add new_file
```

Step - 03
```sh
git rm old_file_name
```

Step - 04
```sh
git commit -m "Rename file from old_file_name to new_file"
```

Automatic way to do it
```sh
git mv old_file_name new_file
git commit -m "Rename file from old_file_name to new_file"
```

# Ignoring Files

## 1. 

We can ignore certain file by simply adding file to a git File that has been called `.gitignore`

So we are gonna create a `.gitignore` file 
```sh
touch .gitignore
```

What we can do with this is we can add folders like `logs/` to this file certain numbers of like `*.log` 

now if we add new file to a git repository and that is placed in a `.gitignore` file that is not gonna stage or gonna upload in server

we are just gonna do some thing like 

```sh
git add .gitignore 
git commit -m "Added gitignore"
```

## 2.

Let us suppose that we have added file to our git like `bin/app.js` now we can do something like add it to our `.gitignore` file , but when we add that file to our `.gitignore` it is been already committed and it is keeping the track of file so now what we can do it to un-stage that file from stage . we can see files like using this command 
```sh
git ls-files
```

now we can see that our file is been tracked so we can remove from there so git does not keep track of that file by simple doing 
```sh
git rm --cached bin/app.js
```

For a directory we can do it by recursively 
```sh
git rm --cached -r bin/
```

# Better status

```sh
git status -s
```

# See the staged activities

```sh
git diff --staged
```
