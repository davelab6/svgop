# svgop 

`svgop` (**SVG O**ptimizer **P**ipeable) is a standalone binary executable that combines the excellent [`svgo`](https://github.com/svg/svgo) Nodejs-based tool for optimizing SVG vector graphics files, and [`pdf.js`](https://github.com/mozilla/pdf.js), the PDF renderer written in JS. 

## Rationale

SVG files, especially exported from various editors, usually contain a lot of redundant and useless information such as editor metadata, comments, hidden elements, default or non-optimal values and other stuff that can be safely removed or converted without affecting SVG rendering result.

## What is `svgop`? 

While `svgo` requires a Nodejs environment to run, `svgop` is a standalone binary executable tool for **macOS** (64-bit) and **Windows** (x86 and x64). `svgop` accepts **SVG and PDF** in stdin and outputs an **optimized SVG** to stdout. 

It uses the default `svgo` [config](https://github.com/twardoch/svgop/blob/master/src/svgop.js). 

This repo contains a process to create `svgop` from `svgo` and `pdf.js` using the Nodejs [`pkg`](https://www.npmjs.com/package/pkg) compiler. 

Note: To make `pkg` work, a customized version of [`config.js`](https://github.com/twardoch/svgop/blob/master/src/lib/svgo/config.js) will replace `svgo`’s own [`config.js`](https://github.com/svg/svgo/blob/master/lib/svgo/config.js). The customized version will need to be updated manually from time to time. 

## Download

[**DOWNLOAD**](https://github.com/twardoch/svgop/releases/latest) the latest release for macOS (`svgop-macos.zip`), Windows 32-bit (`svgop-win32.zip`) or Windows 64-bit (`svgop-win64.zip`). 

## Usage 

- from `.pdf` to `.svg`

```bash
svgop < test.pdf > test.min.svg
```

- from `.svg` to `.svg`

```bash
svgop < test.svg > test.min.svg
```

- from `.svgz` to `.svg`:

```bash
gunzip -c test.svgz | svgop > test.min.svg
```

- from `.svg` to `.svgz`:

```bash
svgop < test.svg | gzip -cfq9 > test.min.svgz
```

## Building

Clone the repo on macOS, run `make`. The executables will be found in `./bin`. 

## License and Copyright

Portions of this software are licensed under the terms of the Apache 2 license. Portions of this software are licensed under the terms of the MIT license. Please consult [LICENSE](https://github.com/twardoch/svgop/blob/master/LICENSE).

- `svgop`: Copyright © 2017 Adam Twardoch
- `svgo`: Copyright © 2012–2017 Kir Belevich and Contributors
- `pdf.js`: Copyright © 2012-2017 Mozilla Foundation and Contributors
