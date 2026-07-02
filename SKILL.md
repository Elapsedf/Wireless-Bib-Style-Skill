---
name: ieee-bib-style-audit
description: Audit and normalize BibTeX files against a wireless IEEE bibliography template; 审核并规范 BibTeX 文件，使其符合无线通信论文常用 IEEE 参考文献格式。
---

# IEEE Bib Style Audit

## Overview

Use this skill for read-only BibTeX style audits and, when explicitly requested, targeted BibTeX cleanup.
The local target style is defined by `template.bib` plus `references/style-rules.md`: IEEE-style abbreviated venues, initialized author names, conference `Proc.` prefixes, conference location/month fields, and arXiv-specific metadata.

This is a local-style skill, not a universal BibTeX law. Infer the style from the user's canonical `.bib` first when one is provided; otherwise use this repository's `template.bib` as the reference.

## Required Sources

Before auditing or cleaning a `.bib` file:

1. Read the user-provided canonical `.bib` if the user names one.
2. Read this repository's `template.bib` when the user asks for this wireless IEEE template, when no canonical file is supplied, or when checking string macro names.
3. Read `references/style-rules.md` for the checklist and preferred entry shapes.

## Workflow

1. Extract the dominant style before judging entries: author format, journal strings/macros, conference booktitle format, month format, arXiv format, and optional fields that the local paper keeps.
2. Audit the requested `.bib` files without editing unless the user explicitly asks to modify them.
3. Report findings grouped by file and entry key, with line numbers and concrete reasons.
4. Separate clear issues from judgment calls, especially for arXiv preprints, books, and ML conference proceedings.
5. If asked to fix, keep changes scoped to the reported entries and preserve citation keys unless the user requests deduplication or key renaming.
6. Do not guess missing metadata such as volume, number, pages, month, DOI, or address. If unavailable, mark it as missing or leave it unchanged.

## Core Checks

- Author names: prefer `Last, F.` or `Last, F. M.` joined by `and`; flag full-name natural-order authors unless the local file deliberately uses them.
- Journal names: prefer IEEE string macros from `template.bib`, such as `ieee_j_wcom`, or abbreviated literal names such as `{IEEE Trans. Wireless Commun.}`; flag full journal names like `IEEE Transactions on ...`.
- Journal metadata: expect `volume`, `number`, `pages`, `month`, `year`, and `doi` when available; flag empty pages and inconsistent month styles.
- Conference names: expect `booktitle={Proc. ...}` or a local string macro that expands to `Proc.`; flag full conference names that are not abbreviated.
- Conference metadata: expect `address={City, State/Country}` and `month={Mon.}`; flag entries using only `location` when the local style prefers `address`.
- arXiv entries: prefer `@misc` with `journal={arXiv preprint arXiv:...}`, `eprint`, `archivePrefix={arXiv}`, optional `primaryClass`, and `[Online]. Available: ...`.
- Duplicates: report duplicate BibTeX keys and likely duplicate titles even when the keys differ.

## Reporting Format

For audits, use concise bullets:

```text
Style summary: ...

File: path/to/file.bib
- L123 `key`: issue; suggested direction.
```

Include a short style summary first when the user asks for the rule pattern.
Do not claim an item is wrong when it is only a local-style decision; label it as "judgment call" or "worth checking".
