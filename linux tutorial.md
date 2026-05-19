# 🐧 Linux Commands & Bash Scripting — Personal Notes

> **Author:** Youhana Emad  
> **Role:** Junior Penetration Tester  
> **Purpose:** Personal reference notes for Linux fundamentals and Bash scripting

---

## 📌 Introduction

My name is **Youhana Emad**, and I am a **Junior Penetration Tester**.

This file contains my personal notes about essential **Linux commands** and **Bash scripting basics**. These notes are designed to help me understand and practice the most important commands used in Linux environments, especially commands related to:

- 🖥️ System information
- 📁 File management
- 🔐 Permissions
- ⚙️ Processes
- 📦 Package management
- 🖊️ Shell scripting

As a junior pentester, Linux is a very important skill because many cybersecurity tools and penetration testing environments depend on it. This file will help me build a strong foundation in Linux, improve my command-line skills, and prepare for real-world cybersecurity and penetration testing tasks.

---

## 🖥️ System Information Commands

| Command | Description |
|--------|-------------|
| `uname -a` | Display all system information |
| `hostname` | Show the system hostname |
| `uptime` | Show how long the system has been running |
| `whoami` | Print the current logged-in user |
| `id` | Display user ID and group ID |
| `df -h` | Show disk space usage (human-readable) |
| `free -h` | Display memory usage |
| `top` / `htop` | Monitor running processes in real time |
| `lscpu` | Show CPU architecture information |
| `lsblk` | List information about block devices |

---

## 📁 File Management Commands

| Command | Description |
|--------|-------------|
| `ls -la` | List all files including hidden ones with details |
| `pwd` | Print current working directory |
| `cd <dir>` | Change directory |
| `mkdir <dir>` | Create a new directory |
| `rm -rf <dir>` | Remove a directory and its contents recursively |
| `cp <src> <dst>` | Copy files or directories |
| `mv <src> <dst>` | Move or rename files |
| `touch <file>` | Create an empty file |
| `cat <file>` | Display file contents |
| `less <file>` | View file contents page by page |
| `find / -name <file>` | Search for a file by name |
| `locate <file>` | Quickly find a file by name |

---

## 🔐 Permissions

### Understanding Permission Notation

```
-rwxr-xr--
 ↑↑↑↑↑↑↑↑↑
 │└──┘└──┘└──── Others (r--)
 │   │└──────── Group  (r-x)
 │   └────────── Owner  (rwx)
 └────────────── File type (- = file, d = directory)
```

| Command | Description |
|--------|-------------|
| `chmod 755 <file>` | Set permissions using numeric notation |
| `chmod u+x <file>` | Add execute permission for the owner |
| `chown user:group <file>` | Change file owner and group |
| `ls -l` | View file permissions |
| `umask` | Show/set default permission mask |

### Numeric Permission Reference

| Value | Permission |
|-------|-----------|
| `7` | rwx (read, write, execute) |
| `6` | rw- (read, write) |
| `5` | r-x (read, execute) |
| `4` | r-- (read only) |
| `0` | --- (no permissions) |

---

## ⚙️ Process Management

| Command | Description |
|--------|-------------|
| `ps aux` | Show all running processes |
| `kill <PID>` | Terminate a process by PID |
| `kill -9 <PID>` | Force kill a process |
| `pkill <name>` | Kill processes by name |
| `jobs` | List background jobs |
| `bg` | Resume a job in the background |
| `fg` | Bring a job to the foreground |
| `nohup <cmd> &` | Run a command immune to hangups |
| `nice -n <val> <cmd>` | Run a command with a given priority |

---

## 📦 Package Management

### Debian / Ubuntu (APT)

```bash
sudo apt update              # Refresh package lists
sudo apt upgrade             # Upgrade all packages
sudo apt install <package>   # Install a package
sudo apt remove <package>    # Remove a package
sudo apt search <package>    # Search for a package
```

### Red Hat / CentOS (YUM / DNF)

```bash
sudo yum install <package>   # Install a package
sudo dnf update              # Update all packages
sudo rpm -qa                 # List all installed packages
```

---

## 🖊️ Bash Scripting Basics

### Hello World Script

```bash
#!/bin/bash
echo "Hello, World!"
```

### Variables

```bash
#!/bin/bash
name="Youhana"
echo "My name is $name"
```

### Conditional Statements

```bash
#!/bin/bash
if [ $1 -gt 100 ]; then
  echo "Number is greater than 100"
else
  echo "Number is 100 or less"
fi
```

### Loops

```bash
# For loop
for i in {1..5}; do
  echo "Iteration $i"
done

# While loop
count=0
while [ $count -lt 5 ]; do
  echo "Count: $count"
  ((count++))
done
```

### Functions

```bash
#!/bin/bash
greet() {
  echo "Hello, $1!"
}

greet "Youhana"
```

### Reading User Input

```bash
#!/bin/bash
read -p "Enter your name: " name
echo "Welcome, $name!"
```

---

## 🔗 Useful Networking Commands (Pentesting Relevant)

| Command | Description |
|--------|-------------|
| `ifconfig` / `ip a` | Show network interfaces |
| `ping <host>` | Test connectivity to a host |
| `netstat -tuln` | List open ports and listening services |
| `ss -tuln` | Modern replacement for netstat |
| `nmap <target>` | Scan a target for open ports |
| `curl <url>` | Transfer data from a URL |
| `wget <url>` | Download files from the web |
| `traceroute <host>` | Trace the route to a host |
| `dig <domain>` | DNS lookup |
| `whois <domain>` | Query domain registration info |

---

## 📚 Resources

- [Linux Command Line Basics — The Linux Foundation](https://www.linuxfoundation.org)
- [Bash Scripting Guide](https://tldp.org/LDP/Bash-Beginners-Guide/html/)
- [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/) — Practice Linux commands in a CTF setting
- [TryHackMe Linux Fundamentals](https://tryhackme.com)
- [HackTheBox](https://www.hackthebox.com)

---

> 💡 *"The quieter you become, the more you are able to hear."* — Kali Linux motto

---

*Last updated: 2026 | Youhana Emad — Junior Penetration Tester*