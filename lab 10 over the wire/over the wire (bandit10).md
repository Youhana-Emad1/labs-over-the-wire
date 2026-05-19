Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 10

## 🎯 Objective

The objective of **Bandit Level 10** is to log in to the Bandit server using the password from **Level 9** and find the password for the next level.

In this level, the password is stored in the file `data.txt`, which contains **Base64 encoded data**.

---

## 🧠 Level Information

- **Username:** `bandit10`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 9:**

```bash
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

---

### 2. Understand the Challenge

The challenge says that the password is stored in the file:

```bash
data.txt
```

The file contains **Base64 encoded data**, so I needed to decode it to get the real password.

This lab focuses on understanding how Base64 encoding works and how to decode encoded data from the terminal.

---

### 3. First Attempt

At first, I used the following command:

```bash
cat data.txt | base64
```

This gave me another encoded output:

```bash
VkdobElIQmhjM04zYjNKa0lHbHpJR1IwVWpFM00yWmFTMkl3VWxKelJFWlRSM05uTWxKWGJuQk9WbW96Y1ZKeUNnPT0K
```

However, this was incorrect because I encoded the data again instead of decoding it.

---

### 4. Decode the Base64 Data

To decode Base64 data, I needed to use the `-d` option with the `base64` command:

```bash
cat data.txt | base64 -d
```

A shorter way to write the same command is:

```bash
base64 -d data.txt
```

### Command Explanation

```bash
cat data.txt
```

Displays the content of the file.

```bash
base64 -d
```

Decodes Base64 encoded data.

```bash
|
```

The pipe operator sends the output of the first command into the second command.

---

## 🔑 Password Found

The password for **Bandit Level 11** is:

```bash
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

---

## ✅ What I Learned

In this level, I learned how to:

- Identify Base64 encoded data
- Use the `base64` command in Linux
- Decode Base64 data using `base64 -d`
- Understand the difference between encoding and decoding
- Use the pipe operator `|` to pass file content into another command

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 11**.

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```