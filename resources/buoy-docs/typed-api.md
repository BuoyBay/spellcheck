---
title: "spellcheck typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["SpellRange", "SpellingMatch"]
dependencies: []
symbols: ["SpellRange", "SpellingMatch"]
related: ["api.md", "getting-started.md", "index.md"]
---

# spellcheck typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## SpellCheck functions

### SpellCheckSupported

`Public Function SpellCheckSupported() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### SpellLanguages

`Public Function SpellLanguages() As Array Of String`

No parameters.

#### Returns

| Type |
| --- |
| `Array Of String` |

### FirstMisspelling

`Public Function FirstMisspelling(text As String, language As String = "") As Optional Of SpellingMatch`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `text` | `String` | `ByVal` | Required |
| `language` | `String` | `ByVal` | `""` |

#### Returns

| Type |
| --- |
| `Optional Of SpellingMatch` |

### SpellingSuggestions

`Public Function SpellingSuggestions(word As String, language As String = "", maximum As Integer = 12) As Array Of String`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `word` | `String` | `ByVal` | Required |
| `language` | `String` | `ByVal` | `""` |
| `maximum` | `Integer` | `ByVal` | `12` |

#### Returns

| Type |
| --- |
| `Array Of String` |

## SpellRange

`Sequential Structure SpellRange`

### Fields

| Name | Type | Value / Default | Description |
| --- | --- | --- | --- |
| `Location` | `Integer` | — | — |
| `Length` | `Integer` | — | — |

## SpellingMatch

`Public Class SpellingMatch`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `StartUTF16` | `Integer` | Yes | No | — | — |
| `LengthUTF16` | `Integer` | Yes | No | — | — |
| `Word` | `String` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(startUTF16 As Integer, lengthUTF16 As Integer, word As String)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `startUTF16` | `Integer` | `ByVal` | Required |
| `lengthUTF16` | `Integer` | `ByVal` | Required |
| `word` | `String` | `ByVal` | Required |

Returns: no value.
