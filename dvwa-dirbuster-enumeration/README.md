# DVWA DirBuster Enumeration Lab

## Overview

This lab demonstrates basic web application enumeration using OWASP DirBuster against the DVWA (Damn Vulnerable Web Application) environment running locally on Kali Linux inside a Docker container.

The objective of the lab was to identify accessible directories and PHP files through brute-force directory enumeration techniques commonly used during penetration testing and web reconnaissance.

---

# Lab Steps

## 1. Starting DVWA Container

The DVWA application was started inside a Docker container on Kali Linux using the following command:

```bash
sudo docker run --rm -it -p 8080:80 vulnerables/web-dvwa
```

This exposed the vulnerable web application locally on port 8080.

<img src="./screenshots/1.%20Slika.png" width="900">

---

## 2. Configuring OWASP DirBuster

OWASP DirBuster was launched and configured to target the local DVWA application running on:

```text
http://127.0.0.1:8080
```

The following settings were configured before starting the scan:

- Scan type: List based brute force
- Target URL: http://127.0.0.1:8080
- Wordlist used:
  
```text
/usr/share/dirbuster/wordlists/directory-list-2.3-small.txt
```

- Brute Force Dirs: Enabled
- Brute Force Files: Enabled
- Recursive Scanning: Enabled
- File extension used: php
- Threads: 10

The wordlist was selected manually through the "Browse" option inside OWASP DirBuster.

After configuring the scan options and selecting the wordlist, the enumeration process was started by clicking the "Start" button.

<img src="./screenshots/2.%20Slika.png" width="900">

---

## 3. Starting Directory Enumeration

The directory brute-force process was started against the DVWA target application.

During this phase, DirBuster generated multiple HTTP requests in order to identify hidden directories and files.

<img src="./screenshots/3.%20Slika%20(pocetak%20procesa).png" width="900">

---

## 4. Enumeration Results

The scan successfully identified multiple accessible directories and PHP files within the DVWA application.

Examples of discovered resources:

- `/login.php`
- `/setup.php`
- `/config`
- `/docs`
- `/vulnerabilities`

The enumeration process also revealed HTTP response codes and response sizes useful for web application reconnaissance.

<img src="./screenshots/4.%20Slika%20(Results%20tree%20view).png" width="900">

---

## 5. Target Web Application

The target application used during the lab was DVWA running locally inside a Docker container.

<img src="./screenshots/Target%20page.png" width="900">

---

# Tools Used

- Kali Linux
- Docker
- DVWA (Damn Vulnerable Web Application)
- OWASP DirBuster

---

# Skills Practiced

- Web application reconnaissance
- Directory enumeration
- File enumeration
- Basic penetration testing methodology
- Usage of OWASP DirBuster
- Local lab environment configuration

---

# Conclusion

This lab demonstrated how directory enumeration tools such as OWASP DirBuster can be used to identify accessible resources within a web application.

The exercise provided practical experience with reconnaissance techniques frequently used during penetration testing and ethical hacking assessments.
