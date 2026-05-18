## Introduction

My name is **Youhana Emad**, and I am a **Junior Penetration Tester**.
This Markdown file contains my personal notes about essential **Linux commands** and **Bash scripting basics**. These notes are designed to help me understand and practice the most important commands used in Linux environments, especially commands related to system information, file management, permissions, processes, package management, and shell scripting.

As a junior pentester, Linux is a very important skill because many cybersecurity tools and penetration testing environments depend on it. This file will help me build a strong foundation in Linux, improve my command-line skills, and prepare for real-world cybersecurity and penetration testing tasks.

## 1. Basic Linux Information Commands

### Network Information
```bash
ifconfig
```
Shows information about network interfaces.

> Alternative command:
```bash
ip addr
```

### Memory Space
```bash
free
```
Shows information about RAM and swap memory.

Useful readable format:
```bash
free -h
```

### Hard Disk Space
```bash
df -h
```
Shows disk usage in human-readable format.

### CPU and Running Processes
```bash
ps aux
```
Shows all running processes with details such as user, CPU usage, memory usage, and PID.

### Kill a Process
```bash
kill PID
```
Example:
```bash
kill 1234
```
Kills the process with PID `1234`.

If the process does not stop:
```bash
kill -9 PID
```

---

## 2. Installing Applications in Linux

### Install Using APT
```bash
sudo apt install application-name
```

Example:
```bash
sudo apt install nano
```

### Install Using Snap
```bash
sudo snap install application-name
```

### Install a `.deb` Package
```bash
sudo dpkg -i application.deb
```

If dependencies are missing, run:
```bash
sudo apt install -f
```

### Run the Previous Command with `sudo`
```bash
sudo !!
```
This repeats the last command but runs it with administrator permissions.

---

## 3. File Permissions in Linux

Linux permissions are based on:

| Permission | Number | Symbol |
|---|---:|---|
| Read | 4 | r |
| Write | 2 | w |
| Execute | 1 | x |

Permission groups:

| Group | Meaning |
|---|---|
| Owner | The user who owns the file |
| Group | Users in the file group |
| Others | Everyone else |

Example permission format:

```text
rw-rw-r--
```

This means:

| Group | Permission |
|---|---|
| Owner | read + write |
| Group | read + write |
| Others | read only |

### View File Permissions
```bash
ls -lah
```

---

## 4. Common Linux Commands

### Show Current User
```bash
whoami
```

### Show Current Directory
```bash
pwd
```

### Read a File
```bash
cat xyz.txt
```

### Create or Edit a File Using Nano
```bash
nano xyz.txt
```

To save and exit in nano:

1. Press `CTRL + X`
2. Press `Y`
3. Press `Enter`

### Remove a File
```bash
rm xyz.txt
```

### Create a Folder
```bash
mkdir xyz
```

### Remove a Folder
```bash
rm -r xyz
```

### Move a File
```bash
mv xyz.txt /home
```

### Rename a File
```bash
mv xyz.txt yan.txt
```

### Copy a File
```bash
cp xyz.txt /home
```

### Print Text in Terminal
```bash
echo "Hello"
```

### Write Text Inside a File
```bash
echo "Hello" > xyz.txt
```

This overwrites the file.

### Append Text to a File
```bash
echo "Hello" >> xyz.txt
```

This adds the text without removing old content.

---

## 5. Changing File Permissions

### Give Full Permission
```bash
chmod 777 xyz.txt
```

This gives read, write, and execute permission to owner, group, and others.

> Note: `777` is not recommended for important files. Use it only for practice or temporary testing.

### Add Execute Permission
```bash
chmod +x xyz.txt
```

### Remove Read Permission
```bash
chmod a-r xyz.txt
```

---

## 6. Search, Count, and View File Content

### Search for a Word in a File
```bash
cat xyz.txt | grep "Hello"
```

Better way:
```bash
grep "Hello" xyz.txt
```

### Count Lines, Words, and Characters
```bash
cat xyz.txt | wc
```

To count only lines:
```bash
wc -l xyz.txt
```

### Show File Content Page by Page
```bash
more xyz.txt
```

Another useful command:
```bash
less xyz.txt
```

### Handle Spaces in File Names
If a file name contains spaces, use quotes:

```bash
cat "t o n.txt"
```

Or use backslash before each space:

```bash
cat t\ o\ n.txt
```

### Hide a File
In Linux, hidden files start with a dot `.`.

```bash
mv file.txt .file.txt
```

### Show Hidden Files
```bash
ls -lah
```

### Unhide a File
```bash
mv .file.txt file.txt
```

### Show File Type Information
```bash
file ./*
```

---

## 7. Connect to a VPS Using SSH

Example:

```bash
ssh root@segfault.net
```

Then enter the password when asked.

Example password from the notes:

```text
segfault
```

---

# Bash Scripting

## 8. Create and Run a Bash Script

### Create a Bash File
```bash
nano xyz.sh
```

### Bash Script Must Start With
```bash
#!/bin/bash
```

Example:

```bash
#!/bin/bash

echo "Hello from Bash"
```

### Run Bash Script Using `bash`
```bash
bash xyz.sh
```

### Make Script Executable
```bash
chmod +x xyz.sh
```

### Run Executable Script
```bash
./xyz.sh
```

---

## 9. Variables in Bash

### Create a Variable
```bash
variable_name="Hello"
```

### Print a Variable
```bash
echo "$variable_name"
```

### Store a File Path in a Variable
```bash
file="/home/xyz.txt"
cat "$file"
```

---

## 10. Bash Arguments

Arguments are values passed to the script when running it.

| Argument | Meaning |
|---|---|
| `$0` | Script name |
| `$1` | First argument |
| `$2` | Second argument |
| `$3` | Third argument |

### Example 1
Create file:

```bash
nano file.sh
```

Write:

```bash
#!/bin/bash

echo "$1"
```

Run:

```bash
bash file.sh Hello
```

Output:

```text
Hello
```

### Example 2
```bash
#!/bin/bash

echo "filename: $0 and your name: $1"
```

Run:

```bash
bash file.sh tony
```

Output:

```text
filename: file.sh and your name: tony
```

---

## 11. For Loop in Bash

### Print Numbers from 1 to 100
```bash
for i in {1..100}; do
  echo "$i"
done
```

### Read Words from a File
```bash
for i in $(cat xyz.txt); do
  echo "$i"
done
```

### Better Way to Read File Lines One by One
```bash
while read line; do
  echo "$line"
done < xyz.txt
```

---

# Sed Command

## 12. What is `sed` Used For?

`sed` is used for:

- Search and replace
- Log sanitization
- Mass text modification
- Deleting lines
- Editing files from the terminal

---

## 13. Search and Replace Using `sed`

### Replace One Word
```bash
echo "day" | sed 's/day/Hello/'
```

Output:

```text
Hello
```

### Replace Two Words
```bash
echo "hello world" | sed 's/hello/hi/; s/world/hi/'
```

Output:

```text
hi hi
```

### Syntax
```bash
sed 's/old_word/new_word/' < inputfile > newfile.txt
```

### Example
Original file content:

```text
tony emad
```

Command:

```bash
sed 's/tony/kero/' < file.txt > kero.txt
cat kero.txt
```

Output:

```text
kero emad
```

### Replace All Occurrences in a Line
Use `g` for global replacement:

```bash
sed 's/hi/a/g' < xyz.txt > new.txt
```

### Edit the Original File Directly
Use `-i`:

```bash
sed -i 's/tony/kero/g' file.txt
```

---

## 14. Delete Lines Using `sed`

### Delete Lines Containing a Word
```bash
sed '/tony/d' file.txt
```

### Delete Lines and Save the Change in the Same File
```bash
sed -i '/tony/d' file.txt
```

---

# User Input in Bash

## 15. Read User Input

### Basic Input
```bash
read name
echo "Name = $name"
```

### Input With Prompt
```bash
read -p "Enter your age: " age
echo "Age = $age"
```

### Secret Input, Useful for Passwords
```bash
read -sp "Enter your password: " pass
echo "Password is: $pass"
```

> Note: In real scripts, do not print passwords to the screen.

### Read the First Line From a File
```bash
read content < /etc/passwd
echo "$content"
```

This prints the first line of `/etc/passwd`.

---

# Command Substitution and Time

## 16. Store Command Output in a Variable

### Store Text Only
```bash
list='ls -lah'
echo "$list"
```

Output:

```text
ls -lah
```

### Store Command Result
```bash
list=$(ls -lah)
echo "$list"
```

This runs `ls -lah` and stores the output in the variable.

---

## 17. Timestamp and Sleep Delay

A timestamp is the number of seconds from `1970-01-01 00:00:00 UTC`.

Example to calculate sleep time:

```bash
start=$(date +%s)
sleep 3
end=$(date +%s)
diff=$((end - start))

echo "time sleep: $diff"
```

Output will be about:

```text
time sleep: 3
```

---

# If Conditions in Bash

## 18. Basic If Syntax

```bash
if [ condition ]; then
  echo "condition is true"
else
  echo "condition is false"
fi
```

---

## 19. Compare Numbers and Text

| Operator | Meaning |
|---|---|
| `-eq` | Equal numbers |
| `-gt` | Greater than |
| `-lt` | Less than |
| `=` | Equal text |

### Compare a Number
```bash
#!/bin/bash

value="10"

if [ "$value" -eq 10 ]; then
  echo "your value is equal 10"
else
  echo "your value is not equal 10"
fi
```

### Compare a Name
```bash
#!/bin/bash

read -p "Enter your name: " name

if [ "$name" = "Ahmed" ]; then
  echo "Hello Ahmed"
else
  echo "wrong name"
fi
```

---

# Quick Practice Commands

```bash
whoami
pwd
ls -lah
mkdir test
cd test
echo "Hello" > xyz.txt
cat xyz.txt
grep "Hello" xyz.txt
wc -l xyz.txt
cp xyz.txt copy.txt
mv copy.txt newname.txt
chmod +x xyz.txt
rm newname.txt
cd ..
rm -r test
```

---

# Summary

These notes cover the basics of:

- Linux information commands
- File and folder management
- Permissions
- Installing applications
- Viewing and searching files
- Bash scripting
- Variables and arguments
- Loops
- `sed`
- User input
- If conditions
