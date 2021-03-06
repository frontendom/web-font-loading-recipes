# web-font-loading-recipes

A bunch of demos for different web font loading strategies. Some of these are included on [A Comprehensive Guide to Font Loading Strategies](https://www.zachleat.com/web/comprehensive-webfonts/), some of them are more _experimental_.

Demos are hosted at https://www.zachleat.com/web-fonts/demos/

## Recommended Methods

As web fonts are a progressive enhancement and with increasing support for the CSS Font Loading API, we can look forward to a time in which we won’t need to inline a polyfill into the header (for even faster font loading). The simplified CSS Font Loading API recipes are the defaults, but polyfilled versions are included for broader browser support. In practice this means only the polyfilled versions will show web fonts in Internet Explorer and Edge web browsers (which do not have support for the CSS Font Loading API).

* [`font-display`](./font-display.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#font-display)
  * [Demo](https://www.zachleat.com/web-fonts/demos/font-display.html)** _(4 web fonts)_
* [`preload`](./preload.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#preload)
  * [Demo](https://www.zachleat.com/web-fonts/demos/preload.html)** _(4 web fonts—1 preloaded)_
* [FOUT with a Class](./fout-with-class.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#fout-class)
  * [Demo](https://www.zachleat.com/web-fonts/demos/fout-with-class.html) _(4 web fonts)_
  * or [using a polyfill](./fout-with-class-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/fout-with-class-polyfill.html) _(4 web fonts)_
* [FOFT](./foft.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#foft)
  * [Demo](https://www.zachleat.com/web-fonts/demos/foft.html) _(5 web fonts, two are the same—but only loaded once)_
  * or [using a polyfill](./foft-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/foft-polyfill.html) _(4 web fonts)_
* [FOFT using only `font-display`](./font-display-mix.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/font-display-mix.html) _(4 web fonts—1 `swap` / 3 `optional`)_
* [Critical FOFT](./critical-foft.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#critical-foft)
  * [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft.html) _(5 web fonts—1 subset)_
  * or [using a polyfill](./critical-foft-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-polyfill.html) _(4 web fonts)_
* [Critical FOFT with Data URI](critical-foft-data-uri.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#critical-foft-data-uri)
  * [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-data-uri.html) _(5 web fonts—1 subset inline Data URI)_
  * or [using a polyfill](./critical-foft-data-uri-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-data-uri-polyfill.html) _(5 web fonts—1 subset inline Data URI)_
* [Critical FOFT with `preload`](./critical-foft-preload.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#critical-foft-preload)
  * [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-preload.html) _(5 web fonts—1 subset)_
  * or [using a polyfill](./critical-foft-preload-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-preload-polyfill.html) _(5 web fonts—1 subset)_

## Experiments in Progress

You’ll probably see blog posts on these at some point.

* [FOUT metric matching with a Variable Font](./variablefont-fout-test.html)
  * Reduction in FOUT reflow (reduce text movement on web font render)
  * Related: [Font style matcher](https://meowni.ca/font-style-matcher/) from @notwaldorf
* Emulate `font-display: optional` with JS (the [eBay method](http://www.ebaytechblog.com/2017/09/21/ebays-font-loading-strategy/))
  * Notable in that it lazy loads the font loading polyfill only if the CSS Font Loading API is not supported
* (To be named) Any recommended non-polyfilled recipe above with one slight variation: it uses the eBay method if the CSS Font Loading API is not supported (in practice this means `font-display: optional` only on IE/Edge). This is what I’m currently doing on [zachleat.com](https://www.zachleat.com/web/).
* FOUT without a class
  * Doesn’t require any modification of the CSS, injects the web fonts using JS programmatically (the Asynchronous Data URI method below also does this). Documented in the [Webfont Handbook from @bramstein](https://abookapart.com/products/webfont-handbook).

## Not Recommended but included for Posterity

* [System fonts](./dont.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#abstain)
  * [Demo](https://www.zachleat.com/web-fonts/demos/dont.html) _(0 web fonts)_
* [Unceremonious Web Fonts](./unceremonious-font-face.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#font-face)
  * [Demo](https://www.zachleat.com/web-fonts/demos/unceremonious-font-face.html)** _(4 web fonts)_
* [Unceremonious Faux Web Fonts](./unceremonious-faux-font-face.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/unceremonious-faux-font-face.html)** _(1 web font)_: Bold and italic variants are rendered using [font-synthesis](https://www.zachleat.com/web/webfont-glossary/#font-synthesis)
* [Unceremonious Web Fonts, WOFF2 Only (Cutting the Mustard)](./unceremonious-font-face-woff2-only.html)
  * Old browsers [used to render FOIT without a timeout](https://www.zachleat.com/web/fout-foit-history/), which in practice made web fonts a single point of failure. Using WOFF2 only cuts the mustard to modern browsers that have a three second FOIT timeout for web fonts. Three seconds is still way too long for me to implement this in production, but it’s worth noting.
  * [Demo](https://www.zachleat.com/web-fonts/demos/unceremonious-font-face-woff2-only.html)** _(4 web fonts)_

### Deprecated Methods

* [Inline Data URI](./inline-data-uri.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#inline-data-uri)
  * [Demo](https://www.zachleat.com/web-fonts/demos/inline-data-uri.html) _(4 web fonts)_
* [Asynchronous Data URI](./async-data-uri.html)
  * [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#async-data-uri)
  * [Demo](https://www.zachleat.com/web-fonts/demos/async-data-uri.html) _(4 web fonts)_
* Anything that injects a new `<style>` with `@font-face` blocks inside. Really bad repaint cost—seriously, don’t do this.

### Failed Experiments

* [`@supports` and `font-display`](failed-supports.html)
  * Reasons for trying:
    * might be nice to only use web fonts if you can FOUT with `font-display`
    * might be nice to have FOUT with a class if `font-display` not supported (and work well without JS dependencies)
  * **Failed**: `@supports` doesn’t work with font-face descriptors.
  * [Demo](https://www.zachleat.com/web-fonts/demos/failed-supports.html)

---

** Take note that these methods will FOUT in Internet Explorer and Edge by taking advantage of their default font loading behavior.
