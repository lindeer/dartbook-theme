
`dartbook-theme` is a web development tool for dartbook theme.

## How to

Using dartbook, it is easy to custom your book website, just create create '\_layouts' for your book's pages' layout, '\_i18n' for different i18n string resources and '\_assets' for appearance. Nearly everything keeps same with gitbook's style.

Dartbook's theme based on [materialize](https://github.com/materializecss/materialize/) css framework. If you would like to custom your own theme style, just did as follow steps:

  0. `git clone https://github.com/lindeer/dartbook-theme && cd dartbook-theme`.
  1. Download latest materialize source package, e.g. [materialize-src-v1.2.0.zip](https://github.com/materializecss/materialize/releases/download/1.2.0/materialize-src-v1.2.0.zip). Extract it and move its sass directory to `./web`. We need materialize's components to build our own styles.
  2. Install dart sass command line tool: `dart pub global activate webdev sass`, of course, make sure your envrionment variables include `~/.pub-cache/bin`: `export PATH=$PATH:~/.pub-cache/bin`.
  3. `sass web/styles.scss web/styles.css`, and then run `webdev serve`.
  4. Open `http://127.0.0.1:8080` in your browser, and start to modify something.
  5. `git clone https://github.com/lindeer/dartbook-theme-default` and export its path as `$assetRoot`.
  6. `./web/main.dart` would finally compile to `dartbook.js`, its main functionality is to show glossary tooltips and bind events for them. `materialize.js` is entirely copied as dartbook's assets. `build.sh` is a helper script for file copy and rename, run it when you finally finished theme developing. The final material　produced by web (`theme/build/*.css,*.js`) would be applied into dartbook resources (`$assetRoot/_assets`).
  7. Apply your developping theme. `dartbook serve /your/book/project/path --theme $assetRoot`.
  8. Publish your finished theme. In the directory `$assetRoot`, commit your changes and change the package name to `dartbook_theme_xxx`, what ever you like. Do not forget to change the theme name of ci files in `/your/book/project/path`:
```diff
-  - dart pub global activate dartbook_theme_default
+  - dart pub global activate dartbook_theme_xxx
```
