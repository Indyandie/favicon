# Favicon

[@mathiasbynens]: https://github.com/mathiasbynens
[@audreyfeldroy]: https://github.com/audreyfeldroy
[favicon-cheat-sheet]: https://github.com/audreyfeldroy/favicon-cheat-sheet

A fork (aberration) of the awesome [favicon-cheat-sheet] by [@audreyfeldroy].

## Favicon Support

All modern browser should use the `favicon.ico` at the root of the domain.

### IOS & Android (Optional)

1. Add `apple-touch-icon-180x180.png` and/or `apple-touch-icon-180x180-precomposed.png` files to the root of the domain, this should suffice for IOS.
2. Android may require the following.
   ```html
   <link rel="apple-touch-icon" href="/apple-touch-icon-180x180.png">
   <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-180x180-precomposed.png">
   ```

### Almost All Favicon (Obsessive)

1. Add largest to smallest apple-touch-icons to the root domain, and the `HTML` links [^3]:

   - `apple-touch-icon-192x192.png`
   - `apple-touch-icon-192x192-precomposed.png`
   - `apple-touch-icon-180x180.png`
   - `apple-touch-icon-180x180-precomposed.png`
   - `apple-touch-icon-152x152.png`
   - `apple-touch-icon-152x152-precomposed.png`
   - `apple-touch-icon-120x120.png`
   - `apple-touch-icon-120x120-precomposed.png`
   - `apple-touch-icon-76x76.png`
   - `apple-touch-icon-76x76-precomposed.png`
   - `apple-touch-icon-57x57.png`
   - `apple-touch-icon-57x57-precomposed.png`
   - `apple-touch-icon.png` (`180px`)
   - `apple-touch-icon-precomposed.png` (`180px`)

     ```html
     <link rel="apple-touch-icon-precomposed" sizes="192x192" href="/apple-touch-icon-192x192.png">
     <link rel="apple-touch-icon-precomposed" sizes="192x192" href="/apple-touch-icon-192x192-precomposed.png">
     <link rel="apple-touch-icon-precomposed" sizes="180x180" href="/apple-touch-icon-180x180.png">
     <link rel="apple-touch-icon-precomposed" sizes="180x180" href="/apple-touch-icon-180x180-precomposed.png">
     <link rel="apple-touch-icon-precomposed" sizes="152x152" href="/apple-touch-icon-152x152.png">
     <link rel="apple-touch-icon-precomposed" sizes="152x152" href="/apple-touch-icon-152x152-precomposed.png">
     <link rel="apple-touch-icon-precomposed" sizes="120x120" href="/apple-touch-icon-120x120.png">
     <link rel="apple-touch-icon-precomposed" sizes="120x120" href="/apple-touch-icon-120x120-precomposed.png">
     <link rel="apple-touch-icon-precomposed" sizes="76x76" href="/apple-touch-icon-76x76.png">
     <link rel="apple-touch-icon-precomposed" sizes="76x76" href="/apple-touch-icon-76x76-precomposed.png">
     <link rel="apple-touch-icon-precomposed" sizes="57x57" href="/apple-touch-icon-57x57.png">
     <link rel="apple-touch-icon-precomposed" sizes="57x57" href="/apple-touch-icon-57x57-precomposed.png">
     <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon.png">
     <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-precomposed.png">
     ```

2. Favicon Chrome for Android

   ```html
   <link rel="shortcut icon" sizes="196x196" href="/path/to/favicon-196.png">
   ```

## Image Files

### PNG

| Sizes   | Name            | Purpose                                                                  |
| ------- | --------------- | ------------------------------------------------------------------------ |
| 48x48   | favicon-48.png  | [Android Devices](https://en.wikipedia.org/wiki/Favicon#Android_devices) |
| 96x96   | favicon-96.png  | GoogleTV icon                                                            |
| 128x128 | favicon-128.png | Chrome Web Store icon                                                    |
| 192x192 | favicon-192.png | [Android Devices](https://en.wikipedia.org/wiki/Favicon#Android_devices) |
| 196x196 | favicon-196.png | Chrome for Android home screen icon                                      |

### ICO

An `ICO` file is a container for multiple `PNG` icons of different sizes. In `favicon.ico`, create at least these:


> Create your .ico out of optimized .png files.

| Sizes | Name                                                                    |
| ----- | ----------------------------------------------------------------------- |
| 16x16 | IE9 address bar, Pinned site Jump List/Toolbar/Overlay                  |
| 32x32 | New tab page in IE, taskbar button in Win 7+, Safari Read Later sidebar |
| 64x64 | Windows site icons [^4], Safari Reading List sidebar in HiDPI/Retina    |

### SVG

Pinned tabs in Safari 9+ use an SVG vector mask for the favicon instead of any other PNG/ICO/etc. favicons that may be present. Vector artwork in the SVG file should be black only (no shades of black or other colors) with a transparent background. Also, a fill color needs to be defined in the <link> tag - a hex value or color shorthand will work. Here's the markup for adding the icon:

```html
<link rel="mask-icon" href="icon.svg" color="#ff0000">
```

## Tools

- [OptiPNG](https://sourceforge.net/projects/optipng/)
- [ImageMagick](https://imagemagick.org/)

  ```shell
  magick convert favicon-16.png favicon-32.png favicon.ico
  ```

## Forcing a Favicon Refresh

Not normally needed. This is only for those frustrating times when you can't get your favicon to refresh, during development:

- Clear the browser cache on Windows (Ctrl+F5 or Ctrl+Shift+R) and on Mac (Command + Shift + R).
- Also close and reopen browser if IE.
- If still stuck, try opening new tab. Or see http://stackoverflow.com/questions/2208933/how-do-i-force-a-favicon-refresh
- Temporarily add explicit HTML markup and append a query string. Remove this when you're done:

  ```html
  <link rel="shortcut icon" href="http://www.yoursite.com/favicon.ico?v=2" />
  <link rel="icon" sizes="16x16 32x32" href="/favicon.ico?v=2">
  ```

For large versioned deployments, if all site visitors need their favicon force-refreshed in an extreme situation:

- Add explicit HTML markup (customize the sizes part) and put your version number in the filename.

```html
<link rel="shortcut icon" href="/favicon-v2.ico" />
<link rel="icon" sizes="16x16 32x32" href="/favicon-v2.ico">
```

## Contribute

Send a pull request...

## References

[^1]: http://mathiasbynens.be/notes/rel-shortcut-icon

[^2]: http://www.w3.org/TR/html5/links.html#rel-icon

[^3]: Adapted from http://mathiasbynens.be/notes/touch-icons

[^4]: No specifics given by MSDN.

[^5]: http://blog.morzproject.com/convert-multiple-png-images-into-a-single-icon-file/

- http://www.jonathantneal.com/blog/understand-the-favicon/
- https://en.wikipedia.org/wiki/Favicon.ico
- http://snook.ca/archives/design/making_a_good_favicon
- http://www.netmagazine.com/features/create-perfect-favicon
- http://www.ravelrumba.com/blog/android-apple-touch-icon/
