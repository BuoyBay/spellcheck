---
title: "Native spell checking API"
summary: "Public symbols and contracts for the spellcheck package."
category: "Reference"
order: 20
keywords: ["spelling", "suggestions", "language", "UTF16"]
symbols: ["SpellCheckSupported", "SpellLanguages", "FirstMisspelling", "SpellingSuggestions", "SpellingMatch", "SpellingMatch.Word", "SpellingMatch.StartUTF16", "SpellingMatch.LengthUTF16"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# API reference

Import `spellcheck` from the sealed package. The signatures below describe its public surface.

| Symbol | Contract |
| --- | --- |
| `SpellCheckSupported() As Boolean` | Report platform support. |
| `SpellLanguages() As Array Of String` | List native spelling languages. |
| `FirstMisspelling(text As String, language As String = "") As Optional Of SpellingMatch` | Return the first misspelling, or None. |
| `SpellingSuggestions(word As String, language As String = "", maximum As Integer = 12) As Array Of String` | Return up to maximum suggestions; valid range 1–100. |
| `SpellingMatch.Word As String` | Read-only matched Unicode word. |
| `SpellingMatch.StartUTF16 / LengthUTF16 As Integer` | Read-only native range measured in UTF-16 code units. |
| `New SpellingMatch(startUTF16, lengthUTF16, word)` | Construct a snapshot from two Integer values and a String. |

## Errors and lifecycle

`StartUTF16` and `LengthUTF16` use Cocoa UTF-16 code units, not UTF-8 bytes or a generic Buoy substring index. Convert offsets correctly before highlighting Unicode text in your editor. An empty language requests the native default. Suggestions reject a blank word and require `maximum` from 1 through 100; the default is 12. No first match returns `None` rather than an exception.

Each check uses a temporary native spell-document tag and closes it before returning, including when an exception occurs. The returned `SpellingMatch` holds read-only Buoy data and requires no native cleanup.

## Platform support

Requires macOS and the main thread. `SpellCheckSupported()` returns False elsewhere; native operations throw `UnsupportedOperationException` on Windows and Linux. Results depend on installed dictionaries and language support.

[Getting started](getting-started.md) · [Package overview](index.md)


[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
