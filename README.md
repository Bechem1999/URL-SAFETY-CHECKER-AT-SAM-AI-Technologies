# 🔐 URL Safety Checker

<p align="center">

<img src="https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white" alt="Python">

<img src="https://img.shields.io/badge/Platform-Kali%20Linux-557C94?logo=kalilinux&logoColor=white" alt="Kali Linux">

<img src="https://img.shields.io/badge/Category-Cybersecurity-red" alt="Cybersecurity">

<img src="https://img.shields.io/badge/Project-URL%20Analysis-orange" alt="URL Analysis">

<img src="https://img.shields.io/badge/Status-Completed-success" alt="Project Status">

</p>

## 📌 Project Overview

**URL Safety Checker** is a Python-based cybersecurity tool designed to perform basic static analysis of URLs and identify common indicators associated with suspicious or potentially phishing-related links.

The tool accepts a URL as input and performs several checks, including URL format validation, HTTPS verification, suspicious keyword detection, IP-address detection, URL-length analysis, and detection of the `@` symbol.

A simple risk-scoring mechanism is then used to classify the URL as either **SAFE**, **SUSPICIOUS**, or **INVALID**.

> **Important:** This project is an educational security-analysis tool. A URL classified as SAFE is not guaranteed to be legitimate or free from malicious content.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* Develop a Python-based URL analysis tool.
* Validate URL formats.
* Determine whether a URL uses HTTPS.
* Identify suspicious keywords commonly associated with phishing.
* Detect URLs using IP addresses instead of domain names.
* Identify unusually long URLs.
* Detect potentially misleading `@` characters.
* Implement a basic risk-scoring system.
* Practice cybersecurity automation using Python.
* Demonstrate practical security analysis skills on Kali Linux.

---

## 🛠️ Technologies Used

| Technology     | Purpose                             |
| -------------- | ----------------------------------- |
| Python 3       | Programming language                |
| Kali Linux     | Security testing environment        |
| `urllib.parse` | URL parsing                         |
| `re`           | Pattern matching and IP detection   |
| Git            | Version control                     |
| GitHub         | Project documentation and portfolio |

---

## 🔎 Security Checks Performed

### 1. URL Format Validation

The tool verifies that the supplied URL contains:

* A supported protocol
* A valid network location
* A recognizable URL structure

Supported protocols:

```text
http://
https://
```

---

### 2. HTTPS Detection

The tool checks whether the URL uses HTTPS.

Example:

```text
https://example.com
```

HTTPS is a positive security indicator because it provides encrypted communication between the client and server.

However:

> HTTPS alone does not prove that a website is trustworthy.

Phishing websites can also use HTTPS.

---

### 3. Suspicious Keyword Detection

The tool searches the URL for potentially suspicious terms such as:

```text
login
verify
password
account
bank
confirm
credential
wallet
urgent
bonus
claim
```

These keywords are treated as indicators rather than proof of malicious activity.

---

### 4. IP Address Detection

The tool checks whether the hostname is an IPv4 address.

Example:

```text
http://192.168.1.10/login
```

Using an IP address does not automatically make a URL malicious, but it can be a useful indicator during basic URL analysis.

---

### 5. URL Length Analysis

URLs exceeding a defined length threshold are flagged.

Very long URLs can sometimes be associated with:

* Obfuscation
* Tracking parameters
* Redirect chains
* Phishing links

---

### 6. `@` Symbol Detection

The tool checks for the `@` symbol because specially crafted URLs can use it to make a destination appear misleading.

Example:

```text
https://example.com@malicious-site.com
```

The actual hostname in this example is different from what a casual reader might initially assume.

---

# ⚙️ Methodology

The URL analysis process follows these stages:

```text
                USER INPUT
                    │
                    ▼
             URL VALIDATION
                    │
             ┌──────┴──────┐
             │             │
           INVALID        VALID
             │             │
             ▼             ▼
          STOP        HTTPS CHECK
                           │
                           ▼
                  KEYWORD ANALYSIS
                           │
                           ▼
                   IP ADDRESS CHECK
                           │
                           ▼
                    LENGTH CHECK
                           │
                           ▼
                    @ SYMBOL CHECK
                           │
                           ▼
                     RISK SCORING
                           │
                           ▼
                 FINAL CLASSIFICATION
                    /             \
                   /               \
                SAFE           SUSPICIOUS
```

---

# 🧪 Testing

The tool was tested using different URL conditions.

| Test Case           | Input                              | Expected Result |
| ------------------- | ---------------------------------- | --------------- |
| Valid HTTPS         | `https://example.com`              | SAFE            |
| HTTP URL            | `http://example.com`               | Warning         |
| IP address          | `http://192.168.1.10/login`        | SUSPICIOUS      |
| Suspicious keywords | `https://example.com/login/verify` | Warning         |
| Invalid input       | `hello`                            | INVALID         |
| `@` character       | `https://example.com@site.com`     | Warning         |
| Long URL            | URL > 100 characters               | Warning         |

---

# 📸 Screenshots

## Safe URL Analysis

![Safe URL Result](screenshots/safe-url.png)

---

<img width="767" height="607" alt="URL SAFE" src="https://github.com/user-attachments/assets/79322585-4eb9-4349-9e45-b9d41272c592" />

## Suspicious URL Analysis

![Suspicious URL Result](screenshots/suspicious-url.png)

---
<img width="676" height="371" alt="testing a suspicious URL" src="https://github.com/user-attachments/assets/cbd19c9c-b15e-4632-b196-ff65fd7ccdcc" />


## Invalid URL Detection

![Invalid URL Result](screenshots/invalid-url.png)

---

Move into the project:

```bash
cd URL-Safety-Checker
```

Run the tool:

```bash
python3 url_safety_checker.py
```

Enter a URL when prompted:

```text
Enter URL: https://example.com

---

## 🧠Lesson Learned

This project provided practical experience in several areas of cybersecurity and Python development.

### Python Programming

I strengthened my understanding of:

* Functions
* Lists
* Conditional statements
* Loops
* Exception handling
* Regular expressions
* String manipulation

### Cybersecurity

The project improved my understanding of:

* URL structure
* Phishing indicators
* HTTPS
* Domain analysis
* URL obfuscation
* Basic risk assessment

### Linux

Working in Kali Linux provided additional experience with:

* Terminal-based development
* File management
* Python execution
* Project organization
* Testing and documentation

---

# ⚠️ Challenges Encountered

During development, several challenges had to be considered.

## Challenge 1: HTTPS Does Not Mean Safe

One important lesson was that HTTPS should not be treated as proof that a website is legitimate.

A malicious website can obtain a valid TLS certificate and operate over HTTPS.

### Challenge 2: Suspicious Keywords Can Produce False Positives

Words such as `login`, `account`, or `verify` are commonly used by legitimate websites.

Therefore, keyword detection should be treated as an indicator rather than definitive evidence.

### Challenge 3: Risk Scoring

Different indicators have different levels of importance.

For example, an IP address alone does not necessarily indicate malicious activity.

The scoring system therefore provides a basic risk estimate rather than a definitive security verdict.

### Challenge 4: Safe Testing

Testing potentially malicious URLs directly can introduce unnecessary risk.

For this project, controlled and non-malicious test URLs were used to evaluate the detection logics
---

# 🔐 Security Disclaimer

This project is intended for:

* Educational purposes
* Cybersecurity learning
* Defensive security analysis
* Authorized security testing

Do not use the tool to access, test, or interact with systems or websites without appropriate authorization.

The result produced by this tool is an indicator-based assessment and should not be considered a definitive determination that a URL is malicious or safe.

#👨‍💻 Author

ATEMLEFAC NKAFU BECHEM

Cybersecurity Engineer

Cybersecurity #Python #URL safety checker #Cryptography #KaliLinux #EthicalHacking #CyberSecurityInternship #SAMAITechnologies
