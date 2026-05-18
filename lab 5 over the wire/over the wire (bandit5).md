Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 5

## 🎯 Objective

The objective of **Bandit Level 5** is to log in to the Bandit server using the password from **Level 4** and find the password for the next level.

In this level, the password is stored somewhere inside the `inhere` directory.  
The correct file has the following properties:

- Human-readable
- 1033 bytes in size
- Not executable

---

## 🧠 Level Information

- **Username:** `bandit5`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 4:**

```bash
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

---

### 2. List the Files and Directories

After logging in successfully, I used the `ls` command:

```bash
ls
```

The output showed many directories:

```bash
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
```

---

### 3. Check for Hidden Files

I used the following command to show detailed information and check if there were hidden files:

```bash
ls -lah
```

There were no useful hidden files in the current directory.

The challenge description says that the password is stored in the only file that is:

- Human-readable
- 1033 bytes in size
- Not executable

So I needed to search for a file with these exact properties.

---

### 4. Search for the Correct File

To find the correct file, I used the `find` command:

```bash
cat $(find . -type f -size 1033c ! -executable)
```

### Command Explanation

```bash
find .
```

Searches inside the current directory.

```bash
-type f
```

Searches for files only.

```bash
-size 1033c
```

Searches for files that are exactly `1033` bytes in size.

```bash
! -executable
```

Searches for files that are not executable.

```bash
cat $(...)
```

Reads the content of the file found by the `find` command.

---

## 🔑 Password Found

The password for **Bandit Level 6** is:

```bash
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

> ⚠️ Note: Make sure to copy the password exactly as shown in your terminal because it maybe diffrent.

---

## ✅ What I Learned

In this level, I learned how to:

- Search inside multiple directories using `find`
- Filter files by type using `-type f`
- Search for files by exact size using `-size`
- Exclude executable files using `! -executable`
- Use command substitution `$()` to pass the result of one command into another command
- Read the correct file using `cat`

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 6**.

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```