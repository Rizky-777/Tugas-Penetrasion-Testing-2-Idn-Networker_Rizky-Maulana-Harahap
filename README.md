# Bandit Wargame Solutions - OverTheWire

![Bandit](https://img.shields.io/badge/OverTheWire-Bandit-yellow)
![Levels](https://img.shields.io/badge/Levels-0--33-brightgreen)
![Linux](https://img.shields.io/badge/Linux-CLI-blue)

Complete write-up and step-by-step solutions for the OverTheWire: Bandit Wargame challenges (Level 0 - 33) to practice Linux CLI and cybersecurity skills.

## 📋 Table of Contents

- [About Bandit Wargame](#about-bandit-wargame)
- [Solutions Overview](#solutions-overview)
- [Commands Learned](#commands-learned)
- [How to Use This Repository](#how-to-use-this-repository)
- [Prerequisites](#prerequisites)
- [Contributing](#contributing)
- [Acknowledgments](#acknowledgments)

## 🎯 About Bandit Wargame

Bandit is a beginner-friendly wargame hosted by [OverTheWire](https://overthewire.org/wargames/bandit/) designed to teach the basics of Linux command-line interface and security concepts. Each level presents a unique challenge that requires using various Linux commands and security techniques to find the password for the next level.

The wargame consists of 34 levels (0-33) that progressively increase in difficulty, covering topics such as:
- Basic Linux navigation and file manipulation
- File permissions and hidden files
- Text processing and pattern matching
- Network protocols and secure shell
- Process management and scheduling
- Data encoding and compression
- Basic scripting and automation

## 📚 Solutions Overview

This repository contains detailed write-ups for each level of the Bandit Wargame, including:
- Problem description
- Step-by-step solution
- Commands used
- Explanations of concepts
- Tips and tricks

Each level builds upon knowledge from previous levels, creating a comprehensive learning path for Linux CLI mastery.

## 🛠️ Commands Learned

Throughout the Bandit Wargame challenges, you'll learn and master numerous Linux commands. Here are the key commands covered:

### **ssh (Secure Shell)**
- **Usage**: Connect securely to remote servers
- **Bandit Application**: Used to connect to the Bandit game servers at `bandit.labs.overthewire.org`
- **Example**: `ssh bandit0@bandit.labs.overthewire.org -p 2220`
- **What I Learned**: How to establish secure remote connections, use custom ports, and manage SSH sessions

### **ls (List)**
- **Usage**: List directory contents
- **Bandit Application**: View files in directories, including hidden files with `-a` flag
- **Example**: `ls -la` to show all files with detailed information
- **What I Learned**: Different listing options, file permissions interpretation, and finding hidden files

### **cd (Change Directory)**
- **Usage**: Navigate between directories
- **Bandit Application**: Move through the file system to locate password files
- **Example**: `cd /home/bandit1` or `cd ..` to move up one level
- **What I Learned**: Absolute vs relative paths, special directories (`.`, `..`, `~`)

### **cat (Concatenate)**
- **Usage**: Display file contents
- **Bandit Application**: Read password files
- **Example**: `cat readme` or `cat ./filename`
- **What I Learned**: How to read files, handle special characters in filenames

### **find**
- **Usage**: Search for files and directories
- **Bandit Application**: Locate files by name, size, permissions, or owner
- **Example**: `find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`
- **What I Learned**: Complex search criteria, filtering by attributes, redirecting errors

### **grep**
- **Usage**: Search text patterns in files
- **Bandit Application**: Find specific strings within large files
- **Example**: `grep "millionth" data.txt`
- **What I Learned**: Pattern matching, regular expressions, case-insensitive searches with `-i`

### **file**
- **Usage**: Determine file type
- **Bandit Application**: Identify file types regardless of extension
- **Example**: `file data.txt`
- **What I Learned**: How Linux determines file types by content, not just extensions

### **strings**
- **Usage**: Extract readable text from binary files
- **Bandit Application**: Find human-readable strings in non-text files
- **Example**: `strings data.txt`
- **What I Learned**: Working with binary files, extracting useful information

### **base64**
- **Usage**: Encode/decode base64 data
- **Bandit Application**: Decode encoded passwords
- **Example**: `base64 -d data.txt`
- **What I Learned**: Understanding base64 encoding, decoding data

### **tr (Translate)**
- **Usage**: Translate or delete characters
- **Bandit Application**: ROT13 cipher decoding, character substitution
- **Example**: `cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`
- **What I Learned**: Character translation, simple ciphers, stream processing

### **tar**
- **Usage**: Archive and compress files
- **Bandit Application**: Extract compressed archives
- **Example**: `tar -xvf archive.tar`
- **What I Learned**: Archive management, compression formats (gzip, bzip2)

### **gzip/gunzip, bzip2/bunzip2**
- **Usage**: Compress and decompress files
- **Bandit Application**: Decompress nested compressed files
- **Example**: `gunzip file.gz` or `bzip2 -d file.bz2`
- **What I Learned**: Different compression algorithms, decompression techniques

### **xxd**
- **Usage**: Create hex dump or reverse it
- **Bandit Application**: View binary files in hexadecimal format, reverse hex dumps
- **Example**: `xxd data.txt` or `xxd -r hexdump`
- **What I Learned**: Hexadecimal representation, binary data manipulation

### **sort**
- **Usage**: Sort lines of text
- **Bandit Application**: Organize data before processing
- **Example**: `sort data.txt`
- **What I Learned**: Sorting algorithms, unique sorting with `sort -u`

### **uniq**
- **Usage**: Filter out repeated lines
- **Bandit Application**: Find unique or duplicate entries
- **Example**: `sort data.txt | uniq -u` (show only unique lines)
- **What I Learned**: Removing duplicates, counting occurrences with `-c`

### **diff**
- **Usage**: Compare files line by line
- **Bandit Application**: Find differences between similar files
- **Example**: `diff file1 file2`
- **What I Learned**: File comparison, identifying changes

### **nc (netcat)**
- **Usage**: Network connections and port scanning
- **Bandit Application**: Connect to services on specific ports
- **Example**: `nc localhost 30000`
- **What I Learned**: Network communication, reading from network services

### **openssl**
- **Usage**: SSL/TLS toolkit for cryptographic operations
- **Bandit Application**: Connect to SSL services
- **Example**: `openssl s_client -connect localhost:30001`
- **What I Learned**: Secure connections, SSL/TLS protocols

### **nmap**
- **Usage**: Network exploration and security auditing
- **Bandit Application**: Scan for open ports
- **Example**: `nmap -p 31000-32000 localhost`
- **What I Learned**: Port scanning, service discovery

### **cron/crontab**
- **Usage**: Schedule recurring tasks
- **Bandit Application**: Understanding scheduled scripts and automation
- **Example**: `crontab -l` to list scheduled jobs
- **What I Learned**: Cron syntax, task scheduling, automated execution

### **git**
- **Usage**: Version control system
- **Bandit Application**: Navigate git repositories, view commit history
- **Example**: `git log`, `git show`, `git branch`
- **What I Learned**: Version control basics, commit history navigation, branch management

### **chmod**
- **Usage**: Change file permissions
- **Bandit Application**: Modify file access rights
- **Example**: `chmod 600 file.txt`
- **What I Learned**: Linux permission system (read, write, execute), octal notation

### **mkdir**
- **Usage**: Create directories
- **Bandit Application**: Create temporary working directories
- **Example**: `mkdir /tmp/myworkdir`
- **What I Learned**: Directory creation, working with temporary directories

### **mv/cp**
- **Usage**: Move/copy files and directories
- **Bandit Application**: Manipulate files for analysis
- **Example**: `cp file.txt /tmp/backup.txt`
- **What I Learned**: File operations, backup strategies

### **Pipes (|) and Redirection (>, >>, <)**
- **Usage**: Chain commands and redirect input/output
- **Bandit Application**: Combine multiple commands for complex operations
- **Example**: `cat file.txt | grep "password" | sort | uniq`
- **What I Learned**: Command chaining, stream redirection, powerful command combinations

### **man**
- **Usage**: Display manual pages
- **Bandit Application**: Learn about commands and their options
- **Example**: `man find`
- **What I Learned**: Self-learning, reading documentation, finding command options

## 💻 How to Use This Repository

1. **Start with Level 0**: Begin at the first level and work your way up
2. **Try It Yourself First**: Attempt each challenge before looking at the solution
3. **Read the Write-ups**: Use the solutions as learning resources
4. **Practice the Commands**: Experiment with the commands in your own Linux environment
5. **Take Notes**: Document your own insights and learning points

## 📋 Prerequisites

To follow along with these solutions, you should have:
- Basic understanding of computer systems
- Access to a terminal/command line
- SSH client installed (usually pre-installed on Linux/Mac, available in Windows 10+ via PowerShell/Terminal, or use PuTTY)
- Enthusiasm to learn!

## 🤝 Contributing

While these are personal solutions to the Bandit Wargame, suggestions for improvements are welcome! Please:
- Don't post complete passwords in public issues
- Suggest alternative solutions or approaches
- Report any errors or outdated information

## 🙏 Acknowledgments

- **OverTheWire Community**: For creating and maintaining the Bandit Wargame
- **Linux Community**: For extensive documentation and resources
- **Security Researchers**: Who contribute to cybersecurity education

---

**Note**: This repository is for educational purposes. Please respect the OverTheWire community guidelines and don't share passwords publicly.

**Happy Hacking! 🚀**
