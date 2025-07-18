### Switching Between Development and Preproduction Without Losing Data

**Step 1: Set Up for Development**

* First, update your `web.config` and `launchSettings.json` files according to your **development** environment.
* Then open the command prompt and check for any file changes:

  ```bash
  git status
  ```
* Now save your changes safely using stash:

  ```bash
  git stash save "Development Stash"
  ```

**Step 2: Set Up for Preproduction**

* Update your `web.config` and `launchSettings.json` according to your **preproduction** environment.
* Then save those changes too:

  ```bash
  git stash save "Preproduction Stash"
  ```

**Step 3: Check All Saved Profiles**

* To see the list of all saved stashes:

  ```bash
  git stash list
  ```

  Example output:

  ```
  stash@{0}: On branch-name: Preproduction Stash
  stash@{1}: On branch-name: Development Stash
  ```

**Step 4: Switch to Development or Preproduction Anytime**

* If you want to apply the **development** profile:

  ```bash
  git stash apply --index stash@{1}
  ```
* If you want to switch to the **preproduction** profile:

  ```bash
  git stash apply --index stash@{0}
  ```

**Important: Safe Reset Without Losing Profile Data**

* Even if you run:

  ```bash
  git reset --hard
  ```

  your stashed profiles will **not be deleted**. You can still switch between them using:

  ```bash
  git stash list
  git stash apply --index stash@{X}
  ```
