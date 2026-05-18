Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 7

## 🎯 Objective

The objective of **Bandit Level 7** is to log in to the Bandit server using the password from **Level 6** and find the password for the next level.

In this level, the password is stored in a file called `data.txt`.  
The password is located next to the word:

```bash
millionth
```

---

## 🧠 Level Information

- **Username:** `bandit7`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 6:**

```bash
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

---

### 2. List the Files

After logging in successfully, I used the `ls` command to list the files in the current directory:

```bash
ls
```

I found a file called:

```bash
data.txt
```

---

### 3. Search for the Password

The challenge says that the password is located next to the word `millionth`.

Instead of reading the whole file manually, I used the `grep` command to search for the word:

```bash
cat data.txt | grep millionth
```

This command displayed the line that contains the word `millionth`.

A shorter way to write the same command is:

```bash
grep millionth data.txt
```

---

## 🔑 Password Found

The password for **Bandit Level 8** is:

```bash
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

---

## ✅ What I Learned

In this level, I learned how to:

- Use `grep` to search inside a file
- Find a specific word in a large text file
- Use the pipe operator `|` to pass output from one command to another
- Search more efficiently instead of reading the whole file manually

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 8**.

```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
```