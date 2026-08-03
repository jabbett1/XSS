# XSS Examples

Notes, excerpts, payloads, and references for cross-site scripting have been reorganized into a purpose-based `docs/` tree.

## Documentation index

| Area | Contents |
| --- | --- |
| [Methodology](docs/methodology/hack-steps.md) | Discovery and review steps for finding stored and reflected XSS. |
| [Payloads](docs/payloads/basic-payloads.md) | Basic payloads, context-specific payloads, and compact payloads. |
| [Techniques](docs/techniques/base-tag-hijacking.md) | Base tag hijacking, blind XSS, BeEF hook usage, and filter evasion notes. |
| [Legacy](docs/legacy/vbscript.md) | VBScript, mixed VBScript/JavaScript tricks, and browser-specific legacy payloads. |
| [Case studies](docs/case-studies/real-world-examples-documents.md) | Real-world incidents and XSS-to-RCE references. |
| [References](docs/references/links.md) | Curated links and external cheat sheets. |

## Folder map

- `docs/methodology/`
  - [hack-steps.md](docs/methodology/hack-steps.md)
- `docs/payloads/`
  - [basic-payloads.md](docs/payloads/basic-payloads.md)
  - [context-specific-payloads.md](docs/payloads/context-specific-payloads.md)
  - [compact-payloads.md](docs/payloads/compact-payloads.md)
- `docs/techniques/`
  - [base-tag-hijacking.md](docs/techniques/base-tag-hijacking.md)
  - [blind-xss.md](docs/techniques/blind-xss.md)
  - [beef-hooking.md](docs/techniques/beef-hooking.md)
  - [filter-evasion.md](docs/techniques/filter-evasion.md)
- `docs/legacy/`
  - [vbscript.md](docs/legacy/vbscript.md)
  - [combining-vbscript-and-javascript.md](docs/legacy/combining-vbscript-and-javascript.md)
  - [browser-specific-payloads.md](docs/legacy/browser-specific-payloads.md)
- `docs/case-studies/`
  - [real-world-examples-documents.md](docs/case-studies/real-world-examples-documents.md)
  - [xss-to-rce-examples.md](docs/case-studies/xss-to-rce-examples.md)
- `docs/references/`
  - [links.md](docs/references/links.md)
  - [portswigger-cheat-sheet.md](docs/references/portswigger-cheat-sheet.md)

## Safety note

These samples are intentionally dangerous and should only be reviewed or replayed in an isolated lab environment. The repository uses placeholder hosts and credentials where possible so examples do not point at live attacker infrastructure by default.
