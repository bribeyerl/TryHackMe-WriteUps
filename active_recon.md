# Active Reconnaissance (Linux)

Active reconnaissance involves directly interacting with systems and services to gather information about a target. Below are common Linux-based tools used during the reconnaissance phase of penetration testing or network diagnostics.

---

## Ping

**Purpose:**  
`ping` is used to test the availability of a remote system by sending ICMP echo requests and measuring the response time.

**Syntax:**
```bash
ping [options] [IP address]
```

**Example:**
```bash
ping -c 10 10.10.1.1
```

**Explanation:**
- `-c 10`: Sends 10 echo requests, then stops automatically.

---

## Traceroute

**Purpose:**  
`traceroute` identifies the path packets take from the local machine to a destination, listing each router (hop) along the way. This helps identify routing issues and potential bottlenecks.

**Syntax:**
```bash
traceroute [domain or IP]
```

**Example:**
```bash
traceroute tryhackme.com
```

---

## Telnet

**Purpose:**  
Although considered outdated, `telnet` is still useful for banner grabbing—revealing service information such as software and version numbers that can hint at vulnerabilities.

**Syntax:**
```bash
telnet [IP address] [port]
```

**Example:**
```bash
telnet 10.10.1.1 80
```

**Usage After Connection:**
Once connected, you can manually send HTTP requests:
```
GET / HTTP/1.1
```

---

## Netcat

**Purpose:**  
Nicknamed the “Swiss Army knife of networking,” `netcat` (or `nc`) is a versatile tool used for reading from and writing to network connections. It supports features such as port scanning, banner grabbing, and creating backdoors.

**Syntax:**
```bash
nc [options] [IP address] [port]
```

**Example:**
```bash
nc -nv 192.168.1.1 22
```

**Common Options:**
- `-l` : Listen mode (act as a server)
- `-v` : Verbose output
- `-n` : Disable DNS resolution for faster scans
- `-u` : Use UDP instead of TCP
- `-p` : Specify local port (used with `-l`)
- `-e` : Execute a program (e.g., `/bin/sh`) upon connection

> ⚠️ Note: The `-e` flag is often disabled in modern systems or Netcat versions due to its association with creating reverse shells.

---

## Summary

| Tool       | Purpose                              | Typical Use Case               |
|------------|--------------------------------------|--------------------------------|
| `ping`     | Check host availability              | Verify if a host is online     |
| `traceroute`| Trace packet path to a destination | Network diagnostics             |
| `telnet`   | Connect to ports and grab banners    | Identify service versions       |
| `netcat`   | Advanced networking operations       | Port scanning, banner grabbing |
