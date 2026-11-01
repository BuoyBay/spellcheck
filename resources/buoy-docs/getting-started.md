---
title: "Native spell checking getting started"
summary: "Install spellcheck and use its native API with explicit ownership."
category: "Guides"
order: 10
keywords: ["spelling", "suggestions", "language", "UTF16"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

Install `spellcheck-0.1.0.buipkg` in `packages/` and import `spellcheck`. Inspect the Optional before using its value. The example reports the first matching word without changing the input text or any system dictionary.

```buoy
Import spellcheck

Sub Main()
    If Not SpellCheckSupported() Then Exit Sub
    Dim found As Optional Of SpellingMatch = FirstMisspelling("A mispelled word", "en_US")
    If found.HasValue Then
        Print found.Value.Word
    End If
End Sub
```

## Handle native constraints

`StartUTF16` and `LengthUTF16` use Cocoa UTF-16 code units, not UTF-8 bytes or a generic Buoy substring index. Convert offsets correctly before highlighting Unicode text in your editor. An empty language requests the native default. Suggestions reject a blank word and require `maximum` from 1 through 100; the default is 12. No first match returns `None` rather than an exception.

[Package overview](index.md) · [API reference](api.md)
