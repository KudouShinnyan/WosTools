# Translation contributions

[简体中文](CONTRIBUTING.md) · [English](CONTRIBUTING_EN.md)

## Files you may edit

UI strings live in these three files; add one more when contributing a new language:

- `res/values/strings.xml` (English, default)
- `res/values-zh-rCN/strings.xml` (Simplified Chinese)
- `res/values-ja/strings.xml` (Japanese)
- `res/values-<locale>/strings.xml` (new language, e.g. `values-ko`, `values-fr`, `values-zh-rTW`)

Please do not modify any other file in this repository.

## Rules

1. The `<string name="...">` keys must match the default English file exactly across every language; there are **161** keys at present. Do not add, remove or rename keys.
2. Keep the number and type of format arguments unchanged, e.g. `%1$d`, `%1$s`. Word order may change, the count may not.
3. Do not put raw backslashes, `&`, `<`, `>` or unescaped quotes inside string values; aapt2 will fail resource compilation. Use full-width or corner quotation marks instead.
4. Do not change the XML declaration or the `<resources>` structure, and do not add comment blocks.
5. Attribute names and page/button labels follow the wording actually shown in the game: Simplified Chinese for zh, Japanese for ja, English for en. The app's own decision terms (Keep / Re-roll / Quality up) are not copies of the game buttons.

## Adding a language

Drop `values-<locale>/strings.xml` into `res/`: after building, **Follow system** picks it up automatically, with no build-config or Java changes. Use the `-r` form for regions (e.g. `zh-rTW`).

To also make it selectable in the home language dropdown, the maintainer must register four places: the `AppPrefs.Lang` enum, the `Locale` in `AppPrefs.wrap()`, the home spinner options, and a `lang_<xx>` string in every language file. This ships with a later release.

Paths in this repository are `res/values-xx/`; the local build project uses `app/src/main/res/values-xx/`. The maintainer copies merged files over.

## Submitting

State which language you changed and which in-game screenshot backs the wording. After merge the maintainer syncs it into the build project for the next release.

This repository contains no application source; translation PRs are not used to build derivative APKs.
