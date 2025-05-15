# XSS Testing Basics with BurpSuite

## Overview

This guide outlines how to test for basic Cross-Site Scripting (XSS) vulnerabilities using BurpSuite and Firefox with the FoxyProxy extension.

---

## Prerequisites

- Firefox browser with the [**FoxyProxy**](https://getfoxyproxy.org/) extension installed.
- BurpSuite installed and running.

---

## Step 1: Configure FoxyProxy

1. Open **FoxyProxy** settings in Firefox.
2. Add a new proxy with the following configuration:
    - **Proxy Type:** HTTP
    - **IP Address:** `127.0.0.1`
    - **Port:** `8080` (or adjust if using a different BurpSuite proxy setting)

> **Tip:**  
> Label this proxy something clear, such as **"BurpSuite Proxy"**, for easy toggling.

---

## Step 2: Set Up BurpSuite

- Open **BurpSuite**.
- Go to the **Proxy** tab.
- Ensure **Intercept** is toggled to **ON**.

---

## Step 3: Locate the Target Form

1. In Firefox, navigate to the **target URL** containing the input form.
2. Note whether any **client-side validation** is enforced on the fields.

> ⚠️ **Note:**  
> Even if client-side validation blocks certain inputs, server-side processing may still be vulnerable.

3. Submit the form with data that passes client-side validation.
4. Click the **Submit Query!** button.

---

## Step 4: Inject XSS via BurpSuite

1. In BurpSuite, intercept the request sent from the form.
2. Identify the input field to target (e.g., `email`).
3. Replace the value of that field with a basic XSS payload.

### Example Payload:

```html
<script>alert('XSS')</script>
```

4. Forward the modified request.

---

> ✅ If the response renders the payload without sanitization, the application is vulnerable to XSS.

---

## Final Notes

- Always keep your testing ethical and within legal bounds.
- Only test systems for which you have explicit authorization.
- Consider trying different payloads to test for stored or DOM-based XSS.

> ⚠️ **Disclaimer:**  
> This guide is for educational and authorized testing purposes only. Unauthorized testing is illegal and unethical.
