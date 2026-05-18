Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
### . List the Files

After logging in successfully, I used the `ls` command to list the files in the current directory:

```bash
ls
```

The output showed a file named:

```bash
-
```

---

### . Check File Details and Permissions

I used the following command to display more details about the file, including permissions, owner, group, size, and modification date:

```bash
ls -lah
```

From the output, I confirmed that `-` is a regular file.

---

### . Try to Read the File

First, I tried to read the file using the `cat` command:

```bash
cat -
```

However, this did not work as expected because `-` is a special character in Linux commands.  
In many commands, `-` means reading from standard input instead of reading from a file.

---

### . Read the File Correctly

To read a file named `-`, I used the `more` command:

```bash
more -
```

This displayed the content of the file and revealed the password for the next level.

---

## 🔑 Password Found

The password for **Bandit Level 2** is:

```bash
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

---

## ✅ What I Learned

In this level, I learned that:

- Some filenames can contain special characters.
- The filename `-` can confuse commands because it is treated as standard input.
- The `ls -lah` command is useful for checking file details and permissions.
- The `more` command can be used to read file content.
- Linux commands may behave differently when dealing with special filenames.

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 2**.

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```