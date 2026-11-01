---
title: "Native spell checking"
summary: "Find misspellings and request bounded native spelling suggestions."
category: "Overview"
order: 0
keywords: ["spelling", "suggestions", "language", "UTF16"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# Native spell checking

The `spellcheck` package reads the macOS spelling service. It lists installed spelling languages, returns the first misspelling as an optional snapshot, and obtains bounded suggestions. It does not learn words, alter ignored-word dictionaries, or change the selected system language.

## Platform support

Requires macOS and the main thread. `SpellCheckSupported()` returns False elsewhere; native operations throw `UnsupportedOperationException` on Windows and Linux. Results depend on installed dictionaries and language support.

## Ownership and lifetime

Each check uses a temporary native spell-document tag and closes it before returning, including when an exception occurs. The returned `SpellingMatch` holds read-only Buoy data and requires no native cleanup.

## Read next

- [Getting started](getting-started.md)
- [API reference](api.md)
