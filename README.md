# 🌐 Web Reconnaissance & Information Gathering

<p align="center">
  <img src="https://img.shields.io/badge/Domain-networkwalks.com-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Focus-Web%20Reconnaissance-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Tools-Kali%20Linux-black?style=for-the-badge&logo=kalilinux" />
  <img src="https://img.shields.io/badge/Project-Cybersecurity-green?style=for-the-badge" />
</p>

<p align="center">
  <b>A Practical Web Reconnaissance and Information Gathering Assessment Using WHOIS, WhatWeb, Nslookup, cURL, WAFW00F and DNSRecon.</b>
</p>

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Project Objectives](#-project-objectives)
- [Target Information](#-target-information)
- [Tools and Technologies](#-tools-and-technologies)
- [Repository Structure](#-repository-structure)
- [Practical Exercises](#-practical-exercises)
  - [01. WHOIS Lookup](#01-whois-lookup)
  - [02. Website Technology Fingerprinting – WhatWeb](#02-website-technology-fingerprinting--whatweb)
  - [03. DNS Investigation – Nslookup](#03-dns-investigation--nslookup)
  - [04. HTTP Header Analysis – cURL](#04-http-header-analysis--curl)
  - [05. Web Application Firewall Detection – WAFW00F](#05-web-application-firewall-detection--wafw00f)
  - [06. DNS Enumeration – DNSRecon](#06-dns-enumeration--dnsrecon)
- [Challenges and Troubleshooting](#-challenges-and-troubleshooting)
- [Key Findings](#-key-findings)
- [Security Recommendations](#-security-recommendations)
- [Lessons Learnt](#-lessons-learnt)
- [Skills Gained](#-skills-gained)
- [Conclusion](#-conclusion)
- [Disclaimer](#-disclaimer)

---

## 📖 Project Overview

Information gathering is one of the fundamental stages of cybersecurity assessments and penetration testing. Before evaluating the security of a web application, it is important to understand its domain registration information, DNS configuration, hosting infrastructure, technologies, HTTP responses, and security mechanisms.

As part of my practical cybersecurity learning journey, I conducted a web reconnaissance exercise focusing on **Networkwalks Academy (`networkwalks.com`)**.

The exercise involved using command-line reconnaissance tools to collect and analyse publicly observable information about the target domain and its web infrastructure.

The assessment focused on six key areas:

1. WHOIS lookup – Gathering domain registration information.
2. WhatWeb – Identifying website technologies and frameworks.
3. Nslookup – Investigating DNS resolution and IP addressing.
4. cURL – Examining HTTP response headers and server information.
5. WAFW00F – Identifying the presence of a Web Application Firewall.
6. DNSRecon – Performing DNS reconnaissance and enumeration.

The practical exercise provided an opportunity to understand how different reconnaissance tools contribute to the information-gathering phase of a cybersecurity assessment.

## 🎯 Project Objectives

The main objectives of this project were to:

- Understand how domain registration information can be retrieved.
- Identify publicly observable website technologies and frameworks.
- Investigate DNS records and domain-to-IP resolution.
- Examine HTTP response headers and server configurations.
- Identify the presence of Web Application Firewalls.
- Understand DNS enumeration techniques.
- Interpret reconnaissance results and identify potential security considerations.
- Develop practical command-line investigation and troubleshooting skills.

## 🎯 Target Information

| Attribute | Observed Information |
|---|---|
| Target Domain | `networkwalks.com` |
| Website Name | Networkwalks Academy |
| Website URL | https://networkwalks.com |
| Resolved IPv4 Address | `192.232.216.135` |
| Registrar | GoDaddy.com, LLC |
| Hosting Nameservers | NS6135.HOSTGATOR.COM / NS6136.HOSTGATOR.COM |
| Web Server | Apache |
| Website Platform | WordPress |
| Detected WAF | ModSecurity (SpiderLabs) |
| DNSSEC | Unsigned |

*Note: These are observations from the supplied command outputs, not independently verified current configurations. Infrastructure and software information can change over time.*

## 🧰 Tools and Technologies

| Tool | Purpose |
|---|---|
| WHOIS | Domain registration and ownership-record investigation |
| WhatWeb | Website technology fingerprinting |
| Nslookup | DNS resolution and IP address investigation |
| cURL | HTTP response and header inspection |
| WAFW00F | Web Application Firewall identification |
| DNSRecon | DNS enumeration and reconnaissance |
| Kali Linux / Linux Terminal | Command-line environment |

---

## 📂 Repository Structure

```text
Web-Reconnaissance-Networkwalks/
│
├── README.md
│
├── 01-WHOIS-Lookup/
│   ├── screenshots/
│   └── findings.md
│
├── 02-WhatWeb-Technology-Fingerprinting/
│   ├── screenshots/
│   └── findings.md
│
├── 03-Nslookup-DNS-Investigation/
│   ├── screenshots/
│   └── findings.md
│
├── 04-cURL-HTTP-Header-Analysis/
│   ├── screenshots/
│   └── findings.md
│
├── 05-WAFW00F-WAF-Detection/
│   ├── screenshots/
│   └── findings.md
│
├── 06-DNSRecon-DNS-Enumeration/
│   ├── screenshots/
│   └── findings.md
│
└── lessons-learned.md
```

---

# 🔬 Practical Exercises

## 01. WHOIS Lookup – Domain Registration Investigation

**Objective:** Gather publicly available domain registration information to understand the domain's registrar, registration dates, nameservers, and domain status.

### Work Performed

Executed the WHOIS command to retrieve registration information associated with `networkwalks.com`.

```bash
whois networkwalks.com
```

### Findings

The investigation revealed the following information:

| Information | Result |
|---|---|
| Domain | networkwalks.com |
| Registrar | GoDaddy.com, LLC |
| Creation Date | 6 November 2019 |
| Updated Date | 12 November 2025 |
| Expiration Date | 6 November 2027 |
| Registrar WHOIS Server | whois.godaddy.com |
| Registrant | Registration Private |
| Privacy Provider | Domains By Proxy, LLC |
| DNSSEC | Unsigned |
| Nameserver 1 | NS6135.HOSTGATOR.COM |
| Nameserver 2 | NS6136.HOSTGATOR.COM |

The WHOIS output also contained the following domain status restrictions:

- clientDeleteProhibited
- clientRenewProhibited
- clientTransferProhibited
- clientUpdateProhibited

These restrictions indicate that certain domain registration changes are locked at the registry level.

The registrant information was privacy-protected through Domains By Proxy, LLC.

### Challenges Encountered

- Interpreting the different fields returned by WHOIS.
- Understanding the difference between publicly available registration information and privacy-protected registrant information.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| Registrant identity was not directly visible. | Examined the registration privacy information and identified Domains By Proxy, LLC as the privacy service provider. |
| Different nameserver entries appeared across the registry and registrar sections. | Recorded the differences and treated them as information requiring further DNS verification rather than assuming all entries were simultaneously authoritative. |

### Key Lesson Learnt

WHOIS provides valuable information about domain registration, registrar details, registration dates, and nameserver configurations.

However, privacy protection can limit the availability of registrant information. WHOIS information should also be correlated with DNS investigation results.

### 📸 Screenshots / Evidence
<img width="2736" height="1824" alt="whois1" src="https://github.com/user-attachments/assets/1a62eee1-69c2-4ca0-81c1-f68116995127" />
<img width="2736" height="1824" alt="whois2" src="https://github.com/user-attachments/assets/1b02b333-8af4-465e-a1aa-6a6864ece92a" />

<img width="2736" height="1824" alt="whois3" src="https://github.com/user-attachments/assets/4f9f3021-4a32-4cc7-b823-210d2983a2fe" />


`01-WHOIS-Lookup/screenshots/`

Suggested evidence:

- WHOIS command execution.
- Domain registration information.
- Registrar and nameserver details.
- Domain status information.

---

## 02. WhatWeb – Website Technology Fingerprinting

**Objective:** Identify the technologies, frameworks, server software, and content management systems used by the target website.

### Work Performed

Executed WhatWeb against the target domain.

```bash
whatweb http://networkwalks.com
```

Also examined the HTTPS version:

```bash
whatweb https://networkwalks.com
```

### Findings

The WhatWeb scan identified several technologies and configurations.

| Technology / Component | Detected Information |
|---|---|
| Web Server | Apache |
| Content Management System | WordPress 7.1.4 |
| WordPress Download Manager | 3.3.76 |
| Front-end Framework | Bootstrap 7.1.4 |
| JavaScript Library | jQuery 3.7.1 |
| Markup Technology | HTML5 |
| Analytics | Google Tag Manager |
| Open Graph | Website protocol detected |
| HTTP Security | HttpOnly cookie attribute detected |
| Email | info@networkwalks.com |
| IP Address | 192.232.216.135 |
| Country Identification | United States |

The HTTP version returned a `301 Moved Permanently` response, redirecting visitors to the HTTPS version of the website.

The HTTPS request returned `200 OK`, indicating a successful response.

### Challenges Encountered

- Interpreting the different technologies identified by WhatWeb.
- Understanding the significance of HTTP-to-HTTPS redirection and detected software versions.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| Multiple technologies were returned in a single scan, making the results difficult to interpret. | Categorised the results into web server, CMS, JavaScript libraries, frameworks, and other technologies. |
| The HTTP scan returned a redirect instead of the final website response. | Performed a separate scan against the HTTPS URL to inspect the final response and identify additional technologies. |

### Key Lesson Learnt

Technology fingerprinting helps security professionals understand a website's technology stack and identify areas that may require further security review.

However, identifying a software version does not automatically mean that the software is vulnerable. Further verification is necessary.

### 📸 Screenshots / Evidence
<img width="2736" height="1824" alt="whatweb" src="https://github.com/user-attachments/assets/43efacbc-2857-4ad7-848f-5d05064d2228" />

`02-WhatWeb-Technology-Fingerprinting/screenshots/`

Suggested evidence:

- WhatWeb HTTP scan.
- WhatWeb HTTPS scan.
- Detected WordPress version.
- Identified web technologies.

---

## 03. Nslookup – DNS Investigation

**Objective:** Investigate DNS resolution and determine the IP address associated with the target domain.

### Work Performed

Executed the Nslookup command.

```bash
nslookup networkwalks.com
```

### Findings

The command returned the following information:

| Attribute | Result |
|---|---|
| DNS Server | 10.0.0.1 |
| DNS Server Address | 10.0.0.1#53 |
| Domain | networkwalks.com |
| Resolved IPv4 Address | 192.232.216.135 |
| Response Type | Non-authoritative answer |

The DNS lookup successfully resolved the domain to:

```text
192.232.216.135
```

However, the command also returned DNS communication timeout errors.

Observed errors included:

```text
communications error to 10.0.0.1#53: timed out
communications error to 192.168.43.210#53: timed out
no servers could be reached
```

This indicated intermittent DNS resolution or communication issues with the configured DNS servers.

### Challenges Encountered

- DNS communication timeouts during the lookup.
- Inconsistent responses from the configured DNS resolvers.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| The configured DNS server at 10.0.0.1 timed out during subsequent requests. | Investigate local DNS connectivity, resolver availability, and network configuration. Retry the lookup after confirming DNS connectivity. |
| Another DNS server at 192.168.43.210 also returned timeout errors. | Check the active network interface and DNS resolver configuration. Compare results using an approved alternative DNS resolver. |

### Key Lesson Learnt

DNS resolution is essential for translating domain names into IP addresses.

However, a successful DNS response does not necessarily mean that every subsequent DNS request will succeed. Resolver availability, network connectivity, and DNS configuration can affect results.

### 📸 Screenshots / Evidence
<img width="2736" height="1824" alt="nslookup" src="https://github.com/user-attachments/assets/cc8e78ee-14ee-439e-a25c-2783552647da" />

`03-Nslookup-DNS-Investigation/screenshots/`

Suggested evidence:

- Nslookup command execution.
- Successful IP resolution.
- DNS server details.
- Communication timeout messages.

---

## 04. cURL – HTTP Header Analysis

**Objective:** Examine the HTTP response headers returned by the web server to understand server responses, cookie attributes, and observable security-related configurations.

### Work Performed

Executed the cURL command with the `-I` option to retrieve HTTP response headers.

```bash
curl -I https://networkwalks.com
```

### Findings

The server returned the following response:

```text
HTTP/2 200
```

This indicated that the HTTPS request was successfully processed.

Important headers observed included:

| Header | Observed Information |
|---|---|
| HTTP Status | HTTP/2 200 |
| Server | Apache |
| Content-Type | text/html; charset=UTF-8 |
| Referrer-Policy | no-referrer-when-downgrade |
| X-Endurance-Cache-Level | 0 |
| X-Nginx-Cache | WordPress |
| Set-Cookie | __wpdm_client |
| Cookie Security | Secure; HttpOnly |

The response also included WordPress API-related links:

```text
https://networkwalks.com/wp-json/
```

The cookie contained the following security attributes:

- Secure
- HttpOnly

These attributes help restrict cookie transmission to secure connections and prevent direct JavaScript access to the cookie, respectively.

### Challenges Encountered

- Understanding the meaning of different HTTP response headers.
- Distinguishing between server information, application-specific headers, and security-related cookie attributes.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| Multiple response headers made it difficult to identify important security information. | Categorised the headers into server information, content information, caching, cookies, and security-related attributes. |
| Understanding the security implications of cookie attributes was challenging. | Examined the Secure and HttpOnly attributes and documented their respective security purposes. |

### Key Lesson Learnt

HTTP response headers provide useful information about web server behaviour and security configurations.

Cookie attributes such as Secure and HttpOnly are important protections, but they do not replace a complete web application security assessment.

### 📸 Screenshots / Evidence
<img width="2736" height="1824" alt="curl" src="https://github.com/user-attachments/assets/4dc0b902-a044-4b54-b7ba-f40c9a90def4" />

`04-cURL-HTTP-Header-Analysis/screenshots/`

Suggested evidence:

- cURL command execution.
- HTTP/2 200 response.
- Server and content headers.
- Cookie security attributes.

---

## 05. WAFW00F – Web Application Firewall Detection

**Objective:** Identify whether the target website is protected by a Web Application Firewall and determine the WAF technology detected.

### Work Performed

Executed WAFW00F against the target website.

```bash
wafw00f https://networkwalks.com
```

### Findings

The WAFW00F scan returned the following result:

```text
WAFW00F : v2.4.2

Checking https://networkwalks.com

The site https://networkwalks.com
is behind ModSecurity (SpiderLabs) WAF.

Number of requests: 2
```

<badge color="success">WAF detected</badge>

The investigation identified **ModSecurity (SpiderLabs)** as the Web Application Firewall protecting the target website.

The tool used two requests during the detection process.

### Challenges Encountered

- Understanding how WAF detection tools identify protective mechanisms.
- Interpreting the difference between detecting a WAF and evaluating its effectiveness.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| It was not immediately clear which WAF technology was protecting the website. | Used WAFW00F to analyse the website's responses and identify the reported ModSecurity WAF. |
| A successful WAF detection could be mistaken for proof that the website was completely secure. | Distinguished between WAF identification and security effectiveness. Documented that further authorised testing would be required to evaluate its configuration and effectiveness. |

### Key Lesson Learnt

A Web Application Firewall provides an additional layer of protection against malicious web requests.

However, detecting a WAF does not establish that the entire website is secure. Proper configuration, monitoring, and regular security assessments remain important.

### 📸 Screenshots / Evidence
<img width="2736" height="1824" alt="wafw00f" src="https://github.com/user-attachments/assets/221ea93f-4fba-4f42-9ad1-cf0a9b0faca3" />

`05-WAFW00F-WAF-Detection/screenshots/`

Suggested evidence:

- WAFW00F command execution.
- ModSecurity detection result.
- Number of requests used during detection.

---
# 06 – DNS Enumeration Using DNSRecon
## Objective
To perform DNS enumeration against `networkwalks.com` using DNSRecon and identify publicly available DNS records, including nameserver, address, text, service, and start-of-authority records.

## Tool Used

- **Tool:** DNSRecon
- **Environment:** Kali Linux
- **Target:** `networkwalks.com`
- **Command executed:**

```bash
dnsrecon -d networkwalks.com
```

## Findings and Observations

The DNSRecon scan completed and returned the following information:

| Record type | Observed result |
|---|---|
| SOA | `ns6135.hostgator.com` – `50.87.144.87` |
| NS | `ns6135.hostgator.com` – `50.87.144.87` |
| NS | `ns6136.hostgator.com` – `192.232.216.131` |
| A | `networkwalks.com` – `192.232.216.135` |
| TXT | A Google site-verification record was identified |
| TXT | An SPF record was identified |
| SRV | Multiple cPanel email-autodiscovery service records were returned |
| DNSSEC | The DNSSEC query returned no answer |

The SPF record observed was:

```text
v=spf1 +a +mx +ip4:50.87.144.87 +include:websitewelcome.com ~all
```

The SRV records identified the service:

```text
_autodiscover._tcp.networkwalks.com
```

They pointed to `cpanelemaildiscovery.cpanel.net` on port `443`, with multiple IP addresses returned by the scan.

DNSRecon reported **8 Records Found** at the end of the SRV enumeration.

## Analysis

The results provided useful information about the domain's DNS configuration and supporting infrastructure.

1. **Nameserver identification:** Two nameservers were returned, both associated with HostGator infrastructure.
2. **IP address discovery:** The A record resolved `networkwalks.com` to `192.232.216.135`.
3. **SOA information:** The SOA record identified `ns6135.hostgator.com` as the reported primary nameserver.
4. **TXT record discovery:** The scan identified a Google site-verification record and an SPF policy. The SPF record provides information about the domain's stated email-sending policy.
5. **Service discovery:** The SRV records exposed cPanel email-autodiscovery configuration, including its destination hostname and port.
6. **DNSSEC observation:** DNSRecon did not receive an answer to its DNSSEC query. This result alone does not establish why the query received no answer or independently prove the domain's complete DNSSEC status.

The nameserver results are consistent with the HostGator nameservers observed during the earlier WHOIS exercise.

## Challenges and Solutions

### Challenge 1: Interpreting different DNS record types

The scan returned several record types, each serving a different purpose. Understanding the difference between SOA, NS, A, TXT and SRV records was necessary to interpret the output correctly.

**Solution:** I reviewed the purpose of each record type and organised the results by record category to make the findings easier to understand.

### Challenge 2: Understanding the DNSSEC query result

The scan reported that there was no answer for the DNSSEC query. This required care when interpreting the result because a missing response does not, by itself, explain the underlying cause.

**Solution:** I documented the exact DNSRecon message and avoided making an unsupported conclusion about the domain's DNSSEC configuration.

## Lessons Learned

- DNS enumeration can reveal useful information about a domain's hosting and supporting services.
- SOA and NS records help identify authoritative DNS infrastructure.
- A records reveal the IPv4 address associated with a domain.
- TXT records can expose domain-verification and email-policy information.
- SRV records can reveal service-discovery configuration.
- DNSSEC query results should be interpreted carefully and verified with additional checks where necessary.
- Reconnaissance findings should be documented accurately without automatically treating publicly available records as security vulnerabilities.

## Evidence
<img width="1631" height="1116" alt="dnsrecon" src="https://github.com/user-attachments/assets/95af1877-bb2e-4245-9fc2-94ad00a4b30d" />

```text
06-DNSRecon-DNS-Enumeration/screenshots/
```
The DNSRecon exercise successfully identified multiple DNS record types associated with `networkwalks.com`, including SOA, NS, A, TXT and SRV records. It also provided visibility into the domain's nameserver infrastructure, SPF policy and cPanel email-autodiscovery configuration.

This exercise strengthened my understanding of DNS enumeration and demonstrated how DNSRecon can support the information-gathering phase of an authorised security assessment.
#

# 📊 Overall Key Findings

The reconnaissance exercise produced the following observations:

| Assessment Area | Key Finding |
|---|---|
| Domain Registration | Registered through GoDaddy |
| Domain Privacy | Registrant information protected by Domains By Proxy |
| Domain Creation | 6 November 2019 |
| Domain Expiration | 6 November 2027 |
| DNSSEC | Unsigned |
| IP Resolution | 192.232.216.135 |
| Web Server | Apache |
| CMS | WordPress |
| JavaScript Library | jQuery 3.7.1 |
| Download Manager | WordPress Download Manager 3.3.76 |
| HTTP Response | 301 redirect to HTTPS |
| HTTPS Response | HTTP 200 |
| Cookie Attributes | Secure and HttpOnly observed |
| WAF | ModSecurity (SpiderLabs) |
| DNSRecon |DNSRecon exercise successfully identified multiple DNS record  |

## 🛡️ Security Recommendations

Based on the information collected, the following areas are worth reviewing during an authorised security assessment.

1. **DNSSEC:** Review DNSSEC deployment to determine whether DNS response integrity protections are appropriate for the domain.
2. **Software Maintenance:** Verify that WordPress, its plugins, and JavaScript dependencies are supported and updated.
3. **HTTP Security Headers:** Review the complete set of HTTP security headers, including Content-Security-Policy, Strict-Transport-Security, and X-Content-Type-Options.
4. **Cookie Security:** Review session cookie configuration, including Secure, HttpOnly, and SameSite attributes where applicable.
5. **WAF Configuration:** Review ModSecurity rules, logging, monitoring, and update practices.
6. **DNS Infrastructure:** Verify authoritative nameserver consistency and DNS resolver reliability.
7. **Information Disclosure:** Review whether publicly exposed technology and server information is necessary.

These are recommendations for further verification, not confirmed vulnerabilities.

---

# 📚 Lessons Learnt

This practical exercise strengthened my understanding of the importance of reconnaissance in cybersecurity.

My key takeaways include:

**1. Domain Intelligence Is Valuable**

WHOIS helps establish domain registration information, registrar details, nameservers, and registration status.

**2. Technology Fingerprinting Improves Visibility**

WhatWeb provides useful insight into the technologies and frameworks powering web applications.

**3. DNS Is Fundamental to Network Communication**

Nslookup and DNSRecon demonstrate how domain resolution and DNS records contribute to understanding network infrastructure.

**4. HTTP Headers Reveal Important Information**

cURL provides a simple way to inspect server responses, cookie attributes, and other HTTP configurations.

**5. WAF Detection Is an Important Assessment Step**

WAFW00F helps identify protective technologies that may be deployed in front of web applications.

**6. Reconnaissance Requires Correlation**

No single tool provides a complete picture of a target. Combining WHOIS, DNS, HTTP, technology fingerprinting, and WAF detection produces a more useful understanding of the web infrastructure.

---

# 🚀 Skills Gained

| Technical Skill | Practical Application |
|---|---|
| Domain Reconnaissance | Collecting domain registration information |
| WHOIS Investigation | Identifying registrar and domain status |
| Technology Fingerprinting | Identifying website technologies |
| DNS Analysis | Investigating domain resolution |
| DNS Enumeration | Understanding DNS record discovery |
| HTTP Analysis | Inspecting response headers |
| Web Security Assessment | Reviewing observable security configurations |
| WAF Detection | Identifying ModSecurity |
| Linux Command Line | Executing reconnaissance commands |
| Technical Documentation | Recording findings and troubleshooting results |

---

# 📝 Conclusion

This practical web reconnaissance exercise provided valuable exposure to the information-gathering phase of cybersecurity assessments.

By using WHOIS, WhatWeb, Nslookup, cURL, WAFW00F, and DNSRecon, I explored how different tools can be used to investigate domain registration information, identify website technologies, analyse DNS resolution, inspect HTTP headers, and detect Web Application Firewall technologies.

One important takeaway was that effective reconnaissance involves more than running commands. It requires interpreting results, identifying limitations, troubleshooting errors, and correlating information from different sources.

The exercise further strengthened my interest in **Cybersecurity, Network Security, Web Application Security, Digital Forensics, and Penetration Testing**.

I look forward to building on these practical skills through additional cybersecurity labs and authorised security assessments.

---

## 🔗 Connect and Follow My Learning Journey

I am continuously developing my practical skills in Cybersecurity, Network Security, Digital Forensics, and IT Infrastructure.

If you find this project useful, feel free to ⭐ star the repository, explore the exercises, and share your feedback.

**Tools:** WHOIS | WhatWeb | Nslookup | cURL | WAFW00F | DNSRecon

**Areas of Interest:** Cybersecurity | Web Reconnaissance | Network Security | Web Application Security | Digital Forensics

---

## ⚖️ Disclaimer

This repository documents an educational reconnaissance exercise.

All security assessments, DNS enumeration, technology fingerprinting, and other testing activities must be conducted on systems for which appropriate permission has been obtained.

The information documented here represents observations from the supplied practical command outputs and should not be interpreted as confirmation of vulnerabilities or evidence of compromise.

---

<p align="center">
  <b>Learn. Explore. Investigate. Secure.</b>
  <br>
  <i>Building practical cybersecurity skills, one assessment at a time.</i>
</p>

#Cybersecurity #WebReconnaissance #InformationGathering #KaliLinux #WHOIS #WhatWeb #DNSRecon #WAFW00F #NetworkSecurity #EthicalHacking
