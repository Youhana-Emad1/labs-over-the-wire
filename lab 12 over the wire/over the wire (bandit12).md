# 🧪 OverTheWire Bandit Level 12 — Hexdump & Multiple Compression Challenge 🔐

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&duration=3000&pause=800&center=true&vCenter=true&width=800&lines=OverTheWire+Bandit+Labs;Level+12+Writeup;Hexdump+%2B+Compression+%2B+Linux+Commands;By+Youhana+Emad" alt="Typing Animation" />
</p>

---

## 👋 Introduction

Hello everybody, I'm **Youhana Emad**, a **Junior Penetration Tester**.

This repository documents my learning journey through the **OverTheWire Bandit** wargame.  
The purpose of this write-up is to explain each level step by step, document the commands I used, and improve my Linux, terminal, and cybersecurity skills through practical hands-on practice.

---

## 🎯 Objective

The objective of **Bandit Level 12** is to log in to the Bandit server using the password from **Level 11** and find the password for the next level.

In this level, the password is stored in the file:

```bash
data.txt
```

But this file is not readable directly because it is a **hexdump** of a file that has been compressed many times.

So, to solve this level, I needed to:

- 🧩 Create a temporary working directory
- 📁 Copy the original file
- 🔄 Reverse the hexdump
- 🔍 Identify the file type
- 📦 Decompress the file many times
- 🔑 Extract the final password

---

## 🧠 Level Information

| Item | Value |
|---|---|
| 👤 Username | `bandit12` |
| 🌐 Host | `bandit.labs.overthewire.org` |
| 🚪 Port | `2220` |
| 🔐 Password from Level 11 | `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4` |

---

## 🚀 Step 1: Connect to the Bandit Server

First, I connected to the server using SSH:

```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

When the server asked for the password, I entered:

```bash
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

✅ Now I am logged in as `bandit12`.

---

## 📌 Step 2: Understand the Challenge

The challenge says:

> The password for the next level is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed.

This means the file went through multiple steps:

```text
Original File ➜ Compressed ➜ Compressed Again ➜ Compressed Again ➜ Hexdump
```

So I needed to reverse everything step by step.

---

## 🧰 Tools Used in This Level

| Tool | Purpose |
|---|---|
| `mktemp -d` | Create a temporary working directory |
| `cp` | Copy files |
| `xxd -r` | Reverse a hexdump |
| `file` | Identify file type |
| `mv` | Rename files |
| `gzip -d` | Decompress gzip files |
| `bzip2 -d` | Decompress bzip2 files |
| `tar -xf` | Extract tar archives |
| `cat` | Read the final password |

---

## 🛠️ Step 3: Create a Temporary Directory

I created a temporary directory using:

```bash
mktemp -d
```

This command gave me a new temporary path like:

```bash
/tmp/tmp.XYZ123
```

Then I moved into it:

```bash
cd /tmp/tmp.XYZ123
```

> ⚠️ I worked inside `/tmp` because I did not want to modify the original `data.txt` file.

---

## 📁 Step 4: Copy the Original File

I copied the original `data.txt` file into my temporary directory:

```bash
cp ~/data.txt .
```

Now I can work safely on the copied file.

---

## 🔄 Step 5: Reverse the Hexdump

Since `data.txt` is a hexdump, I reversed it using:

```bash
xxd -r data.txt > data
```

Then I checked the file type:

```bash
file data
```

The output showed that the file was compressed.

---

## 📦 Step 6: Start Decompressing the File

### 🟢 First Compression — gzip

The file was gzip compressed, so I renamed it:

```bash
mv data data.gz
```

Then I decompressed it:

```bash
gzip -d data.gz
```

After that, I checked the file type again:

```bash
file data
```

---

### 🔵 Second Compression — bzip2

The file was bzip2 compressed, so I renamed it:

```bash
mv data data.bz2
```

Then I decompressed it:

```bash
bzip2 -d data.bz2
```

Then I checked the file type:

```bash
file data
```

---

### 🟢 Third Compression — gzip Again

The file was compressed again using gzip:

```bash
mv data data.gz
gzip -d data.gz
file data
```

---

### 📦 Fourth Step — tar Archive

The file became a tar archive, so I renamed it:

```bash
mv data data.tar
```

Then I extracted it:

```bash
tar -xf data.tar
```

Then I listed the files:

```bash
ls
```

I found:

```bash
data5.bin
```

---

## 🔁 Step 7: Continue Extracting and Decompressing

I checked the file type:

```bash
file data5.bin
```

Then I extracted it:

```bash
tar -xf data5.bin
```

This gave me another file:

```bash
data6.bin
```

Then I checked it:

```bash
file data6.bin
```

---

### 🔵 Decompress `data6.bin`

The file was bzip2 compressed, so I renamed it:

```bash
mv data6.bin data6.bz2
```

Then I decompressed it:

```bash
bzip2 -d data6.bz2
```

Then I checked it:

```bash
file data6
```

---

### 📦 Extract Another tar Archive

The file became another tar archive:

```bash
mv data6 data6.tar
```

Then I extracted it:

```bash
tar -xf data6.tar
```

This gave me:

```bash
data8.bin
```

---

### 🟢 Final gzip Decompression

I checked the file type:

```bash
file data8.bin
```

It was gzip compressed, so I renamed it:

```bash
mv data8.bin data8.gz
```

Then I decompressed it:

```bash
gzip -d data8.gz
```

Finally, I checked it:

```bash
file data8
```

Now the file became readable text.

---

## 🔑 Step 8: Read the Final Password

I used `cat` to read the final file:

```bash
cat data8
```

And I got the password.

---

## 🧾 Bash Script Used

To make the process easier and avoid repeating commands manually, I wrote a Bash script.

First, I created the script:

```bash
nano file.sh
```

Then I wrote:

```bash
#!/bin/bash

echo "🚀 Creating temporary directory..."
WORKDIR=$(mktemp -d)
cd "$WORKDIR" || exit

echo "📁 Copying original data.txt..."
cp ~/data.txt .

echo "🔄 Reversing hexdump..."
xxd -r data.txt > data
file data

echo "📦 Decompressing gzip..."
mv data data.gz
gzip -d data.gz
file data

echo "📦 Decompressing bzip2..."
mv data data.bz2
bzip2 -d data.bz2
file data

echo "📦 Decompressing gzip again..."
mv data data.gz
gzip -d data.gz
file data

echo "📦 Extracting tar archive..."
mv data data.tar
tar -xf data.tar
ls
file data5.bin

echo "📦 Extracting data5.bin..."
tar -xf data5.bin
ls
file data6.bin

echo "📦 Decompressing data6.bin using bzip2..."
mv data6.bin data6.bz2
bzip2 -d data6.bz2
file data6

echo "📦 Extracting data6 tar archive..."
mv data6 data6.tar
tar -xf data6.tar
ls
file data8.bin

echo "📦 Final gzip decompression..."
mv data8.bin data8.gz
gzip -d data8.gz
file data8

echo "🔑 Final password:"
cat data8
```

To save the file in `nano`:

```bash
CTRL + O
Enter
CTRL + X
```

Then I ran the script:

```bash
bash file.sh
```

---

## 🔐 Password Found

The password for **Bandit Level 13** is:

```bash
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

---

## ✅ What I Learned

In this level, I learned how to:

- 🧪 Work safely inside a temporary directory
- 📁 Copy files using `cp`
- 🔄 Reverse a hexdump using `xxd -r`
- 🔍 Identify file types using `file`
- 📦 Decompress gzip files using `gzip -d`
- 📦 Decompress bzip2 files using `bzip2 -d`
- 📦 Extract tar archives using `tar -xf`
- 🧾 Write and run a Bash script
- 🧠 Solve a multi-step Linux challenge

---

## 🧠 Important Notes

This level is not about encryption.  
It is mainly about **encoding**, **hexdump reversing**, and **file decompression**.

The most important command in this level is:

```bash
file filename
```

Because it tells us what type of file we are dealing with before choosing the next command.

---

## 🚀 Next Level

The password found in this level will be used to log in to **Bandit Level 13**.

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

---

<p align="center">
  <b>✅ Bandit Level 12 Completed Successfully!</b>
</p>

<p align="center">
  🧪 🔄 📦 🔑 🚀
</p>