# Browserslist [![Build Status](https://travis-ci.org/ai/browserslist.svg)](https://travis-ci.org/ai/browserslist)

Get browsers versions that matches given criterias.
Useful for tools like [Autoprefixer].

You can select browsers by passing a string. This library will use Can I Use
data to return you a appropriate list of all versions.

For example, last version of each major browser and version, which is used more
that 5% in global usage statistics:

```js
browserslist('> 5%, last 1 version');
//=> ['safari 8', 'opera 26', 'ios_saf 8.1', 'ie_mob 11', 'ie 11', 'and_chr 39',
//    'firefox 33', 'firefox 32', 'chrome 39', 'chrome 38', 'chrome 37']
```

if you don't provide an argument, Browserslist will look for a `browserslist`
config file in current or parent directories.

If no config file is found, Browserslist will use default list:
`> 1%, last 2 versions, Firefox ESR, Opera 12.1`.

<a href="https://evilmartians.com/?utm_source=browserslist">
<img src="https://evilmartians.com/badges/sponsored-by-evil-martians.svg" alt="Sponsored by Evil Martians" width="236" height="54">
</a>

[Autoprefixer]: https://github.com/postcss/autoprefixer
[two-letter contry codes]: http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Officially_assigned_code_elements

## Queries

You can specify the browsers by queries (case insensitive):

* `last 2 versions`: the last 2 versions for each major browser.
* `last 2 Chrome versions`: the last versions of a specific browser.
* `> 5%`: versions selected by global usage statistics.
* `> 5% in US`: uses USA usage statistics. It accepts [two-letter contry codes].
* `Firefox > 20`: versions of Firefox newer than 20.
* `Firefox >= 20`: versions of Firefox newer than or equal to 20.
* `Firefox < 20`: versions of Firefox less than 20.
* `Firefox <= 20`: versions of Firefox less than or equal to 20.
* `Firefox ESR`: the latest [Firefox ESR] version.
* `iOS 7`: the browser version directly.

Blackberry and Android WebView will not be used in `last n versions`.
You should add them by name.

## Browsers

Names are case insensitive:

* `Android` for Android WebView.
* `BlackBerry` or `bb` for Blackberry browser.
* `Chrome` for Google Chrome.
* `Firefox` or `ff` for Mozilla Firefox.
* `Explorer` or `ie` for Internet Explorer.
* `iOS` or `ios_saf` for iOS Safari.
* `Opera` for Opera.
* `Safari` for desktop Safari.
* `OperaMobile` or `op_mob` for Opera Mobile.
* `OperaMini` or `op_mini` for Opera Mini.
* `ChromeAndroid` or `and_chr` for Chrome for Android
  (mostly same as common `Chrome`).
* `FirefoxAndroid` or `and_ff` for Firefox for Android.
* `ExplorerMobile` or `ie_mob` for Internet Explorer Mobile.


## Usage

```js
var browserslist = require('browserslist');

// Your CSS/JS build tool code
var process = function (css, opts) {
    var browsers = browserslist(opts.browsers, { path: opts.file });
    // Your code to add features for selected browsers
}
```

If list is missing, Browserslist will look for a config file.
You can provide a `path` option (that can be a file) to find config file
relatively to it.

Queries can be a string `"> 5%, last 1 version"`
or and array `[''> 5%', 'last 1 version']`.

## Config File

Browserslist’s config should has `browserslist` name and splits browsers queries
by new line. You can write comment after `#`:

```
# Browsers that we support

> 1%
Last 2 versions
IE 8 # sorry
```
