Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 11

## 🎯 Objective

The objective of **Bandit Level 11** is to log in to the Bandit server using the password from **Level 10** and find the password for the next level.

In this level, the password is stored in the file `data.txt`.  
All lowercase letters `a-z` and uppercase letters `A-Z` have been rotated by 13 positions.

This encryption method is called **ROT13**.

---

## 🧠 Level Information

- **Username:** `bandit11`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 10:**

```bash
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

---

### 2. Understand the Challenge

The challenge says that the password is stored in:

```bash
data.txt
```

The text inside the file is encoded using **ROT13**, which means each letter is rotated by 13 positions.

For example:

```bash
A becomes N
B becomes O
a becomes n
b becomes o
```

So I needed to decode the file using the `tr` command.

---

### 3. First Attempt

I tried using the `tr` command to transform the letters:

```bash
cat data.txt | tr 'A~Z' 'a~z'
```

However, this was not the correct ROT13 syntax.

---

### 4. Decode the ROT13 Text

To correctly decode ROT13, I used this command:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

A shorter way to write the same command is:

```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
```

### Command Explanation

```bash
cat data.txt
```

Displays the content of the file.

```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Rotates all uppercase and lowercase letters by 13 positions.

```bash
|
```

The pipe operator sends the output of `cat` into the `tr` command.

---

## 🔑 Password Found

The password for **Bandit Level 12** is:

```bash
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

---

## ✅ What I Learned

In this level, I learned how to:

- Understand ROT13 encoding
- Use the `tr` command to translate characters
- Decode rotated text from a file
- Work with uppercase and lowercase character ranges
- Combine commands using the pipe operator `|`

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 12**.

```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```
