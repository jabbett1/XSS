# Blind XSS

## What it is

These notes describe using XSSHunter to validate a blind XSS that does not execute in a page visible to the attacker.

## When it applies

Use this when the application stores your input and only later renders it to another user, such as an administrator reviewing submitted data.

## Example

The original note uses a "contact us" page as an example: if the results are only viewable by an administrator manually and not the requesting user, the attacker would not immediately see their `alert(1)` attack.

XSSHunter workflow:

1. Disable any proxies (for example, Burp Suite).
2. Create an account at https://xsshunter.com
3. Log in at https://xsshunter.com/app
4. Go to Payloads to get your payload.
5. Modify the payload to fit your attack or build a polyglot with it.
6. Check XSS Hunter to see the payload execution.

The note explains that when the JavaScript payload executes, it will take a screenshot of the victim's screen and send that data back to the XSSHunter site. When this happens, XSSHunter sends an alert and provides detailed information so the attack can be replayed with a more malicious payload.

## Notes

The original content uses XSSHunter as the validation workflow and keeps the example focused on delayed rendering by an administrator.

## Source

Kim, Peter. *The Hacker Playbook 3: Practical Guide To Penetration Testing* (p. 59). Secure Planet. Kindle Edition.
