# 1. **Set up of VS Code with WSL**
1. First download vs code.
2. Open powershell as admin. Paste this code `wsl --install`
3. Restart the machine 
4. download wsl `--install -d Ubuntu` from powershell as admin
5. type username and password. the cursor will not shift when writing the password.
6. Now to set up WSL inside vs code click on `><` then select wsl it will start downloading.
7. if `6` step doesn't work close vs code then open power shell type  `wsl --shutdown` close it.
    open ubuntu type `rm -r ~/.vscode-server` then type `code .`
8. press `ctrl + ~` to open terminal in vs code.
9. **Changing default workspace folder** : If i want to make another folder as my primary coding space, make a folder by `mkdir Project` and named then open that `project` folder by this `cd` then `code . -r` paste this.
10. NOTE: use `mnt folder` to use windows files
11. NOTE: use `touch abc.c` to save the code

# 2. **setup vscode for github**
**Part 1: One-Time Machine Setup (Only done once on your laptop)**

* `ssh-keygen -t ed25519 -C "your-email@example.com"` (instead of email ID you can use any phrase here. Avoid giving personal email ID)
* **Why:** Generates your private key (which stays on your laptop) and public key (which you upload to GitHub).


* `cat ~/.ssh/id_ed25519.pub`
* **Why:** Displays your public key in the terminal so you can copy and paste it into **GitHub Settings -> SSH Keys**.


* `ssh -T git@github.com`
* **Why:** Verifies your SSH link to GitHub. The terminal must respond with: *"Hi user! You've successfully authenticated..."*



---

**Part 2: Starting a New Project (Run every time you build something new)**

* **Step 1:** Create an empty repository on GitHub in your browser.
* **Why:** Allocates space online for your project files. Do not check "Add README" or license options.


* `git init`
* **Why:** Initializes version control inside your local project directory.


* `git add .`
* **Why:** Stages all current project files for tracking.


* `git commit -m "Initial commit"`
* **Why:** Captures your first permanent local version snapshot.


* `git branch -M main`
* **Why:** Labels your default local branch as `main`.


* `git remote add origin git@github.com:<username>/<repo-name>.git`
* **Why (Run this for every new project):** Your laptop does not automatically know where this specific project lives online. You must run this command in every new project folder so Git can save that unique repository's SSH address under the short nickname `origin`.

to check status: `git remote -v` -> Inspect which online URLs your folder connects to for fetching and pushing.

* `git push -u origin main`
* **Why:** Sends your code to GitHub and establishes a tracking link between your local `main` branch and the remote `main` branch.


---

**Part 3: Daily Development Routine (Your standard edit loop)**

* `git add .`
* **Why:** Selects all new edits, additions, and deletions you want to include in your next update.


* `git commit -m "Clear description of changes"`
* **Why:** Packages those staged edits into a distinct historical checkpoint.


* `git push`
* **Why:** Sends your latest commits straight to GitHub. You do not need `-u` or remote names here because the link is already saved.



---

**Part 4: Working on Secondary Branches (Like `table`)**

* `git checkout -b table`
* **Why:** Creates a isolated development branch named `table` and shifts your workspace onto it.


* `git add .` followed by `git commit -m "Build table component"`
* **Why:** Saves your work exclusively on the `table` branch while keeping `main` untouched.


* `git push -u origin table`
* **Why (First push only):** Publishes the `table` branch onto GitHub and establishes its upstream tracking link.


* Any following updates on `table`:
* `git push`
* **Why:** Pushes directly because your branch tracking is already configured.
