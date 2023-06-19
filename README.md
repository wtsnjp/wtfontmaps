# wtfontmaps

My personal Japanese font maps for dvipdfmx. The font maps are optimized for macOS + TeX Live + Morisawa passport.

You can use these settings freely for any purpose, but note that there is NO WARRANTY.

## Installing wtfontmaps

You can easily install wtfontmaps to your TEXMFLOCAL with Rake. The root privilege may be required.

```shell
rake install
```

Conversely, to uninstall:

```shell
rake uninstall
```

You don't have to install wtfontmaps to build sample documents. Just try

```shell
rake sample
```

## How to use the font maps (in general)

To check the current font settings,

```shell
kanji-config-updmap-sys status
```

To setup the font settings,

```shell
kanji-config-updmap-sys <map name>
```

where `<map name>` is one of the followings:

* `morisawa-pr6`
* `morisawa-pr6n`
* `ryumin-shingo-pr6`
* `ryumin-shingo-pr6n`
* `udreimin-udshingo-pr6`
* `udreimin-udshingo-pr6n`
* `reimin-shingo-pr6`
* `reimin-shingo-pr6n`

Note that the root privilege may be required.

## License

Files in this repository are distributed under [the MIT license](./LICENSE).

---

Takuto Asakura ([wtsnjp](https://twitter.com/wtsnjp))
