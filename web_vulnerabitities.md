# Web Vulnerabilities

- [Web Vulnerabilities](#web-vulnerabilities)
  - [Cross-Site Scripting (XSS)](#cross-site-scripting-xss)
    - [Examples](#examples)
    - [Reflected XSS](#reflected-xss)
    - [Stored XSS](#stored-xss)
    - [Payloads](#payloads)
    - [Solutions](#solutions)
  - [External Entity Injection (XXE)](#external-entity-injection-xxe)
    - [Examples](#examples-1)
    - [Payloads](#payloads-1)
  - [Cross-Site Request Forgery (CSRF)](#cross-site-request-forgery-csrf)
    - [Examples](#examples-2)
    - [Payloads](#payloads-2)
  - [SQL Injection](#sql-injection)
    - [Examples](#examples-3)
    - [Payloads](#payloads-3)
  - [Open Redirect](#open-redirect)
    - [Examples](#examples-4)
    - [Payloads](#payloads-4)
  - [References](#references)

## Cross-Site Scripting (XSS)

Injection of client-side scripts into web pages viewed by other users

### Examples

In a chat application the message "Hello <script>alert('world')</script>" makes a popup appear on the other user's screen

### Reflected XSS

A reflected XSS attack occurs when an attacker can trick a user into visiting a malicious website. The malicious website then sends a malicious payload to the vulnerable website. The vulnerable website then reflects the malicious payload back to the user's browser. The user's browser then executes the malicious payload. It's not persistent, it's just a one-time attack.

![Reflected XSS](./ressources/reflectedXSS.png)

### Stored XSS

A stored XSS is when a malicious payload is stored on the vulnerable website. When a user visits the vulnerable website, the malicious payload is retrieved from the database and executed by the user's browser. It's persistent and can be triggered multiple times.

![Stored XSS](./ressources/StoredXSS.png)

### Payloads

```html
<script>alert('XSS')</script>
```

[Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XSS%20Injection/README.md)

### Solutions

Sanitize user input

- [OWASP XSS Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

## External Entity Injection (XXE)

Injection of XML external entities into web pages, which can be used to read files on the server and perform Server-Side Request Forgery (SSRF)

### Examples

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE foo [ <!ELEMENT foo ANY >
<!ENTITY xxe SYSTEM "file:///etc/passwd" >]>
<stockCheck>
<productId>&xxe;</productId>
</stockCheck>
```

### Payloads

[Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XXE%20Injection/README.md)

## Cross-Site Request Forgery (CSRF)

A malicious website can trick a user into visiting a malicious website. The malicious website then sends a request to the vulnerable website. The vulnerable website then executes the request. It's not persistent, it's just a one-time attack.

### Examples

```html
<img src="http://vulnerable-website.com/transfer?to=attacker&amount=1000000" />
```

### Payloads

[Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/CSRF%20Injection/README.md)

## SQL Injection

Modification of SQL queries to bypass authentication or retrieve data from the database

### Examples

Sending the following request to a login page

```http
username=admin' OR '1'='1'&password=123
```

### Payloads

[Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md)

## Open Redirect

Redirecting a user to a malicious website

### Examples

```html
<a href="http://vulnerable-website.com/redirect?url=http://malicious-website.com">Click here</a>
```

### Payloads

[Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Open%20Redirect/README.md)

## References

- [OWASP](https://owasp.org/)
- [TryHackMe - Owasp Top 10](https://tryhackme.com/room/owasptop10)
- [Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings)
