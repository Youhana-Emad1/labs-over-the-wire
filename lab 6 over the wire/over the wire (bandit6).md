Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 6

## 🎯 Objective

The objective of **Bandit Level 6** is to log in to the Bandit server using the password from **Level 5** and find the password for the next level.

In this level, the password is stored somewhere on the server and has specific properties.

The password file is:

- Owned by user `bandit7`
- Owned by group `bandit6`
- 33 bytes in size

---

## 🧠 Level Information

- **Username:** `bandit6`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 5:**

```bash
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

---

### 2. List the Files

After logging in successfully, I used the `ls` command to list the files in the current directory:

```bash
ls
```

There were no useful visible files.

---

### 3. Show Hidden Files and Permissions

I used the following command to show hidden files and detailed permissions:

```bash
ls -lah
```

I found some hidden files such as:

```bash
.profile
.bashrc
.bash_logout
```

However, these files did not contain the password.

---

### 4. Understand the File Requirements

The challenge says that the password file has the following properties:

```bash
owned by user bandit7
owned by group bandit6
33 bytes in size
```

So I needed to search the whole server for a file matching these conditions.

---

### 5. Search for the Correct File

I used the `find` command to search from the root directory `/`:

```bash
find / -type f -user bandit7 -group bandit6 -size 33c
```

### Command Explanation

```bash
find /
```

Searches the whole filesystem starting from the root directory.

```bash
-type f
```

Searches for files only.

```bash
-user bandit7
```

Searches for files owned by the user `bandit7`.

```bash
-group bandit6
```

Searches for files owned by the group `bandit6`.

```bash
-size 33c
```

Searches for files that are exactly `33` bytes in size.

---

### 6. Read the Password File

After finding the correct file, I used `cat` to read it:

```bash
cat $(find / -type f -user bandit7 -group bandit6 -size 33c)
```

A cleaner version of the command is:

```bash
cat $(find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null)
```

The `2>/dev/null` part hides permission denied errors.

---

## 🔑 Password Found

The password for **Bandit Level 7** is:

```bash
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

---

## ✅ What I Learned

In this level, I learned how to:

- Search the whole Linux filesystem using `find`
- Search files by owner using `-user`
- Search files by group using `-group`
- Search files by exact size using `-size`
- Hide permission errors using `2>/dev/null`
- Use command substitution `$()` to pass the result of `find` into `cat`

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 7**.

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```