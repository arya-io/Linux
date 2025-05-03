## QUESTIONS

1. **How do you print the lines between 5 and 10 (inclusive)?**  
Answer:  
```bash
head -10 filename | tail -6
```

2. **Create a new file `new.txt` that is a concatenation of `file1.txt` and `file2.txt`.**  
Answer:  
```bash
cat file1.txt file2.txt > new.txt
```

3. **What is the output of the following code?**
```bash
os=Unix
echo 1.$os 2."$os" 3.'$os' 4.$os
```
Answer:  
```bash
1.Unix 2.Unix 3.$os 4.Unix
```

4. **To feed standard output of one command to standard input of another in a single shell session. Example?**  
Answer:  
```bash
|
```
(This is called a *pipe*.)

5. **Output of this command:**
```bash
cat < file1 >> file2 | file3
```
Answer:  
Syntax error

## Permissions & Users

### Q. Create a collaborative directory `/common/adm` with the following:

* Group ownership should be `admin`.
* Directory readable, writable, and accessible to members of `admin` only (except root).

```bash
mkdir -p /common/adm
chgrp admin /common/adm
chmod 770 /common/adm
```

---

### Q. Copy `/etc/fstab` to `/var/tmp` and set these permissions:

* Owner: `root`
* Group: `root`
* Not executable by anyone
* User `harry`: read/write
* User `natasha`: no read/write
* Others: read only

```bash
cp -rfv /etc/fstab /var/tmp/
chown root /var/tmp/fstab
chgrp root /var/tmp/fstab
setfacl -m u:harry:6 /var/tmp/fstab
setfacl -m u:natasha:0 /var/tmp/fstab
chmod o=r /var/tmp/fstab
```

---

### Q. Create a `qstat` command alias to run a specific `ps` command:

```bash
alias qstat='ps -eo pid,tid,class,rtprio,ni,pri,psr,pcpu,stat,wchan:14,comm'
qstat
```

---

### Q. Create the following users and groups:

* A group called `admin`:

```bash
groupadd admin
```

* User `harry` in `admin` group:

```bash
useradd -G admin harry
```

* User `natasha` in `admin` group:

```bash
useradd -G admin natasha
```

* User `sarah` (no shell, not in `admin`):

```bash
useradd -s /bin/nologin sarah
```

* Set password `redhat@123?` for all:

```bash
passwd harry
passwd natasha
passwd sarah
```

---

### Q. Change file `schedule.txt` permissions:

* Owner and group can edit.
* Others can only *view*.

Correct answer:

```bash
chmod 664 schedule.txt
```

(Where owner & group = write & read (6), others = read-only (4).)

---

### Q. If umask is `077` and user `jason` creates `/tasks`, what are the permissions?

Umask formula:

```bash
777 - 077 = 700
```

So `/tasks` will have `drwx------` (owner full, others no access).

---

## Assignment 2: Shell Script (Menu Driven)

Write a script that shows this menu:

```
1. Make a file
2. Display contents
3. Copy the file
4. Rename the file
5. Delete the file
6. Exit
```

### Code:

```bash
#!/bin/bash

while true
do
    echo "Welcome to Menu"
    echo "------------------------"
    echo "1. Make a file"
    echo "2. Display contents"
    echo "3. Copy the file"
    echo "4. Rename the file"
    echo "5. Delete the file"
    echo "6. Exit"

    read -p "Enter your option: " option

    case $option in
    "1")
        read -p "Enter file name: " file_name
        if [[ -e "$file_name" ]]; then
            echo "Error: File already exists!"
        else
            echo "Enter some content. Press Ctrl + D to save."
            cat > "$file_name"
            echo "$file_name created successfully!"
        fi
        ;;
    "2")
        read -p "Enter file name: " file_name2
        if [[ -e "$file_name2" ]]; then
            cat "$file_name2"
        else
            echo "Error: File does not exist."
        fi
        ;;
    "3")
        read -p "Enter source file name: " srcfile
        if [[ -e "$srcfile" && -r "$srcfile" ]]; then
            read -p "Enter target file name: " trgfile
            if [[ ! -e "$trgfile" ]]; then
                cp "$srcfile" "$trgfile"
                echo "File copied."
            else
                echo "Error: Target file exists."
            fi
        else
            echo "Error: Source file does not exist or is not readable."
        fi
        ;;
    "4")
        read -p "Enter source file name: " srcfile
        if [[ -e "$srcfile" && -r "$srcfile" ]]; then
            read -p "Enter target file name: " trgfile
            if [[ ! -e "$trgfile" ]]; then
                mv "$srcfile" "$trgfile"
                echo "File renamed."
            else
                echo "Error: Target file exists."
            fi
        else
            echo "Error: Source file does not exist or is not readable."
        fi
        ;;
    "5")
        read -p "Enter file name: " file5
        if [[ -e "$file5" ]]; then
            if [[ -w "$file5" ]]; then
                read -p "Do you want to delete the file? Press 9 to confirm: " delt
                if [[ $delt == "9" ]]; then
                    rm "$file5"
                    echo "File deleted."
                else
                    echo "Deletion cancelled."
                fi
            else
                echo "Error: File is not writable."
            fi
        else
            echo "Error: File does not exist."
        fi
        ;;
    "6")
        exit
        ;;
    *)
        echo "Invalid option!"
        ;;
    esac
done
```

---
