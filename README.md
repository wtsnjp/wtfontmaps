# wtfontmaps

My personal Japanese font maps for dvipdfmx. The font maps are optimized for macOS + TeX Live + Morisawa passport.

You can use these settings freely for any purpose, but note that there is NO WARRANTY.

## How to use the font maps (in general)

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
* `reimin-shingo-pr6`

Note that you have to run this **at the top-level of this repository** or move/symlink the font maps to a suitable place which the kpathsea library can find (e.g., under `$TEXMFLOCAL/fonts/map/dvipdfmx/`).

## Installing wtfontmaps

You can easily install wtfontmaps to your TEXMFLOCAL with Rake. Typically, root privileges are required.

```
$ sudo rake install
```

Conversely, to uninstall:

```
$ sudo rake uninstall
```

You don't have to install wtfontmaps to build sample documents. Just try

```
$ rake sample
```

## License

Files in this repository are distributed under [the MIT license](./LICENSE).

---

Takuto ASAKURA ([wtsnjp](https://twitter.com/wtsnjp))
