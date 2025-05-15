# Passive Reconnaissance

## Tools Used
- `whois`
- `nslookup`
- `dig`

---

## Passive Reconnaissance Overview

Passive reconnaissance involves **gathering information without directly interacting** with the target. This type of reconnaissance relies solely on publicly accessible data.

**Examples:**
- Retrieving DNS records using a public DNS server
- Reviewing job listings related to the target
- Reading news articles about the organization

---

## Active Reconnaissance Overview

In contrast, active reconnaissance **involves direct interaction** with the target and is generally considered intrusive.

**Examples:**
- Connecting to target services (e.g., HTTP, FTP, SMTP)
- Calling the company for information (social engineering)
- Physically accessing premises under false pretenses (social engineering)

---

## `whois`

**Description:**  
The `whois` command provides domain registration details.

**Syntax:**  
```
whois {domain.com}
```

**Example:**  
```
whois tryhackme.com
```

---

## `nslookup`

**Description:**  
`nslookup` retrieves information about domain names and IP addresses.

**Query Types:**

| Query Type | Description           |
|------------|------------------------|
| A          | IPv4 addresses         |
| AAAA       | IPv6 addresses         |
| CNAME      | Canonical name         |
| MX         | Mail servers           |
| SOA        | Start of authority     |
| TXT        | TXT records            |

**Syntax:**  
```
nslookup -type={QueryType} {domain}
```

**Examples:**  
```
nslookup -type=A tryhackme.com
nslookup -type=MX tryhackme.com
```

---

## `dig`

**Description:**  
`dig` is a flexible DNS lookup tool.

**Options:**

| Option    | Description                         |
|-----------|-------------------------------------|
| +short    | Concise output                      |
| +stats    | Displays statistics                 |
| +trace    | Traces the DNS lookup path          |
| @server   | Queries a specific DNS server       |

**Query Types:**

| Query Type | Description       |
|------------|-------------------|
| A          | IPv4 address      |
| MX         | Mail server       |
| NS         | Name server       |
| CNAME      | Canonical name    |

**Syntax:**  
```
dig [options] domain_name [query_type]
```

**Examples:**  
```
dig tryhackme.com
dig @8.8.8.8 tryhackme.com
dig tryhackme.com MX
```

---

## Additional Tools

- **[dnsdumpster.com](https://dnsdumpster.com):** Used to discover subdomains.
- **[shodan.io](https://shodan.io):** Useful for gathering open port and service information.

