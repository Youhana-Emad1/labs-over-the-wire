Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---
# Bandit Level 8

## 🎯 Objective

The objective of **Bandit Level 8** is to log in to the Bandit server using the password from **Level 7** and find the password for the next level.

In this level, the password is stored in the file `data.txt`.  
The password is the only line of text that occurs only once.

---

## 🧠 Level Information

- **Username:** `bandit8`
- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Password from Level 7:**

```bash
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

---

## 🛠️ Steps to Find the Password

### 1. Connect to the Bandit Server

First, I connected to the Bandit server using SSH:

```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered the password from the previous level:

```bash
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

---

### 2. Understand the Challenge

The challenge says that the password is stored in `data.txt`.

The password is the only line that appears once in the file.

So, I needed to find the unique line.

---

### 3. First Attempt

First, I tried to use `cat` with `uniq`:

```bash
cat dattttta.txt | uniq
```

This failed because the filename was written incorrectly.

The correct filename is:

```bash
data.txt
```

Also, `uniq` only works correctly when repeated lines are next to each other.

---

### 4. Sort the File

Then I used the `sort` command:

```bash
sort data.txt
```

This command sorted the lines inside the file, but it only arranged the data.

It did not show the unique line by itself.

---

### 5. Find the Unique Line

Finally, I used `sort` with `uniq -u`:

```bash
sort data.txt | uniq -u
```

### Command Explanation

```bash
sort data.txt
```

Sorts the file so repeated lines are placed next to each other.

```bash
uniq -u
```

Prints only the lines that occur once.

So the full command finds the only unique line in the file.

---

## 🔑 Password Found

The password for **Bandit Level 9** is:

```bash
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

---

## ✅ What I Learned

In this level, I learned how to:

- Use `sort` to arrange lines in a file
- Use `uniq` to filter repeated lines
- Use `uniq -u` to print only unique lines
- Combine commands using the pipe operator `|`
- Understand why sorting is important before using `uniq`

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 9**.

```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
```