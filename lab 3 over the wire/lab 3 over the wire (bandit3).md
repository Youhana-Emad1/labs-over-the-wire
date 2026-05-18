Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 3

## 🎯 Objective

The objective of **Bandit Level 3** is to log in to the Bandit server using the password from **Level 2** and find the password for the next level.

In this level, the password is stored in a hidden file inside a directory called `inhere`.

---

## 🧠 Level Information

- **Username:** `bandit3`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 2:**

```bash
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

---

### 2. List the Files

After logging in successfully, I used the `ls` command to list the files in the current directory:

```bash
ls
```

The output showed a directory named:

```bash
inhere
```

---

### 3. Move Inside the Directory

I used the `cd` command to enter the `inhere` directory:

```bash
cd inhere
```

Then I used `ls` to list the files:

```bash
ls
```

At first, no files appeared.

---

### 4. Show Hidden Files

Since no files appeared with the normal `ls` command, I used `ls -lah` to show all files, including hidden files:

```bash
ls -lah
```

The output showed a hidden file named:

```bash
...Hiding-From-You
```

---

### 5. Try to Rename the Hidden File

I tried to rename the file to make it easier to read:

```bash
mv ...Hiding-From-You Hiding-From-You
```

However, this failed because I did not have permission to rename the file.

---

### 6. Read the Hidden File

Instead of renaming the file, I read it directly using the `cat` command:

```bash
cat ...Hiding-From-You
```

This displayed the password for the next level.

---

## 🔑 Password Found

The password for **Bandit Level 4** is:

```bash
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

---

## ✅ What I Learned

In this level, I learned that:

- Hidden files in Linux usually start with a dot `.`.
- The normal `ls` command does not show hidden files.
- The `ls -lah` command shows hidden files and detailed file information.
- I may not always have permission to rename files.
- I can read hidden files directly if I know their exact name.

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 4**.

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```