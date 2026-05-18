
Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---

# Bandit Level 0

## 🎯 Objective

The objective of **Bandit Level 0** is to connect to the Bandit server using SSH and find the password for the next level.

Each Bandit level depends on the password collected from the previous level.

---

## 🧠 Level Information

- **Username:** `bandit0`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password:** `bandit0`

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered:

```bash
bandit0
```

---

### 2. List the Files

After logging in successfully, I used the `ls` command to list the files in the current directory:

```bash
ls
```

The output showed a file named:

```bash
readme
```

---

### 3. Read the File Content

To read the content of the `readme` file, I used the `cat` command:

```bash
cat readme
```

---

## 🔑 Password Found

After reading the file, I found the password for the next level:

```bash
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

---

## ✅ What I Learned

In this level, I learned how to:

- Connect to a remote server using SSH
- Use a custom SSH port
- List files using the `ls` command
- Read file content using the `cat` command
- Retrieve the password needed for the next Bandit level

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 1**.

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```