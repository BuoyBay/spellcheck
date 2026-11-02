# Native spelling and suggestions

`Import spellcheck`. `SpellLanguages()` lists native languages. `FirstMisspelling(text, language = "")` returns Optional Of SpellingMatch, with Word, StartUTF16 and LengthUTF16. Offsets use Cocoa UTF-16 units, not UTF-8 byte positions. `SpellingSuggestions(word, language = "", maximum = 12)` returns up to the requested limit. Uses a temporary spell-document tag which is always closed. Never changes the selected system language, learned words, or ignored-word dictionary. Main thread required. Results depend on installed language dictionaries.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add spellcheck --git https://github.com/BuoyBay/spellcheck.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

```basic
Import spellcheck

Sub Main()
    If Not SpellCheckSupported() Then Exit Sub
    Dim found As Optional Of SpellingMatch = FirstMisspelling("A mispelled word", "en_US")
    If found.HasValue Then
        Print found.Value.Word
    End If
End Sub
```

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer spellcheck
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
