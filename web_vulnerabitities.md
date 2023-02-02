# Web Vulnerabilities

- [Web Vulnerabilities](#web-vulnerabilities)
  - [Cross-Site Scripting (XSS)](#cross-site-scripting-xss)
    - [Examples](#examples)
    - [Reflected XSS](#reflected-xss)
    - [Stored XSS](#stored-xss)
    - [Payloads](#payloads)
    - [Solutions](#solutions)

## Cross-Site Scripting (XSS)

Injection of client-side scripts into web pages viewed by other users

### Examples

In a chat application the message "Hello <script>alert('world')</script>" makes a popup appear on the other user's screen

### Reflected XSS

A reflected XSS attack occurs when an attacker can trick a user into visiting a malicious website. The malicious website then sends a malicious payload to the vulnerable website. The vulnerable website then reflects the malicious payload back to the user's browser. The user's browser then executes the malicious payload. It's not persistent, it's just a one-time attack.

![Reflected XSS](./ressources/reflectedXSS.png)

### Stored XSS

A stored XSS is when a malicious payload is stored on the vulnerable website. When a user visits the vulnerable website, the malicious payload is retrieved from the database and executed by the user's browser. It's persistent and can be triggered multiple times.

![Stored XSS](./ressources/storedXSS.png)

### Payloads

```html
<script>alert('XSS')</script>
```

[Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XSS%20Injection/README.md)

### Solutions

Sanitize user input

- [OWASP XSS Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
