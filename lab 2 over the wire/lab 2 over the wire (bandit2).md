Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 2

## 🎯 Objective

The objective of **Bandit Level 2** is to log in to the Bandit server using the password from **Level 1** and find the password for the next level.

In this level, the password is stored in a file that contains spaces in its filename.

---

## 🧠 Level Information

- **Username:** `bandit2`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 1:**

```bash
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

---

### 2. List the Files

After logging in successfully, I used the `ls` command to list the files in the current directory:

```bash
ls
```

The output showed a file named:

```bash
spaces in this filename
```

---

### 3. Check File Details and Permissions

I used the following command to display more details about the file, including permissions, owner, group, size, and modification date:

```bash
ls -lah
```

From the output, I confirmed that `spaces in this filename` is a regular file.

---

### 4. Try to Read the File

First, I tried to read the file normally using `cat`:

```bash
cat spaces in this filename
```

However, this failed because Linux treats each word as a separate argument.

I also tried using `more`:

```bash
more spaces in this filename
```

This also failed for the same reason.

---

### 5. Escape the Spaces

To read a file that contains spaces in its name, I escaped each space using a backslash `\`.

I used the following command:

```bash
cat spaces\ in\ this\ filename
```

Another correct way is to use `./` before the filename:

```bash
cat ./spaces\ in\ this\ filename
```

This command successfully displayed the content of the file.

---

## 🔑 Password Found

The password for **Bandit Level 3** is:

```bash
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

---

## ✅ What I Learned

In this level, I learned that:

- Filenames in Linux can contain spaces.
- Spaces separate command arguments in the terminal.
- To access a file with spaces in its name, I can escape the spaces using `\`.
- I can also use quotes to handle filenames with spaces, like this:

```bash
cat "spaces in this filename"
```

- The `ls -lah` command helps show detailed file information and permissions.

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 3**.

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```
