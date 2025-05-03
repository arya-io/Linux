# 🗂️ Version Control with & without Git

---

## 🔒 Version Control Without Git

### 📄 **Check File Integrity**

```bash
sha1sum {file_name}
```

* ✅ This generates a **SHA-1 hash** (40-character checksum) of your file.
* 🛡️ Useful to **verify file authenticity** — if the hash matches, the file hasn't been tampered with!

---

## 🌱 Git & GitHub

---

### 🔧 **Initialize Git Repository**

```bash
git init
```

* ➡️ Creates a new **empty Git repository** in your current folder.
* 🎯 Adds a hidden `.git` folder that tracks all version history from now on.

---

### 📜 **Track Modifications**

```bash
git log
```

* ✅ Lists **all commits** made with time, author, and message.
* 🔎 Helps in auditing changes and who did what!

---

### 🎥 **Record Terminal Commands**

```bash
script script_name
```

* 📝 Starts recording your terminal session.
* 🎯 Good for keeping track of the commands you ran (useful for reports, demos, or sharing).

---

### 📦 **GitHub: Generate Personal Access Token (PAT)**

To interact securely with GitHub (especially now that passwords are deprecated):

1. Go to **Profile > Settings > Developer Settings > Personal Access Tokens > Tokens (classic)**
2. Select scopes:

   * ✅ `write`
   * ✅ `delete`
   * ✅ `admin.org`
   * ✅ `user`
3. Click on **Generate Token**

🔐 **Copy and store the token safely** — you'll need this to push code via HTTPS.

---

## 🚀 **Git Version Control System \[GVCS]**

> 🛠️ **Created by Linus Torvalds** (the father of Linux) for developing the Linux Kernel!

---

### 🧐 **What is Git?**

* **Git** is a **Version Control System (VCS)**.
* Think of it like a **"time machine"** for your code.
  You can snapshot your files and **go back** anytime if you make a mistake.

👨‍💻 **Why developers use Git?**

* We make lots of changes while developing.
* Sometimes, we need to check **old versions** or rollback.
* It helps in:

  * 🔄 Comparing past versions
  * 🔎 Finding bugs
  * 🚀 Collaborating with others

✅ Git helps you track, manage, and control every change in your project.

---

### 📚 **Basic Git Concepts**

| 🏠 Your Local Code              | ✍️ Staged Site                 | 📡 The Server (Remote Repo)              |
| ------------------------------- | ------------------------------ | ---------------------------------------- |
| Your personal edits on your PC. | Mark files as ready to commit. | Push your work to cloud/server to share. |

---

* **Local Code**: Work you do on your machine (editing, creating).
* **Staged**: Files you marked ready to be saved (using `git add`).
* **Server (Remote)**: Where you push code (`git push`) so others can see and collaborate.

---

### 🔄 **Why go back to old versions?**

* 🟣 To check if older version worked better.
* 🟣 To see what changed, when, and by whom.
* 🟣 To debug errors easily.

✅ **Git helps** track, manage, and restore code with ease!

---

### 🌐 **What is GitHub?**

* **GitHub** = Cloud platform to **store Git repositories**.
* Hosts your version history **online** so you and your team can collaborate.

---

### 🆚 **Git vs GitHub**

| 🔧 Git                                        | ☁️ GitHub                              |
| --------------------------------------------- | -------------------------------------- |
| Tool to track & manage code versions locally. | Platform to store code in cloud repos. |
| Runs on your **computer (local)**.            | Runs on the **web (cloud-based)**.     |

---

## 📦 **Basics to Start Using Git**

### 🔽 **Install Git**

```bash
# For Ubuntu/Debian
apt install git -y

# For RHEL/CentOS
yum install git -y
```

---

### 🔎 **Check Installed Git Version**

```bash
git --version
```

---

# 🌿 Starting with Git (Configuration, Branching & Committing)

---

## 👤 Setup Git Username & Email (First Step!)

```bash
# Set your name
git config --global user.name "Your Name"

# Set your email
git config --global user.email "your_email@example.com"
```

✅ Git uses this info in every commit you make.

---

### 🔎 View Current Config

```bash
git config --global --list
# OR
git config --global -l
```

---

### ❌ Remove/Unset Config

```bash
git config --unset --global user.email
```

---

## 📥 Clone a Remote Repository (from GitHub)

```bash
git clone https://github.com/account_name/repo.git
cd repo/
ls -a    # Check for .git directory (this shows it's a git repo)
```

🎯 **`.git/`** folder tracks everything about version control.

---

## 🆕 Initialize a New Local Repository

```bash
mkdir my_project
cd my_project
git init
ls -a    # You'll see .git/ now
```

✅ This creates an **empty Git repo** in the current directory.

---

## ➕ Staging Files for Commit

### To Add **All Files**

```bash
git add .
```

### To Add **Specific File**

```bash
git add FILENAME
```

✅ After adding, files move from "modified" ➡️ "staged" status.

---

## 🔎 View Repository Config (repo-specific)

```bash
cat .git/config
```

Sample output:

```ini
[core]
  repositoryformatversion = 0
  filemode = true
  bare = false
  logallrefupdates = true
[remote "origin"]
  url = https://github.com/username/repo.git
  fetch = +refs/heads/*:refs/remotes/origin/*
```

---

## 🌿 Working with Branches

### 🔧 Create & Switch to New Branch

```bash
git checkout -b branch_name
```

✅ `-b` creates and switches to **branch\_name**.

### 🔄 Switch to an Existing Branch

```bash
git checkout branch_name
```

### 📋 List Branches

```bash
git branch      # List local branches
git branch -a   # List local + remote branches
```

---

## ✍️ Make Edits & Check Differences

### Example: Edit README

```bash
cat >> readme.md
llll
```

### View Changes (Differences)

```bash
git diff
```

✅ Shows line-by-line changes:

* `+` lines are **added**
* `-` lines are **removed**

---

## ✔️ Add & Commit Changes

### Stage File(s)

```bash
git add readme.md
# OR add everything
git add .
```

### Commit with Message

```bash
git commit -m "Updated readme"
```

Sample output:

```
[branch_name commit_hash] Updated readme
 1 file changed, 1 insertion(+)
```

---

## 🔗 Merge Branches

### Merge `test` branch into `main`

```bash
git checkout main
git merge test
```

✅ Now `main` includes all changes from `test` branch.

---

## 🔎 View Commit History

```bash
git log
```

### 🪄 Show Branches with Logs

```bash
git show-branch
```

---

## 🚀 Committing Code to Remote Repository

### 1️⃣ Setup Name & Email *(Do this once)*

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"
```

---

### 2️⃣ Clone Repo & Make Changes

```bash
mkdir hello
cd hello
git clone URL
cd repo_name
```

Create a file:

```bash
cat > hello.py
```

Write:

```python
#!/usr/bin/python3
print("Hello, World")
```

Press `Ctrl+D` to save.

---

### 3️⃣ Check Repo Status

```bash
git status
```

✅ Shows which files are new, modified, or staged.

---

### 4️⃣ Add & Commit Changes

```bash
git add hello.py
git status
git commit -m "Added hello.py"
```

---

## 📜 View Commit Logs

```bash
git log
```

### 📝 One-line History

```bash
git log --oneline
```

✅ Shows each commit in **one line** — super handy for quick review!

---

## ✅ Recommended Learning Flow

1. **git init** ➡️ Start tracking
2. **git add** ➡️ Stage files
3. **git commit** ➡️ Save snapshot
4. **git branch** ➡️ Manage branches
5. **git merge** ➡️ Combine branches
6. **git log** ➡️ View history
7. **git push** ➡️ Upload to GitHub (coming next!)

---

# 🔥 Git Log, Public Repo Workflow & Internals

---

## 📜 Log: Viewing Commits

### One-line Log Format

```bash
git log --pretty=oneline
```

---

### 🎯 Controlling Log Output

```bash
git log --pretty=oneline --max-count=2       # Show latest 2 commits
git log --pretty=oneline --since='5 minutes ago'  # Commits since last 5 minutes
git log --pretty=oneline --until='5 minutes ago'  # Commits before 5 minutes ago
git log --pretty=oneline --author="Your Name"     # Filter by author
git log --pretty=oneline --all              # Show all refs (branches/tags)
```

✅ Useful to search, filter, and check specific commits.

---

## 🚀 Public Repository Workflow (Push Code to GitHub)

---

### 1️⃣ Create Repo on GitHub

➡️ Example:
`https://github.com/sinhakiara/DevOps-Demo`

---

### 2️⃣ Clone the Repo

```bash
git clone https://github.com/sinhakiara/DevOps-Demo.git
cd DevOps-Demo
```

---

### 3️⃣ Create a Branch

```bash
git checkout -b test
git branch     # Verify current branch
```

---

### 4️⃣ Make Changes in Branch

Edit files:

```bash
cat >> README.md
LOL

cat > index.html
<h1>ulala</h1>
```

Stage & commit:

```bash
git add .
git status
git commit -m "Home web page in test branch"
```

---

### 5️⃣ Merge Branch into Main

```bash
git checkout main
git merge test
```

---

### 6️⃣ Add Remote Repo (Optional Step)

```bash
git remote add origin https://github.com/sinhakiara/DevOps-Demo.git
cat .git/config   # Confirm remote added
```

---

### 7️⃣ Generate GitHub Token

➡️ Go to:
**Settings ➡️ Developer Settings ➡️ Personal Access Tokens ➡️ Generate New Token**

### 🔒 Store Credentials (so you won’t get login prompt every time)

```bash
git config --global credential.helper store
```

---

### 8️⃣ Push to GitHub

```bash
git push -u origin main
```

✅ Use **username** and **token** as password when prompted.

---

## 🧱 Git Internals (Under the Hood)

---

### 🗂️ `.git` Directory

```bash
ls -C .git
```

➡️ This folder stores **entire repo history** and config — never delete this!

---

### 🗄️ Git Object Store

```bash
ls -C .git/objects
```

➡️ Shows dirs named with **2 letters** (first 2 of SHA1 hash).

#### Deeper: Check one object dir

```bash
ls -C .git/objects/<2-letter-dir>
```

* Files here = **compressed objects** (blobs, trees, commits).

---

### ⚙️ Config File

```bash
cat .git/config
```

* Stores **repo-specific config** like remotes, branch info.

---

### 🌿 Branches & Tags

```bash
ls .git/refs
ls .git/refs/heads   # Branches
ls .git/refs/tags    # Tags
cat .git/refs/tags/v1  # Shows hash tied to tag
```

---

### 📍 The HEAD File

```bash
cat .git/HEAD
```

➡️ Shows **which branch** you’re currently on.

---

## 🔍 Dumping Commits & Trees (Deep Dive)

---

### 1️⃣ Dump Latest Commit

```bash
git log --oneline
git cat-file -t <commit-hash>   # Type of object (should be commit)
git cat-file -p <commit-hash>   # Pretty print commit details
```

---

### 2️⃣ Finding the Tree

```bash
git cat-file -p <tree-hash>
```

Example output:

```
100644 blob 28e0e9d6ea7e25f35ec64a43fe8386f90	Rakefile
040000 tree e46f374f5b36c6f02fb379044f754d795	lib
```

✅ Shows files + subdirs in the project at that commit.

---

### 3️⃣ Dump a Directory (e.g., lib folder)

```bash
git cat-file -p <lib-tree-hash>
```

---

## 🔄 Rollback & Checkout

---

### 🕒 Temporarily Switch to an Older Commit

```bash
git checkout <SHA1-hash>
```

✅ Good for **browsing** old versions (but doesn't delete anything).

---

### ❌ Hard Delete Unpublished Commits

```bash
git reset --hard <SHA1-hash>
```

🚩 **Warning:** This will permanently delete commits after the specified hash (if not pushed yet).

---

## ✅ Quick Recap: Git Internals

| Git Part       | Command              | Meaning                      |
| -------------- | -------------------- | ---------------------------- |
| `.git/objects` | `ls .git/objects`    | Stores all commits/files     |
| `HEAD`         | `cat .git/HEAD`      | Points to current branch     |
| Config         | `cat .git/config`    | Repo settings                |
| Branches       | `ls .git/refs/heads` | Shows all branches           |
| Tags           | `ls .git/refs/tags`  | Shows tags linked to commits |

---

## 🚀 Recommended Git Work Cycle

1. `git log --oneline` ➡️ Quick view commits
2. `git cat-file -p <hash>` ➡️ Inspect commits/trees
3. `git reset --hard <hash>` ➡️ Rollback
4. `git push` ➡️ Push changes to GitHub

---
