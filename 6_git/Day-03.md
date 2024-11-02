### How to Set Up SSH for Git Push

Today I learned that we can’t use the `git push` command right out of the box; we need to set up SSH for a secure connection with GitHub. Here’s a simple, step-by-step guide to getting SSH configured and pushing code seamlessly!

#### Step 1: Check for Existing SSH Keys
Before creating a new key, let’s see if one already exists:

```sh
ls -al ~/.ssh
```

If you see a file like `id_rsa.pub` or `id_ed25519.pub`, you can skip the key creation step. Otherwise, let’s create one!

#### Step 2: Generate a New SSH Key
Run the following command to generate an SSH key:

```sh
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Replace `"your_email@example.com"` with your email. This creates a new key file that Git will use to securely connect to GitHub.

#### Step 3: Add Your SSH Key to GitHub
Next, we need to tell GitHub about this key so it can authenticate you.

1. Display the key with:

   ```sh
   cat ~/.ssh/id_ed25519.pub
   ```

2. Copy the output (the entire key).

3. Go to [GitHub’s SSH settings](https://github.com/settings/keys):
   - **Settings** > **SSH and GPG keys** > **New SSH key**.
   - Paste your key and save.

#### Step 4: Verify the Connection
To make sure everything’s set up correctly, test the SSH connection with:

```sh
ssh -T git@github.com
```

You should see a success message welcoming you to GitHub!

#### Step 5: Configure Your Git Remote
Make sure your Git repository uses the SSH URL:

```sh
git remote set-url origin git@github.com:yourusername/yourrepo.git
```

Replace `yourusername/yourrepo.git` with your actual GitHub username and repository name.

#### Step 6: Push Your Code!
With SSH set up, you’re ready to push your code:

```sh
git push -u origin main
```

And that’s it! 🎉 You’re now set up to push your code effortlessly.