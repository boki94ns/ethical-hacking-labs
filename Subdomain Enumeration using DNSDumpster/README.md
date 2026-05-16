# Subdomain Enumeration using DNSDumpster

## Objective

The goal of this lab was to perform passive DNS reconnaissance and subdomain enumeration against the target domain ebay.com using DNSDumpster.

---

# Step 1 - Target Identification

The target domain ebay.com was selected for passive DNS reconnaissance.

DNSDumpster was used in order to identify:
- subdomains
- IP addresses
- ASN information
- hosting providers
- TXT records
- exposed technologies

<img src="screenshots/Slika 1.png">

The screenshot above shows the target domain being entered into DNSDumpster before starting the reconnaissance process.

---

# Step 2 - DNS Reconnaissance Overview

After starting the scan, DNSDumpster identified a large amount of publicly available infrastructure information related to the target domain.

<img src="screenshots/Slika 2.png">

## Analysis

### Hosting / Networks

The scan identified multiple hosting providers and networks including:
- eBay infrastructure
- Amazon AWS
- Akamai CDN
- Google Cloud

This suggests that the organization uses distributed cloud and CDN infrastructure.

### Services / Banners

Several technologies and services were identified:
- nginx
- gunicorn
- AkamaiGHost
- awselb/2.0

These technologies indicate:
- web servers
- reverse proxies
- load balancers
- CDN infrastructure

### Geographic Distribution

Infrastructure was distributed across multiple countries including:
- United States
- United Kingdom
- Germany

This indicates globally distributed services and infrastructure.

---

# Step 3 - Subdomain Enumeration

DNSDumpster identified a large number of subdomains associated with ebay.com.

<img src="screenshots/Slika 3.png">

## Analysis of Results

### Host

The Host field represents discovered subdomains.

Examples:
- accounts.ebay.com
- academy.ebay.com
- ads.ebay.com

These may represent:
- authentication systems
- educational portals
- advertising infrastructure

---

### IP Address

The IP field displays the public IP address associated with the subdomain.

IP addresses can reveal:
- hosting locations
- cloud providers
- infrastructure segmentation

---

### ASN

ASN (Autonomous System Number) identifies the network owner responsible for the IP range.

Examples observed:
- AS11643 (eBay)
- AS14618 (Amazon AWS)
- AS20940 (Akamai)

---

### ASN Name

ASN Name identifies the organization owning the network infrastructure.

Examples:
- eBay Inc.
- Amazon.com Inc.
- Akamai Technologies

---

### Open Services

The Open Services field reveals detected technologies and banners.

Examples:
- nginx
- AWS ELB
- AkamaiGHost

This information may help identify:
- web servers
- reverse proxies
- load balancers

---

### RevIP

RevIP indicates how many domains or subdomains are associated with the same IP address.

Higher values may indicate:
- shared hosting
- CDN usage
- load balancing infrastructure

---

# Step 4 - Additional Subdomain Analysis

Additional subdomains related to advertising, testing and internal infrastructure were identified.

<img src="screenshots/Slika 4.png">

## Analysis

Interesting findings included:
- testing environments
- advertising infrastructure
- account-related systems

Example:
- agentflowtesting.ebay.com

The presence of the word "testing" may indicate a development or staging environment.

---

# Step 5 - AI Related Infrastructure

Several AI-related subdomains were identified.

<img src="screenshots/Slika 5.png">

## Analysis

Examples:
- aim-e2e-ai-cd1.ebay.com
- aim-e2e-ai-ef1.ebay.com

These names suggest:
- AI-related services
- internal AI infrastructure
- distributed AI environments

---

# Step 6 - TXT Records Enumeration

TXT records associated with the target domain were identified.

<img src="screenshots/Slika 6.png">

<img src="screenshots/Slika 7.png">

## Analysis

TXT records revealed:
- Stripe verification
- Google verification
- SPF records
- third-party integrations

### SPF Record

SPF records help prevent email spoofing by defining which servers are allowed to send emails on behalf of the domain.

### Verification Records

Verification entries are commonly used for:
- Google services
- Stripe
- MongoDB
- Docker
- DocuSign

---

# Conclusion

The reconnaissance process revealed a large and distributed infrastructure utilizing multiple providers including AWS, Akamai and Google Cloud.

Multiple authentication systems, testing environments, AI-related services and cloud-hosted applications were identified through passive DNS reconnaissance.

This lab demonstrates how publicly available DNS information can provide insight into an organization's external infrastructure and potential attack surface.

---

# Disclaimer

This project was performed for educational purposes only using passive reconnaissance techniques. No intrusive scanning or exploitation was conducted.
