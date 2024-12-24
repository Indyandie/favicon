# Favicon

[@mathiasbynens]: https://github.com/mathiasbynens
[@audreyfeldroy]: https://github.com/audreyfeldroy
[favicon-cheat-sheet]: https://github.com/audreyfeldroy/favicon-cheat-sheet

An fork (aberration) of the awesome [favicon-cheat-sheet] by [@audreyfeldroy].

## The HTML

### Basics

For the main favicon itself, it's best for cross-browser compatibility not to
use any HTML. Just name the file `favicon.ico` and place it in the root of your
domain. [^1], [^2]

This works in every desktop browser/version all the way back to IE6, except for SeaMonkey. [^1]

#### Optional But Encouraged

You probably also want the following:

1. Touch icon for iOS 2.0+ and Android 2.1+:

   ```html
   <link rel="apple-touch-icon-precomposed" href="path/to/favicon-180.png">
   ```

## Very Optional, for the Obsessive

If you're obsessive, you want all this too:

1. Largest to smallest apple-touch-icons [^3]:

   ```html
   <!-- For Iphone 6 plus running iOS 8: -->
   <link rel="apple-touch-icon-precomposed" sizes="180x180" href="/path/to/favicon-180.png">

   <!-- For iPad with high-resolution Retina display running iOS ≥ 7: -->
   <link rel="apple-touch-icon-precomposed" sizes="152x152" href="/path/to/favicon-152.png">

   <!-- For iPad with high-resolution Retina display running iOS ≤ 6: -->
   <link rel="apple-touch-icon-precomposed" sizes="144x144" href="/path/to/favicon-144.png">

   <!-- For iPhone with high-resolution Retina display running iOS ≥ 7: -->
   <link rel="apple-touch-icon-precomposed" sizes="120x120" href="/path/to/favicon-120.png">

   <!-- For iPhone with high-resolution Retina display running iOS ≤ 6: -->
   <link rel="apple-touch-icon-precomposed" sizes="114x114" href="/path/to/favicon-114.png">

   <!-- For first- and second-generation iPad: -->
   <link rel="apple-touch-icon-precomposed" sizes="76x76" href="/path/to/favicon-76.png">

   <!-- For non-Retina iPhone, iPod Touch, and Android 2.1+ devices: -->
   <link rel="apple-touch-icon-precomposed" href="/path/to/favicon-57.png">
   ```

2. Favicons targeted to any additional png sizes that you add that aren't covered above:

   ```html
   <link rel="icon" href="/path/to/favicon-32.png" sizes="32x32">
   ```

3. Favicon Chrome for Android

   ```html
   <link rel="shortcut icon" sizes="196x196" href="/path/to/favicon-196.png">
   ```

## The Images

Create at least this:

| Sizes         | Name        | Purpose                                                                 |
| ------------- | ----------- | ----------------------------------------------------------------------- |
| 16x16 & 32x32 | favicon.ico | Default required by IE. Chrome and Safari may pick ico over png, sadly. |

More about favicon.ico below. Yes, it's 1 file with multiple sizes.

If you also sort of care about iOS and Android but are lazy:

| Sizes   | Name            | Purpose                                                   |
| ------- | --------------- | --------------------------------------------------------- |
| 180x180 | favicon-180.png | General use iOS/Android icon, auto-downscaled by devices. |

But keep in mind that icons with complex detail often don't downscale well.
Often you have to tweak subtle design details for smaller sizes.

If you're obsessive, create these too:

| Sizes   | Name            | Purpose                                                              |
| ------- | --------------- | -------------------------------------------------------------------- |
| 32x32   | favicon-32.png  | Certain old but not too old Chrome versions mishandle ico            |
| 57x57   | favicon-57.png  | Standard iOS home screen (iPod Touch, iPhone first generation to 3G) |
| 76x76   | favicon-76.png  | iPad home screen icon                                                |
| 96x96   | favicon-96.png  | GoogleTV icon                                                        |
| 120x120 | favicon-120.png | iPhone retina touch icon (Change for iOS 7: up from 114x114)         |
| 128x128 | favicon-128.png | Chrome Web Store icon                                                |
| 144x144 | favicon-144.png | IE10 Metro tile for pinned site                                      |
| 152x152 | favicon-152.png | iPad retina touch icon (Change for iOS 7: up from 144x144)           |
| 180x180 | favicon-180.png | iPhone 6 plus                                                        |
| 196x196 | favicon-196.png | Chrome for Android home screen icon                                  |

## ICO File

An .ico file is a container for multiple .bmp or .png icons of different sizes. In favicon.ico, create at least these:

| Sizes | Name                                                                    |
| ----- | ----------------------------------------------------------------------- |
| 16x16 | IE9 address bar, Pinned site Jump List/Toolbar/Overlay                  |
| 32x32 | New tab page in IE, taskbar button in Win 7+, Safari Read Later sidebar |
| 48x48 | Windows site icons [^4]                                                 |

If you're obsessive and don't mind 1-3kb extra size, also include these sizes in your .ico:

| Sizes | Name                                                                 |
| ----- | -------------------------------------------------------------------- |
| 24x24 | IE9 Pinned site browser UI                                           |
| 64x64 | Windows site icons [^4], Safari Reading List sidebar in HiDPI/Retina |

Create your .ico out of optimized .png files.

TODO: get confirmation that IE9+ supports .ico files that contain .png files (issue `#9`_)

.. _`#9`: https://github.com/audreyr/favicon-cheat-sheet/issues/9

## SVG File

Pinned tabs in Safari 9+ use an SVG vector mask for the favicon instead of any other PNG/ICO/etc. favicons that may be present. Vector artwork in the SVG file should be black only (no shades of black or other colors) with a transparent background. Also, a fill color needs to be defined in the <link> tag - a hex value or color shorthand will work. Here's the markup for adding the icon:

```html
<link rel="mask-icon" href="icon.svg" color="#ff0000">
```

## Tools

- [OptiPNG](https://sourceforge.net/projects/optipng/)
- [ImageMagick](https://imagemagick.org/)

  ```shell
  convert favicon-16.png favicon-32.png favicon.ico
  ```

## Forcing a Favicon Refresh

Not normally needed. This is only for those frustrating times when you can't get your favicon to refresh, during development:

- Clear the browser cache on Windows (Ctrl+F5 or Ctrl+Shift+R) and on Mac (Command + Shift + R).
- Also close and reopen browser if IE.
- If still stuck, try opening new tab. Or see http://stackoverflow.com/questions/2208933/how-do-i-force-a-favicon-refresh
- Temporarily add explicit HTML markup and append a query string. Remove
  this when you're done:

```html
<link rel="shortcut icon" href="http://www.yoursite.com/favicon.ico?v=2" />
<link rel="icon" sizes="16x16 32x32" href="/favicon.ico?v=2">
```

For large versioned deployments, if all site visitors need their favicon force-refreshed in an extreme situation:

- Add explicit HTML markup (customize the sizes part) and put your version
  number in the filename.

```html
<link rel="shortcut icon" href="/favicon-v2.ico" />
<link rel="icon" sizes="16x16 32x32" href="/favicon-v2.ico">
```

TODO: find edge cases where this markup doesn't work (issue `#3`_).

.. _`#3`: https://github.com/audreyr/favicon-cheat-sheet/issues/3

## FAQ

**What about having both a default root favicon.ico and favicon.png?**
I think it's actually better to provide only `favicon.ico` and not `favicon.png`, because:

- An `.ico` is a container for multiple `.bmp` or `.png` files. If you specify 1 default `favicon.png`, and if that `favicon.png` overrides the `favicon.ico`, you are giving up control over how the favicon looks at different resolutions and allowing the browser to do all resizing. For example, you might want the 64x64 version to contain text and the 16x16 version to not display the text at all, since at 16x16 it would be unreadable anyway.
- There is no `favicon.png` in the HTML5 specification, just `/favicon.ico`. From http://www.w3.org/TR/html5/links.html#rel-icon:
  - 'In the absence of a link with the icon keyword, for Documents obtained over HTTP or HTTPS, user agents may instead attempt to fetch and use an icon with the absolute URL obtained by resolving the URL "/favicon.ico" against the document's address, as if the page had declared that icon using the icon keyword.'

More about this in http://stackoverflow.com/questions/1344122/favicon-png-vs-favicon-ico-why-should-i-use-pngs-instead-of-icos/1344379#1344379 (Note: the text in the chosen answer about alpha transparency is incorrect. See the 2nd answer.)

**Is it true that favicons should be in the site root?**
No, that's only if you don't explicitly specify the browser/device-specific
`<link>` tags with a favicon path. See https://en.wikipedia.org/wiki/Favicon.ico.

If you don't have favicon.ico in the root consider adding one, or returning a HTTP 204 instead.
Many tools and services e.g. bookmarking sites, feed readers, web crawlers etc., request a
favicon.ico from the site root, and so receive a HTTP 404 if it's not present. In the worst
case some frameworks will return a custom error page which is likely to be many times larger
than the missing favicon.

**Is it true that the png has to be named favicon.png?**
No, this has never been true as far as I can tell from my obsessive research.

**Is it true that the ico has to be named favicon.ico?**
If you don't explicitly specify its `<link>` tag, yes. Explicitness is best,
so we both name it `favicon.ico` and explicitly specify the `<link>` tag.

**Why not prefix with "apple-touch-icon"?**
If you don't specify `<link>` tags, iOS looks for files prefixed with
`apple-touch-icon` or `apple-touch-icon-precomposed`. Many (e.g. HTML5
Boilerplate) rely on this assumption, but:

- Explicitly specifying `<link>` tags is clearer and supported by Apple.
- Not hard-coding names as `apple-touch-icon` clears up confusion as to whether
  the same icons can be reused for other purposes as-is, e.g. reusing
  favicon-144.png for Windows pinned site.

**Why use iOS precomposed icons?**

- iOS non-precomposed icons add rounded corners, drop shadow, and reflective
  shine. Sounds great in theory, but in practice the results can be very
  frustrating, especially to designers.
- Non-precomposed icons don't work with Android 2.1.

**Why absolute paths?**
Some Firefox versions require absolute paths. Since all browsers support them,
it's the simplest choice.

**Why not append a query string to force-refresh for all visitors?**
Some proxies and load balancers can fail to read query strings in edge cases.

## Contribute!

Send pull requests if you have anything to add/change, providing citations and justification. I'd love to see this improve.

## References

[^1]: http://mathiasbynens.be/notes/rel-shortcut-icon

[^2]: http://www.w3.org/TR/html5/links.html#rel-icon

[^3]: Adapted from http://mathiasbynens.be/notes/touch-icons

[^4]: No specifics given by MSDN.

[^5]: http://blog.morzproject.com/convert-multiple-png-images-into-a-single-icon-file/

- http://mathiasbynens.be/notes/rel-shortcut-icon <-- special thanks [@mathiasbynens]
- http://mathiasbynens.be/notes/touch-icons <-- special thanks [@mathiasbynens]
- http://www.jonathantneal.com/blog/understand-the-favicon/
- https://en.wikipedia.org/wiki/Favicon.ico
- http://snook.ca/archives/design/making_a_good_favicon
- http://www.netmagazine.com/features/create-perfect-favicon
- http://www.ravelrumba.com/blog/android-apple-touch-icon/
- http://msdn.microsoft.com/en-us/library/ie/gg491740(v=vs.85).aspx
