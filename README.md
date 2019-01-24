# wtfontmaps

My personal font maps for dvipdfmx (for documents in Japanese). The font maps are optimized for macOS + TeX Live + Morisawa passport. I haven't check whether these work on other environments.

You can use these settings freely for any purpose, but note that there is NO WARRANTY.

## How to use the font maps

To check the current font settings, type

```
$ kanji-config-updmap-sys status
```

To setup the font settings, type

```
$ sudo kanji-config-updmap-sys <map name>
```

where `<map name>` is one of the followings:

* `morisawa-pr6`
* `ryumin-shingo-pr6`
* `udreimin-udshingo-pr6`

Note that this have to be run **at the top-level of this repository** or move/symlink the font maps to a suitable place which the kpathsea library can find (e.g., under `$TEXMFDIST/fonts/map/dvipdfmx/`).

## License

Files in this repository are distributed under [the MIT license](./LICENSE).

---

Takuto ASAKURA ([wtsnjp](https://twitter.com/wtsnjp))
