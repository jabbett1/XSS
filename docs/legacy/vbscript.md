# VBScript

## What it is

These notes cover using VBScript instead of JavaScript for XSS in Internet Explorer.

## When it applies

Use this when you are dealing with Internet Explorer-specific behavior or with filters that assume XSS will only use JavaScript syntax.

## Example

VBScript code can be introduced in several ways:

```html
<script language=vbs>MsgBox 1</script>
<img onerror="vbs:MsgBox 1" src=a>
<img onerror=MsgBox+1 language=vbs src=a>
```

In all cases, you can use `vbscript` instead of `vbs` to specify the language. In the last example, note the use of `MsgBox+1` to avoid the use of whitespace, thereby avoiding the need for quotes around the attribute value. This works because `+1` effectively adds the number `1` to nothing, so the expression evaluates to `1`, which is passed to the `MsgBox` function.

The original note also highlights that some functions can be called without brackets and that VBScript is not case-sensitive:

```html
<SCRIPT LANGUAGE=VBS>MSGBOX 1</SCRIPT>
<IMG ONERROR="VBS:MSGBOX 1" SRC=A>
```

## Notes

The case-insensitive behavior is called out as particularly useful when an application converts input to uppercase and breaks equivalent JavaScript payloads.

## Source

Stuttard, Dafydd. *The Web Application Hacker's Handbook* (Kindle Locations 12508-12520). Wiley. Kindle Edition.
