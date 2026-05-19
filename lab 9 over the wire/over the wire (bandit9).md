Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 9

## 🎯 Objective

The objective of **Bandit Level 9** is to log in to the Bandit server using the password from **Level 8** and find the password for the next level.

In this level, the password is stored in the file `data.txt`.  
The password is hidden inside one of the few human-readable strings and is preceded by several `=` characters.

---

## 🧠 Level Information

- **Username:** `bandit9`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 8:**

```bash
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

---

### 2. Understand the Challenge

The challenge says that the password is stored in the file:

```bash
data.txt
```

The password is inside one of the few human-readable strings and is preceded by several `=` characters.

So I needed to extract readable strings from the file and search for lines containing `=`.

---

### 3. Use the `strings` Command

I used the `strings` command to show human-readable text inside the file:

```bash
strings data.txt
```

This command extracts readable strings from binary or mixed-content files.

---

### 4. Search for Lines Containing `=`

To filter the output and show only the lines that contain `=`, I used `grep`:

```bash
strings data.txt | grep "="
```

### Command Explanation

```bash
strings data.txt
```

Extracts human-readable strings from `data.txt`.

```bash
grep "="
```

Searches for lines that contain the `=` character.

```bash
|
```

The pipe operator sends the output of the first command into the second command.

---

## 🔑 Password Found

The password for **Bandit Level 10** is:

```bash
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

---

## ✅ What I Learned

In this level, I learned how to:

- Use `strings` to extract human-readable text from a file
- Use `grep` to filter specific lines
- Search for useful patterns inside file output
- Combine commands using the pipe operator `|`
- Handle files that contain non-readable or binary data

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 10**.

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```