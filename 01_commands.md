# 🐧 Linux Notes

---

## 📁 Basic Commands

### 📍 PATH

* **Absolute Path**: `/home/natasha/Desktop`
* **Relative Path**: `Desktop` (relative to current directory)

---

### 📌 pwd

* Prints the **current working directory**

---

### 📂 cd

* Changes the **current directory**

Examples:

```bash
cd path/to/folder       # Go to specified path
cd ..                   # Move one directory up
cd ../../               # Move two levels up
```

---

### 📋 ls

* Lists the contents of a directory

```bash
ls                      # List contents in current dir
ls /root/Desktop        # List contents of Desktop dir
```

---

### 👤 whoami

* Displays the **current logged-in username**

---

### 🗂️ mkdir

* Creates a **new directory**

```bash
mkdir myfolder
```

---

### 📝 touch

* Creates a **blank file**

```bash
touch file.txt
```

---

### 🧾 cat > filename

* Creates a **new file** with content from terminal input

```bash
cat > marvels
# Type content here
[Ctrl + D]  # Save & Exit
```

---

### 🔁 cat filename

* Displays the contents of a file

---

### ➕ cat >> filename

* Appends text to an existing file

```bash
cat >> marvels
# Additional content
[Ctrl + D]
```

---

### ⏱️ date

* Displays the **current system date and time**

---

### 🧹 clear / Ctrl + L

* Clears the terminal screen

---

## 📤 Input & Output Operators

```bash
>   # Standard output redirection
<   # Standard input redirection
```

---

## 📄 COPY

### 🔄 a) File to File

```bash
cp src.txt dest.txt
cp -fv src.txt dest.txt     # Force and Verbose mode
```

### 📁 b) File/Directory to Directory

```bash
cp -rfv src/ dest/
# -r: Recursive
# -f: Force overwrite
# -v: Verbose
```

---

## 📘 man command

* View the **manual/help** for a command

```bash
man mkdir
```

---

## ❌ REMOVE

### 🗑️ a) Remove File

```bash
rm filename
rm -fv filename
```

### 🧺 b) Remove Directory

```bash
rm -rfv dirname
```

---

## 📦 MOVE (Cut & Paste)

### 🔀 Move File/Dir

```bash
mv src dst
```

### ✏️ Rename File/Dir

```bash
mv oldname newname
```

---

## 🕵️‍♂️ Hidden Files

### 🛠️ Create Hidden Directory

```bash
mkdir .hiddenfolder
```

### 👁️ Show All (including hidden)

```bash
ls -a
```

---

## 👨‍💻 whoami (again, reminder)

* Displays the **username** of the current session

---

## 🖨️ Echo, Terminal, & Messaging

### 🔊 `echo "message"`

* Prints the message on the terminal

```bash
echo "Hello, world!"
```

---

### 📺 `tty`

* Displays the **current terminal name**

```bash
/dev/pts/0
```

---

### 📤 Send message to another terminal

```bash
echo "LOL" > /dev/pts/1
```

* Displays the message **"LOL"** on another user's terminal (if permissions allow)

---

### 📄 Store output directly in a file

```bash
echo "Darlings" > kiki
```

* Creates `kiki` file and stores the message in it

---

## 🧙‍♂️ Aliases

### 🔍 View current aliases

```bash
alias
```

---

### ➕ Create an alias

```bash
alias money='whoami'
```

* Now running `money` will show the current user

---

### ❌ Remove an alias

```bash
unalias money
```

---

## 📦 Variables

### 🧑‍💻 User-defined variable

```bash
a=8
```

### 🔁 Printing variable values

```bash
echo "$a"       # Outputs: 8
echo '$a'       # Outputs: $a
echo "$a=$a"    # Outputs: 8=8
echo "\$a=$a"   # Outputs: $a=8
```

📌 **Tip**:

* `""` (Double quotes) allow **variable expansion**
* `''` (Single quotes) treat everything **literally**

---

## 🌍 Environment Variables

### 🧾 View all env variables

```bash
env
```

---

### 🔍 Show a specific env var

```bash
echo $HISTTIMEFORMAT
```

---

### 🕒 Format for command history timestamp

```bash
%d  # Day
%m  # Month
%y  # Year
%T  # Time
```

---

### 🛠️ Set timestamp format for history

```bash
export HISTTIMEFORMAT="%d-%m-%y %T "
```

---

### 🕘 Command History

```bash
history          # Show command history
history -d N     # Delete entry at index N
history -c       # Clear entire history
```

⚠️ **Secret Tip**:

* Adding a space **before a command** prevents it from being stored in history!

---

## 📂 File & Directory Management

### 🕵️ Check file type

```bash
file filename
```

---

### 📦 Create multiple directories

```bash
mkdir dir{1..10}
```

---

### 📄 Create multiple files

```bash
touch file{1..10}
```

---

### 📚 Create nested directories (parent → child)

```bash
mkdir -p a/b/c/d
```

---

### 🧹 Remove empty directory

```bash
rmdir directory
```

---

## 🔍 Finding Data with `find` Command

### 🧾 Syntax:

```bash
find <where_to_find> -<attribute> <what_to_find>
```

Example:

```bash
find /folder -name filename
```

---

### 1️⃣ By NAME

```bash
find . -name natasha
find . -iname natasha         # Case-insensitive search
find /home/edbda/ -iname "*.png"   # All .png files (case-insensitive)
```

---

## 📚 Working with File Content

### 🔃 sort

```bash
sort filename         # Sort file content
sort -u filename      # Sort uniquely (remove duplicates)
```

---

### 📖 more

```bash
more filename
```

* Displays content page-by-page; press `Enter` to see more.

---

### 🔢 wc (Word Count)

```bash
wc filename           # Shows lines, words, bytes, and filename
wc -l filename        # Line count
wc -w filename        # Word count
wc -c filename        # Byte count
wc -l -w -c filename  # All three together
```

---

### 🔝 head

```bash
head -n 5 filename     # First 5 lines
head -5 filename       # Same as above
```

---

### 🔚 tail

```bash
tail -n 5 filename     # Last 5 lines
tail -5 filename       # Same as above
```

---

### 2️⃣ By SIZE

**Units:**

* `k` → Kilobytes
* `M` → Megabytes
* `G` → Gigabytes

Examples:

```bash
find /home/edbda -size 2k         # Exactly 2KB
find /home/edbda -size +2k        # Greater than 2KB
find /home/edbda -size -2k        # Less than 2KB
find /home/edbda -size +2M -size -10M   # Between 2MB and 10MB
```

---

### 3️⃣ By TYPE

```bash
find /home/edbda -type f                  # Files only
find /home/edbda -type d                  # Directories only
find /home/edbda -type f -iname "abc"     # Specific file (case-insensitive)
```

---

### 4️⃣ By INDEX NUMBER

```bash
find /home/edbda -inum 45645456456
```

👉 To find a file’s index (inode) number:

```bash
ls -i
```

---

## 🔗 Piping `|`

```bash
cmd1 | cmd2
```

➡ Passes output of `cmd1` as input to `cmd2`

Example:

```bash
cat filename | wc -l
```

---

## 👤 User Management

### ➕ Add User

```bash
adduser username
```

---

### 🧬 User Info

```bash
id username       # UID + GID
id -u username    # User ID only
id -g username    # Group ID only
```

---

### 🔁 Switch User

```bash
su - username     # Switch to another user
exit              # Go back to previous user
logout            # Also returns to previous user
```

---

### 🔐 Set/Change Password

```bash
passwd username
```

---


## 👥 User & Group Management

### 🗑️ Deleting Users & Groups

```bash
userdel username              # Delete user (keep home dir)
userdel -r username           # Delete user and remove home dir

gpasswd groupname             # Set password for a group

grep groupname /etc/group     # Search group details
grep groupname /etc/gshadow   # Search secure group info

groupdel groupname            # Delete a group
```

---

## 🧑‍💻 Advanced User & Group Management

```bash
useradd -u 2000 username         # Create user with custom UID
usermod -u 2001 username         # Change UID of existing user

groupadd -g 9000 groupname       # Create group with custom GID
groupmod -g 9001 groupname       # Modify GID of group

useradd -c "COMMENT" username    # Add user with description
usermod -c "NEW COMMENT" username # Modify comment for a user

useradd -m -d /home/homeName username  # Create user with custom home dir
mkdir /home/homeName
usermod -d /home/newhomeName username  # Change existing home dir

useradd -s /bin/nologin username       # Create user with non-login shell
usermod -s /bin/bash username          # Change user shell to bash

# Check user/group info:
grep username /etc/passwd
grep groupname /etc/group
```

---

## 🔍 `grep` – Pattern Searching in Files

### 🔤 Basic Syntax

```bash
grep "string" filename
grep "string1\|string2" filename   # OR operator
```

---

### 🚫 Inverse Match

```bash
grep -v "string" filename   # Show lines NOT containing "string"
```

---

### 🔠 Case-Insensitive Match

```bash
grep -i "s" filename
```

---

### 💡 Metacharacters

```bash
^     # Start of line
$     # End of line

grep -i "^s" filename   # Lines starting with 's'
grep -i "s$" filename   # Lines ending with 's'
```

---

### 🎯 Only Match Output

```bash
grep -o "string" filename   # Print only the matched part
```

---

### ⬆️⬇️ Lines Before & After Match

```bash
grep -B 1 "^i" filename      # 1 line Before match
grep -A 1 "^i" filename      # 1 line After match
grep -A 1 -B 1 "^i" filename # 1 line Before and After
```

---

## 📏 Pattern / Regex Matching

### 🔤 Character Classes

```bash
[a-z]         # lowercase letters
[A-Z]         # uppercase letters
[0-9]         # digits
[a-zA-Z0-9]   # alphanumeric
```

---

## ✨ Extended `grep` (egrep or grep -E)

```bash
grep -E "pattern" filename
egrep "pattern" filename
```

🔁 **Repetition with `{}`**

```bash
[a-z]{10}       # Exactly 10 lowercase letters
[a-z]{10,20}    # Between 10 and 20 lowercase letters
[a-z]{10,}      # At least 10 lowercase letters
```

> 📝 You can mix character classes and ranges to match complex patterns effectively.

---

## 📝 VIM Editor – Basics & Commands

### 🖊️ Insert & Command Mode

```bash
i       # Insert mode (start typing)
Esc     # Exit insert mode (return to command mode)
```

---

### 📄 Navigation & Editing

```bash
G       # Go to end of file
yy      # Yank (copy) current line
nyy     # Yank n lines
p       # Paste below the cursor
P       # Paste above the cursor
dd      # Delete (cut) current line
ndd     # Delete (cut) n lines
u       # Undo last change
Ctrl + r # Redo last undone change
```

---

### 📌 Last Line Mode Commands

```bash
:set nu         # Show line numbers
:set nonu       # Hide line numbers

:10             # Go to line 10
/word           # Search 'word'
n               # Next match
N               # Previous match

:%s/old/new/    # Replace first occurrence
:%s/old/new/g   # Replace all occurrences

:w              # Save file
:wq             # Save and quit
:q              # Quit
:w!             # Force save
:q!             # Force quit without saving
:wq!            # Force save and quit
```

---

## 🔄 System Package Management (`apt`)

### 🔃 Update & Upgrade

```bash
apt update       # Updates package lists (no install)
apt upgrade      # Installs all available updates
```

---

### 📦 Install & Remove Packages

```bash
apt install package_name        # Install package
apt autoremove package_name     # Remove package + unused dependencies
```

---

## 👥 Group Membership in Linux

### 🧾 Types of Membership

| Membership    | Description                                                        |
| ------------- | ------------------------------------------------------------------ |
| **Primary**   | Assigned at user creation, controls login group (in `/etc/passwd`) |
| **Secondary** | Additional groups (in `/etc/group`), do not affect login           |

---

### 1️⃣ Primary Group Example

```bash
groupadd developers                  # Create a group
useradd -g developers john           # Create user with primary group
id john                              # View group memberships
```

---

### 2️⃣ Secondary Group Example

```bash
groupadd testers                     # Create a group
useradd -G testers jane              # Add user to secondary group
id jane                              # View group memberships
```

---

### 👤 Advanced User Creation with Group

```bash
useradd -G groupname -m -d /home/kids -s /bin/bash username
```

🧩 Explanation:

* `-G groupname`: Secondary group
* `-m`: Create home directory
* `-d /home/kids`: Set custom home directory
* `-s /bin/bash`: Set shell as bash

---

### 📂 Check Group Info

```bash
cat /etc/group       # Lists all groups and their members
```

---

## 🔐 **File & Directory Permissions (Basic)**

### 📄 Listing Permissions

```bash
ls -l                # Long list with permissions, owner, group, etc.
ls -l filename       # Long list for a specific file
ls -ld directory     # Long list for a directory itself (not its contents)
ls -R                # Recursive list of directories and subdirectories
```

---

## 1️⃣ **Symbolic Method** of Permissions

### 🧩 Permission Types:

| Type    | Symbol |
| ------- | ------ |
| Read    | `r`    |
| Write   | `w`    |
| Execute | `x`    |

### 👥 User Types:

| Who    | Symbol |
| ------ | ------ |
| User   | `u`    |
| Group  | `g`    |
| Others | `o`    |
| All    | `a`    |

### ➕ Modifiers:

| Action      | Symbol |
| ----------- | ------ |
| Add         | `+`    |
| Remove      | `-`    |
| Set/Replace | `=`    |

---

### 🧪 Example Breakdown

```bash
-rw-r--r-- 1 root root 43 Sep 23 01:56 file1
# u: rw   g: r   o: r
```

📦 **Default Permissions:**

* **Files:** `644` → `rw-r--r--`
* **Directories:** `755` → `rwxr-xr-x`

---

### 🛠️ Changing Permissions – Symbolic

```bash
chmod u+rx file         # Give read & execute to user
chmod u-r,g+rw,o-rwx file
# Remove read from user, add rw to group, remove all from others
chmod u=rw file         # Set read & write only for user
chmod ugo=r file        # Read-only for everyone
chmod a=r file          # Same as above (a = all)
chmod +x file           # Add execute to everyone
```

---

## 2️⃣ **Numeric (Octal) Method**

| Permission | Binary | Octal |
| ---------- | ------ | ----- |
| `---`      | 000    | 0     |
| `--x`      | 001    | 1     |
| `-w-`      | 010    | 2     |
| `-wx`      | 011    | 3     |
| `r--`      | 100    | 4     |
| `rw-`      | 110    | 6     |
| `rwx`      | 111    | 7     |

---

### 🔧 chmod with Numbers

```bash
chmod 711 file         # rwx (user), --x (group), --x (others)
chmod 111 dir -R       # --x for all, recursively
```

---

## 🧮 **umask – Default Permissions Control**

### 📌 Commands

```bash
umask                 # Show current umask
umask 0000            # Set umask to 0000 (least restrictive)
```

---

### 🔍 Default Permissions = Base - umask

🗂️ **Directories:**
`777 - umask`
📄 **Files:**
`666 - umask`

#### 🧠 Example (umask = 0022):

| Type      | Calculation | Result              |
| --------- | ----------- | ------------------- |
| Directory | `777 - 022` | `755` → rwx r-x r-x |
| File      | `666 - 022` | `644` → rw- r-- r-- |

> 🔒 Note: Files **don’t get execute** permissions by default (even with umask 0000).

---

# 📁 OWNERSHIP IN LINUX 🔐

In Linux, **every file and directory** has:

* an **Owner (User)** 👤
* a **Group** 👥

Ownership decides **who can read, write, or execute** a file or directory.

---

## 🔍 Check Ownership of a File

Use `ls -l` to view ownership and permissions:

```bash
ls -l filename
```

### ✅ Example:

```bash
ls -l myfile.txt
```

**Output:**

```
-rw-r--r-- 1 john developers 1024 Mar 10 10:30 myfile.txt
```

Here:

* `john` → **Owner** 👤
* `developers` → **Group** 👥

---

## 🔄 Change User Ownership – `chown`

Use `chown` to change the owner of a file:

```bash
chown username filename
```

### ✅ Example:

```bash
chown john myfile.txt
```

Now **john** becomes the owner of `myfile.txt`.

---

## 🧑‍🤝‍🧑 Change Group Ownership – `chgrp`

To change the **group** ownership:

```bash
chgrp groupname filename
```

### ✅ Example:

```bash
chgrp developers myfile.txt
```

---

## 🔁 Change Both Owner and Group

You can change both at once with:

```bash
chown username:groupname filename
```

### ✅ Example:

```bash
chown john:developers myfile.txt
```

Now `john` is the owner, and `developers` is the group.

---

## 👥 What if the New Owner is from "Others"?

In Linux:

* **Owner** → The user who created the file
* **Group** → A group of users
* **Others** → Everyone else

To give ownership to an "others" user:

---

### 🧭 Step 1: Change User Ownership

```bash
chown username filename
```

#### ✅ Example:

```bash
chown jane myfile.txt
```

Now **jane** is the owner, no longer in "others".

---

### 🧭 Step 2: Add User to a Group

```bash
usermod -G groupname username
```

#### ✅ Example:

```bash
usermod -G developers jane
```

Now **jane** is part of the `developers` group.

---

### 🧭 Step 3: Change Group Ownership

```bash
chgrp groupname filename
```

#### ✅ Example:

```bash
chgrp developers myfile.txt
```

---

## 🔁 RECURSIVE Ownership Changes

Use the `-R` flag to apply changes **recursively** to all files and subdirectories.

---

### 👤 Recursive User Ownership:

```bash
chown -R username directoryname
```

#### ✅ Example:

```bash
chown -R john /mydir
```

---

### 👥 Recursive Group Ownership:

```bash
chgrp -R groupname directoryname
```

#### ✅ Example:

```bash
chgrp -R developers /mydir
```

---

### 🔄 Recursive Owner + Group Change:

```bash
chown -R username:groupname directoryname
```

#### ✅ Example:

```bash
chown -R john:developers /mydir
```

---

## 🔎 Find Files by Owner or Group

Sometimes you want to list files owned by a specific user or group.

---

### 👤 Find Files Owned by a User:

```bash
find /path/to/search -user username
```

#### ✅ Example:

```bash
find /home -user john
```

---

### 👥 Find Files Belonging to a Group:

```bash
find /path/to/search -group groupname
```

#### ✅ Example:

```bash
find /home -group developers
```

---

📌 **Tips to Remember**:

* `chown` → Change Owner (and optionally group)
* `chgrp` → Change Group only
* Use `-R` for recursive changes
* Use `ls -l` to check ownership anytime

---

# 🛡️ ACCESS CONTROL LIST (ACL)

ACL (Access Control List) gives **fine-grained permissions** to users **without changing** file ownership or basic permissions (`rwx`).

---

### ✅ Key Points:

* ACL allows assigning **custom permissions** to specific users or groups.
* If ACL is applied on a file, you will see a **`+` sign** at the end of the permissions when you use `ls -l`.

#### 👀 Example:

```bash
ls -l file1.txt
-rw-r--r--+ 1 user group 1234 May 04 10:00 file1.txt
```

---

## ✍️ Set ACL

```bash
setfacl -m u:username:permissions filename
```

🔸 Example:

```bash
setfacl -m u:j1:rw file1.txt
```

Gives **read and write** permission to user `j1` on `file1.txt`.

---

## 👥 Set Group ACL

```bash
setfacl -m g:groupname:permissions filename
```

🔸 Example:

```bash
setfacl -m g:developers:rw file1.txt
```

---

## 📖 View ACL

```bash
getfacl filename
```

🔸 Example:

```bash
getfacl file1.txt
```

---

# ⚙️ PROCESS MANAGEMENT

---

## 🔄 What is a Process?

* A **process** is any **running program**.
* You can run **multiple instances** of the same program, each being its own process.
* The **shell** (your terminal session) is also a process.

---

## 🆔 Process ID (PID)

* Every process has a unique **PID (Process ID)**.
* Each process also has a **PPID (Parent Process ID)**.
* The **`init`** process (PID 1) is the parent of all orphan processes.

---

## 🚀 Creating a Process

### 🖥️ Terminal 1:

```bash
sleep 100
```

### 🖥️ Terminal 2:

```bash
ps -la
```

This will show details including PID and PPID.

---

## 📊 Process Info & Roles

The kernel tracks:

* Process **priority**
* **Address space**
* Allowed **file access**
* Process roles:

  * Parent 👨‍👦
  * Child 👶
  * Zombie 🧟

---

## 🧟 What is a Zombie Process?

* If a **parent process dies before its child**, the child process becomes a **zombie**.
* Zombie processes are **not running**, just waiting for the parent to acknowledge their termination.
* These are eventually "adopted" and cleaned up by `init`.

### 👇 Example Flow:

```
PPID[kill]
   └── PID[kill]

PPID[die]
   └── PID[zombie]
```

---

## 🧰 Process Monitoring Tools

### 🔧 Commands:

* `ps` – Show current processes
* `top` – Live view of system processes
* `htop` – Enhanced, interactive version of `top` (if installed)

### 🚀 Common Usage:

```bash
ps                # Show processes of current shell
ps -l             # Show PPID (Parent Process ID)
ps -e             # Show all system processes
ps -la            # Detailed listing
top               # Live process viewer
```

Press **`q`** to exit from `top`.

---

## 💀 Killing Processes

### 🔫 Kill by PID:

```bash
kill PID
```

### 🔫 Force Kill:

```bash
kill -9 PID
```

### 🛑 Kill by Name:

```bash
pkill sleep
killall sleep
```

---

## 🎭 Background Processes

### Run in background:

```bash
sleep 10000 &
sleep 20000 &
```

---

### View background jobs:

```bash
jobs
```

#### Output:

```
[1]-  Running                 sleep 10000 &
[2]+  Running                 sleep 20000 &
```

* `-` → Second last job
* `+` → Last added job

---

### View with PID:

```bash
jobs -l
```

---

### Bring job to foreground:

```bash
fg %2
```

---

### Stop (pause) foreground job:

Press `Ctrl + Z`

---

### Resume in background:

```bash
bg %2
```

---

📌 **Recap**:

* `sleep` creates a process that just waits.
* `jobs` shows background processes.
* `fg`, `bg`, `kill`, and `ps` are essential for process control.
* Zombies aren’t dangerous—but too many = system mess.

---

# 🐚 SHELL SCRIPTING IN LINUX

Shell scripting allows you to execute **multiple commands** by running a **single file** (like an automation shortcut).

---

## 📁 Script Basics

✅ **File extension**: `.sh` or `.bash`
✅ **Shebang** (`#!`) tells the system which shell to use.

---

### ✍️ Create a Script:

```bash
# vim runme.sh
```

#### 📝 Example:

```bash
#!/bin/bash        # ← Shebang (env declaration)
echo "Running multiple commands!"
date
whoami
```

### 💾 Save & Quit:

Press `ESC` then type `:wq`

---

## ✅ Make It Executable:

```bash
chmod u+x runme.sh
```

---

## ▶️ Run the Script:

```bash
./runme.sh
# OR
bash runme.sh
```

---

## 🐞 Debugging a Script:

```bash
bash -x runme.sh
```

This shows **each command** as it's being executed.

---

# 🧮 VARIABLES

Variables store data like text or numbers.

---

### ✨ Simple Example:

```bash
#!/bin/bash
target="example.com"
echo "Target: $target"
echo "Target: ${target}"
```

---

### 📥 Read from User:

```bash
#!/bin/bash
read -p "Enter the target: " target
echo "Target: ${target}"
echo "Target or default: ${target:-DEFAULT}"
```

---

### 🔁 Assign via Command:

```bash
target=$(whoami)        # Recommended
# OR
target=`whoami`         # Older syntax
echo "Current user: $target"
```

---

# ➗ ARITHMETIC

### 🧮 Fixed Values:

```bash
x=10
y=2
echo $(($x + $y))
```

---

### 🧮 User Input:

```bash
read -p "Enter first: " x
read -p "Enter second: " y
echo "Sum: $(($x + $y))"
```

---

### 🧮 Using `expr`:

```bash
expr 2 + 2
expr 2 - 2
expr 2 / 2
expr 2 \* 2
```

> Note: Escape `*` with `\`

✅ Combine with echo:

```bash
echo "Addition: $(expr $a + $b)"
```

---

# ⚖️ CONDITIONAL STATEMENTS

Used to perform decisions based on conditions.

---

## 📌 Syntax Forms:

1. `if...then...fi`
2. `if...then...else...fi`
3. `if...then...elif...fi`
4. `if...then...elif...else...fi`

---

### 1️⃣ if...then...fi

```bash
#!/bin/bash
read -p "Enter a number: " a

if [[ $a == "0" ]]; then
    echo "You entered zero."
fi
```

---

### 2️⃣ if...then...else...fi

```bash
#!/bin/bash
read -p "Enter a number: " a

if [[ $a == "0" ]]; then
    echo "Zero is neutral"
else
    echo "Not zero!"
fi
```

---

### 3️⃣ if...then...elif...fi

```bash
#!/bin/bash
read -p "Enter a number: " a

if [[ $a == "0" ]]; then
    echo "Zero"
elif [[ $a == "1" ]]; then
    echo "One"
fi
```

---

### 4️⃣ if...then...elif...else...fi

```bash
#!/bin/bash
read -p "Enter a number: " a

if [[ $a == "0" ]]; then
    echo "Zero"
elif [[ $a == "1" ]]; then
    echo "One"
else
    echo "Neither zero nor one"
fi
```

---

### 💡 Bonus Tips:

* Use `[[ ]]` for test conditions.
* Variables should be **quoted** if user input is expected (to avoid issues with spaces or empty strings).
* Always test your scripts using `bash -x script.sh`.

---

# 🔁 SHELL SCRIPTING – OPERATORS, LOOPS, REDIRECTION

---

## 1️⃣ RELATIONAL OPERATORS

Used for **comparing values**, either strings or numbers.

### 🔡 String Comparisons:

```bash
[[ str1 == str2 ]]     # Equal
[[ str1 != str2 ]]     # Not Equal
[[ str1 < str2 ]]      # Less than (ASCII)
[[ str1 > str2 ]]      # Greater than (ASCII)
[[ str1 =~ regex ]]    # Matches regex
[[ str1 !~ regex ]]    # Doesn't match regex
```

### 🔢 Numeric Comparisons:

```bash
[[ $a -eq $b ]]    # Equal
[[ $a -ne $b ]]    # Not Equal
[[ $a -lt $b ]]    # Less than
[[ $a -le $b ]]    # Less than or equal
[[ $a -gt $b ]]    # Greater than
[[ $a -ge $b ]]    # Greater than or equal
```

---

## 📄 FILE OPERATIONS

Check file/directory properties.

```bash
[[ -e file ]]    # Exists
[[ -r file ]]    # Readable
[[ -w file ]]    # Writable
[[ -x file ]]    # Executable
[[ -f file ]]    # Is a file
[[ -d dir  ]]    # Is a directory
[[ -z var  ]]    # Empty string
[[ -n var  ]]    # Non-empty string
[[ -s file ]]    # File size > 0
[[ ! -s file ]]  # File is empty
```

---

## 2️⃣ LOGICAL OPERATORS

Combine multiple conditions.

```bash
[[ $a == "1" ]] && [[ $b == "2" ]]   # AND
[[ $a == "1" ]] || [[ $b == "2" ]]   # OR
[[ ! -z $var ]]                      # NOT empty
```

---

# 🧠 CONDITIONALS RECAP

---

### 1) `if...then...fi`

```bash
if [ $a == "1" ]; then
  echo "It done"
fi
```

---

### 2) `if...then...else...fi`

```bash
if [ $a == "1" ]; then
  echo "It done"
else
  echo "WTF"
fi
```

---

### 3) `if...elif...fi`

```bash
if [ $a == "1" ]; then
  echo "It done"
elif [ $a == "2" ]; then
  echo "Its FUN"
fi
```

---

### 4) `if...elif...else...fi`

```bash
if [ $a == "1" ]; then
  echo "It done"
elif [ $a == "2" ]; then
  echo "Its FUN"
else
  echo "WTF"
fi
```

---

# 🔁 WHILE LOOP

Repeats code **as long as the condition is true**.

```bash
while true
do
  echo "LOL"
done
```

💡 One-liner:

```bash
while true; do echo "LOL"; done
```

---

# 📥 INPUT REDIRECTION

Used to read input from a file.

```bash
# Create a file
cat > file
Dheeraj
Tabish
Amruta
Mayur
```

### Read using `while`:

```bash
while read -r name; do
  echo "Name: $name"
done < file
```

✅ OR using pipe:

```bash
cat file | while read -r name; do
  echo "Name: $name"
done
```

---

# 🧰 TOOL – DNS BASICS

| Type          | Example             |
| ------------- | ------------------- |
| 🌐 Domain     | `example.com`       |
| 🧷 Sub-domain | `admin.example.com` |

**DNS (Domain Name System)**
🧭 Converts **names ⇄ IP addresses**

* `Name → IP`: e.g., `google.com` → `142.250.190.14`
* `IP → Name`: Reverse DNS (PTR record)

---

# 📝 SHELL SCRIPTS: TARGETING, FUNCTIONS, AND CASE

---

## 🎯 **Targeting with a Shell Script**

Script that checks subdomains for a given target domain. The script uses **`host`** command to resolve subdomains:

```bash
#!/bin/bash
target=$1       # Target domain passed as an argument
file=$2         # File containing subdomains

# Loop through each subdomain in the file
while read -r sub; do
    if host "$sub.$target" &> /dev/null; then  # Check if the subdomain resolves
        echo "$sub.$target"
    fi
done < $file
```

---

## 🔄 **Nested if Conditionals**

Handling file read/write permissions in a nested structure.

```bash
#!/bin/bash
file=$1   # File passed as an argument

# Check if file exists
if [ -f "$file" ]; then
    # Check if file is writable
    if [ -w "$file" ]; then
        echo "Enter text:"
        cat >> $file   # Append text to the file
    else
        echo "Not writable"
    fi
else
    echo "$file not found"
fi
```

---

## 🛠️ **Functions in Shell Script**

Creating reusable code blocks (functions) for common tasks.

```bash
#!/bin/bash
target=$1   # Target domain
file=$2     # File containing subdomains

# Define function to brute-force subdomains
brute(){
    while read -r sub; do
        if host "$sub.$target" &> /dev/null; then  # Resolve subdomain
            echo "$sub.$target"
        fi
    done < $file
}

# Check if file exists and run brute-force function
if [ -f "$file" ]; then
    brute
else
    echo "$file not found"
fi
```

---

## 🗂️ **Case Statements in Bash**

Using a **`case`** structure to handle multiple conditions in a clean way.

```bash
#!/bin/bash

# Function 1
f1(){
    echo "F1 is cool"
}

# Function 2
f2(){
    echo "F2 is awesome"
}

# Menu for user input
menu(){
    echo -e "1. Func 1\n2. Func 2\n3. Exit"
    read -p "Input> " a
}

menu   # Show menu

# Case statement for menu selection
case $a in
    "1") 
        f1  # Call function f1
        ;;
    "2")
        f2  # Call function f2
        ;;
    "3")
        exit  # Exit the script
        ;;
    *)
        echo "Very Good Day"  # Default case
        ;;
esac
```

---

# 📥 IO STREAMS IN LINUX

In Linux, **IO streams** allow programs to read and write data. There are **three types** of streams:

* **stdin** (file descriptor 0): Input stream.
* **stdout** (file descriptor 1): Output stream.
* **stderr** (file descriptor 2): Error stream.

### 📝 **stdin: Standard Input**

You can redirect input into a command, for example, by setting values from a file.

```bash
# Write to file
cat > file
redhat
redhat

# Read input from file using stdin
passwd nix < file
# Output: password set successfully
```

---

# 📤 **Standard Output (stdout)**

### 🌟 **Redirecting Output to a File**

You can redirect the standard output (stdout) to a file using the **`>`** operator.

```bash
# Redirect output of echo to a file
echo "LOL" > file

# Display the contents of the file
cat file
# Output: LOL
```

---

### 🚮 **Redirecting Output to /dev/null**

**`/dev/null`** is a special device file that discards anything sent to it (like a "black hole" for data). Useful for ignoring unnecessary output.

```bash
# Send the output to /dev/null, discarding it
echo "LOL" > /dev/null
```

This command will execute, but it will not display anything because the output is discarded.

---

# ⚠️ **Standard Error (stderr)**

### 🔴 **Redirecting Error to /dev/null**

To suppress error messages, redirect **stderr** to **/dev/null** using **`2>`**.

```bash
# A non-existent command that will generate an error
ppwwdd 2> /dev/null
```

* Here, the **`2>`** operator redirects the standard error to **`/dev/null`**, preventing the error message from appearing on the screen.

---

### 🏷️ **Redirecting Only the Errors**

Using **`2>`** allows you to redirect only error output (stderr) while leaving standard output intact.

```bash
# Redirect errors to /dev/null
pwd 2> /dev/null
```

The **`pwd`** command outputs the current directory, but if any error occurs (e.g., permissions issue), it will be discarded.

---

### 🔀 **Redirecting Both Output and Error**

To redirect **both output (stdout) and errors (stderr)** to the same location, use **`&>`**.

```bash
# Redirect both output and errors to /dev/null
pwd &> /dev/null
```

In this case, both the output and any potential error (if **`pwd`** encounters one) will be discarded.

---

### 🔥 **Silencing All Output (Including Errors)**

If you want to completely silence both the output and errors from a command, simply redirect both:

```bash
# Redirect both output and error for a non-existent command
ppwwdd &> /dev/null
```

This ensures that both the standard output and the error messages are discarded, making the command execute silently.

---
