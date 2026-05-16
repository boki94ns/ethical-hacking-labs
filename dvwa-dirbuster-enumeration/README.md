# DVWA DirBuster Enumeration Lab

## Overview

This lab demonstrates basic web application enumeration using OWASP DirBuster against the DVWA (Damn Vulnerable Web Application) environment running inside a Docker container on Kali Linux.

The objective of the lab was to identify accessible directories and PHP files through brute-force directory enumeration techniques commonly used during penetration testing and web application reconnaissance.

---

# Environment

- Operating System: Kali Linux
- Virtualization: Oracle VirtualBox
- Target Application: DVWA
- Deployment Method: Docker
- Enumeration Tool: OWASP DirBuster

---

# Target Setup

DVWA container was started using Docker with the following command:

```bash
sudo docker run --rm -it -p 8080:80 vulnerables/web-dvwa
```

The application was accessible locally at:

```text
http://127.0.0.1:8080
```

---

# Enumeration Configuration

The following configuration was used in OWASP DirBuster:

- Target URL:
  ```text
  http://127.0.0.1:8080
  ```

- Wordlist:
  ```text
  /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt
  ```

- Recursive scanning enabled
- PHP extension enumeration enabled
- 10 scanning threads used

---

# Enumeration Process

DirBuster performed recursive directory and file brute-force enumeration against the DVWA application.

The scan identified multiple accessible resources, including:

- `/login.php`
- `/setup.php`
- `/security.php`
- `/config/`
- `/docs/`
- `/external/`
- `/vulnerabilities/`

HTTP response codes such as `200`, `302`, and `403` were observed during enumeration.

---

# Findings

The enumeration process successfully revealed:

- accessible PHP application endpoints,
- configuration-related directories,
- documentation directories,
- vulnerability-related paths inside the DVWA application.

This demonstrates how directory enumeration can expose hidden or sensitive application resources during web reconnaissance activities.

---

# Screenshots

## DirBuster Startup

## Target Configuration

## Enumeration Process

## Results Tree View

## DVWA Target Application

---

# Skills Practiced

- Web Application Enumeration
- Directory Bruteforcing
- Docker-based Lab Setup
- Basic Web Reconnaissance
- Kali Linux Tool Usage
- HTTP Response Analysis

---

# Conclusion

This lab provided hands-on experience with web application reconnaissance and directory enumeration techniques using OWASP DirBuster in a controlled DVWA environment.

The exercise demonstrates how publicly accessible resources and hidden directories can be identified during the reconnaissance phase of penetration testing.
