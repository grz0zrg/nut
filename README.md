# nut
---
**Minimalist build system for JavaScript app.**

This is a **minimalist build system** to write JS app. without hassles.

This program is written with the [Anubis language](https://fr.wikipedia.org/wiki/Anubis_(langage))

Could be adapted/extended to other ends easily.

It is basically a simple pre-processor producing a single debug and production ready file each time a file change in the app. src directory, it is recursive.

Files modification date are checked against the build files modification date, if one file appear to be more recent than the build files, the build system trigger itself.

You only need to pass the plain output file (either CSS or JS), Nut will look at an entry point file which will be the base of your applications,
in this file you can then use directives such as include as follow: `/*#include [FILENAME]*/`
Nut will read the entry point file sequentially, include the content of `[FILENAME]` if the directive is encountered
and output a single file application in a dist folder, CSS and JS is automatically detected from the file extension and a program such as a minifier will be called and output a production ready file as well.

Base requirement for web. applications with JS and CSS (basic setup):
 * `uglifyjs` and `csso` should be installed with Node/NPM `npm install uglifyjs csso`
 * The app. folder should contain a `js` and `css` folder
 * "js" folder should contain a file named `app_[APP_NAME].js` where `[APP_NAME]` is your application name
 * "css" folder should contain a file named `app_[APP_NAME].css` where `[APP_NAME]` is your application name
 * Call Nut in the app. root directory with `anbexec nut [APP_NAME].js`
 * Call Nut in the app. root directory with `anbexec nut [APP_NAME].css`
 * The debug and production ready files will be available in the `dist` folder as `[APP_NAME].js` `[APP_NAME].css` `[APP_NAME].min.js` `[APP_NAME].min.css`

Features:
 - Automatized background build by comparing changes between build files and files in the `js` and `css` folder every two seconds (recursive)
 - Produce debug and production ready files, minified & optimized CSS and JS output in a `dist` folder
 - Parse `/*#include [FILENAME]*/` directives to provide **KISS** modularity (only in the src root directory and specific directories like workers)
 - Fast & minimalist :)

This support sub-applications as well, just create as many entry point files as wanted.

Usage: `anbexec nut [output_filename].[js|css]`

---
by Julien Verneuil (grz0zrg) 2014/2017
