# Spelling and suggestions · 0.1.0

`Import spellcheck`. `SpellLanguages()` lists native languages. `FirstMisspelling(text, language = "")` returns Optional Of SpellingMatch, with Word, StartUTF16 and LengthUTF16. Offsets use Cocoa UTF-16 units, not UTF-8 byte positions. `SpellingSuggestions(word, language = "", maximum = 12)` returns up to the requested limit. Uses a temporary spell-document tag which is always closed. Never changes the selected system language, learned words, or ignored-word dictionary. Main thread required. Results depend on installed language dictionaries.

These native operations require macOS; `SpellCheckSupported()` returns False on Windows/Linux, and unsupported operations throw rather than silently emulating an Apple API. All six compiler targets are checked; native execution is verified on macOS arm64.

Maintainers run the private validation suite before release. See the repository README for public build instructions.

Inspired by [macoslib’s Cocoa examples](https://github.com/macoslib/macoslib); implemented independently against [Apple’s API](https://developer.apple.com/documentation/appkit/nsspellchecker).
