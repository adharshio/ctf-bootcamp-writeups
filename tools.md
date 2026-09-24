---

layout: default
title: Helpful Tools & Platforms
permalink: /tools/
---


# 🛠️ Helpful Tools & Platforms

New to CTFs? You don't need to know hundreds of tools.

Here are some beginner-friendly tools and platforms that can help you understand and solve CTF challenges.

---

## 🧩 CyberChef

**Best for:** Encoding, decoding, cryptography, and data manipulation.

CyberChef is a web-based tool that lets you perform different operations on data.

You can use it for:

* Base64 encoding/decoding
* Hexadecimal conversions
* URL encoding/decoding
* XOR
* Hash-related operations
* Text transformations

**Website:** [CyberChef](https://gchq.github.io/CyberChef/)

---

## 🐧 Linux Terminal

**Best for:** File analysis, navigating systems, and solving a wide variety of CTF challenges.

The Linux terminal is one of the most useful skills you can develop for CTFs.

### Commands to learn

```bash
ls
cd
pwd
cat
less
grep
find
file
strings
head
tail
chmod
```

### Useful examples

```bash
file mystery
```

Identify what type of file you are dealing with.

```bash
strings mystery
```

Look for readable text inside a file.

```bash
grep "flag" file.txt
```

Search for the word `flag` inside a file.

```bash
find . -type f
```

Find files in the current directory and its subdirectories.

### Tip

You don't need to memorize every Linux command.

Learn what a command does and use the built-in documentation when you need help:

```bash
man grep
```

or

```bash
grep --help
```

---

## 🔎 Nmap

**Best for:** Network and service discovery.

Nmap is used to discover hosts, open ports, and services running on a network.

### Basic example

```bash
nmap <target>
```

You might see something like:

```text
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
```

This tells you that SSH and HTTP services are available.

### Tip

In a CTF, start by understanding what services are exposed before trying to interact with them.

**Website:** [Nmap](https://nmap.org/)

---

## 🦈 Wireshark

**Best for:** Network forensics.

Wireshark allows you to inspect network traffic captured in files such as `.pcap` and `.pcapng`.

It can help you identify:

* HTTP requests
* DNS queries
* IP addresses
* Network protocols
* Suspicious traffic
* Data transferred over the network

### Useful filters

```text
http
```

Show HTTP traffic.

```text
dns
```

Show DNS traffic.

```text
tcp
```

Show TCP traffic.

```text
ip.addr == 192.168.1.10
```

Show traffic involving a specific IP address.

### Tip

Don't try to understand every packet.

First identify the protocols and conversations that look interesting.

**Website:** [Wireshark](https://www.wireshark.org/)

---

## 🌐 Burp Suite

**Best for:** Web security challenges.

Burp Suite allows you to inspect and modify HTTP requests between your browser and a web application.

It is useful for understanding:

* HTTP requests and responses
* Cookies
* Parameters
* Headers
* Forms
* Sessions

For beginners, start by understanding what an HTTP request and response actually look like.

**Website:** [Burp Suite](https://portswigger.net/burp)

---

## 🖼️ ExifTool

**Best for:** Metadata and file analysis.

Files can contain metadata that isn't immediately visible.

For example:

```bash
exiftool image.jpg
```

You may find information such as:

* Camera information
* Timestamps
* Software information
* GPS information
* Author information

ExifTool can be especially useful for **OSINT and forensics** challenges.

**Website:** [ExifTool](https://exiftool.org/)

---

## 🔤 Strings

**Best for:** Finding readable text inside files and binaries.

Sometimes useful information is simply stored inside a file.

Try:

```bash
strings file
```

You can also combine it with `grep`:

```bash
strings file | grep -i flag
```

This is often worth trying before using more complicated tools.

---

## 📦 Binwalk

**Best for:** Finding embedded data inside files.

Binwalk can help identify files and other data embedded inside another file.

For example:

```bash
binwalk suspicious_file
```

It can be useful in certain **forensics and steganography** challenges.

**GitHub:** [Binwalk](https://github.com/ReFirmLabs/binwalk)

---

# 🎮 Platforms to Practice

Tools are useful, but the best way to learn CTFs is to actually solve challenges.

Here are some platforms that are good starting points.

---

## 🟢 TryHackMe

**Good for:** Complete beginners.

TryHackMe provides guided rooms where you learn a concept and then practice it through challenges.

It covers areas such as:

* Linux
* Networking
* Web security
* Cryptography
* Forensics
* Cybersecurity fundamentals

**Website:** [TryHackMe](https://tryhackme.com/)

---

## 🟣 picoCTF

**Good for:** CTF-style challenges.

picoCTF is designed around learning cybersecurity through CTF challenges.

Challenges cover areas such as:

* General Skills
* Cryptography
* Web
* Forensics
* Reverse Engineering
* Binary Exploitation

**Website:** [picoCTF](https://picoctf.org/)

---

## 🐧 OverTheWire

**Good for:** Linux and command-line fundamentals.

If you're completely new to the Linux terminal, start with **Bandit**.

Bandit gradually introduces commands and concepts that are extremely useful when solving CTF challenges.

**Website:** [OverTheWire](https://overthewire.org/wargames/)

---

## 🔴 Root Me

**Good for:** Practicing different CTF categories.

Root Me contains challenges covering:

* Web
* Network
* Cryptography
* Forensics
* Reverse Engineering
* Programming

**Website:** [Root Me](https://www.root-me.org/)

---

## 🌐 PortSwigger Web Security Academy

**Good for:** Learning web security.

PortSwigger's Web Security Academy provides interactive labs for learning about web vulnerabilities.

It's particularly useful if you become interested in web-based CTF challenges.

**Website:** [Web Security Academy](https://portswigger.net/web-security)

---

## 🏆 CTFtime

**Good for:** Finding CTF competitions.

Once you are comfortable with the basics, CTFtime can help you find upcoming competitions and explore previous CTF events.

**Website:** [CTFtime](https://ctftime.org/)

---

# 🚀 Where Should I Start?

If you're completely new, **don't try to learn everything at once.**

A simple progression is:

```text
Linux Basics
     ↓
CyberChef
     ↓
Basic File Analysis
     ↓
Wireshark
     ↓
Nmap
     ↓
Burp Suite
     ↓
Solve CTF Challenges
```

### 🟢 Absolute Beginner

Start with:

* OverTheWire Bandit
* TryHackMe

### 🟣 CTF Practice

Try:

* picoCTF
* Root Me

### 🌐 Interested in Web Security?

Try:

* PortSwigger Web Security Academy

### 🏆 Want to Participate in Competitions?

Check:

* CTFtime

---

