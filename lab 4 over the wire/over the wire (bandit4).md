Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 4

## 🎯 Objective

The objective of **Bandit Level 4** is to log in to the Bandit server using the password from **Level 3** and find the password for the next level.

In this level, the password is stored in one of several files inside the `inhere` directory.  
The correct file is the only one that contains human-readable text.

---

## 🧠 Level Information

- **Username:** `bandit4`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 3:**

```bash
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

---

### 2. List the Files

After logging in successfully, I used the `ls` command:

```bash
ls
```

The output showed a directory named:

```bash
inhere
```

So I moved inside it:

```bash
cd inhere
```

Then I listed the files:

```bash
ls
```

The output showed these files:

```bash
-file00  -file01  -file02  -file03  -file04
-file05  -file06  -file07  -file08  -file09
```

---

### 3. Check File Details

I used the following command to show more details about the files:

```bash
ls -lah
```

This showed the permissions, owners, sizes, and file details.

However, all files looked very similar, so I needed another way to identify the correct file.

---

### 4. Identify the File Type

To know which file contains readable text, I used the `file` command:

```bash
file ./*
```

This command checks the type of each file in the current directory.

From the output, I found that the readable ASCII text file was:

```bash
-file07
```

---

### 5. Read the Correct File

Because the filename starts with `-`, I used `./` before the filename to tell Linux that it is a file in the current directory:

```bash
cat ./-file07
```

This displayed the password for the next level.

---

## 🔑 Password Found

The password for **Bandit Level 5** is:

```bash
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

---

## ✅ What I Learned

In this level, I learned that:

- The `file` command helps identify the type of a file.
- Not all files are human-readable.
- ASCII text files usually contain readable content.
- Filenames that start with `-` can confuse Linux commands.
- Using `./` before a filename tells Linux to treat it as a file path.

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 5**.

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```
