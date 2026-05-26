# Stretchy Justification

A side-by-side typography demo that justifies text by adjusting the `wdth` axis of a variable font per line — no word-spacing tricks.

**[Live demo](https://pretext-newbreak.vercel.app)**

## What it does

| Panel | Behaviour |
|---|---|
| **Regular** | CSS `text-align: justify` at the font's default width |
| **Stretchy** | Each line is binary-searched to the `wdth` value that fills the column exactly. Expands from Regular upward first; condenses below Regular only when a line would overflow. Word-spacing is added as a last resort when even the widest setting isn't enough. |

Supports **English** (Knuth-Liang hyphenation via [hypher](https://github.com/bramstein/hypher) + [Pretext](https://github.com/chenglou/pretext) line-breaking), **Tamil** (browser Range API + soft hyphens), and **Arabic** (browser Range API, RTL).

## Controls

| Control | Effect |
|---|---|
| Column width | Width of each text column in px |
| Font size | Size in px |
| Space highlights | Tints inter-word spaces: red = wider than normal (up to 4×), blue = narrower than normal |
| Rivers | Highlights spaces in blue with alpha proportional to their vertical alignment with spaces on adjacent lines |
| Width axis subset | Clamps the `wdth` range the stretchy search is allowed to use |
| Upload override | Replace the bundled font for the current language |

## Running locally

```bash
python3 -m http.server 8081
# open http://localhost:8081
```

No build step. Fonts are bundled (`amstelvar.ttf`, `korkai.ttf`, `arabic.ttf`).

## Bundled fonts

| Language | Font | Stretch axis |
|---|---|---|
| English | [Amstelvar](https://github.com/googlefonts/amstelvar) | `wdth` 50–125 |
| Tamil | [Korkai](https://github.com/tenkodu/Korkai) | `wdth` 100–200 |
| Arabic | [Estedad v7.3](https://github.com/aminabedi68/Estedad) | `KSHD` 100–200 |
