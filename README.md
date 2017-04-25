# nut
---
**Minimalist build system for JavaScript app.**

This is a **minimalist build system** to write JS app. without hassles.

This program is written with the [Anubis language](https://fr.wikipedia.org/wiki/Anubis_(langage))

It is basically a simple pre-processor producing as many debug and production ready file as needed each time a file change in the app. src directory, it is recursive.

Files modification date are checked against the build files modification date, if one file appear to be more recent than the build files, the build system trigger itself.

You only need to pass the plain (non-production) output file (either CSS or JS) or a list of plain output file, Nut will look at one or multiple entry point files which start with "app_", they will be the base of your applications, in these files you can then use directives such as include as follow: `/*#include [FILENAME]*/` Nut will read the entry point file sequentially, include the content of `[FILENAME]` if the directive is encountered (and will seek the include directive in the included files as well) and output a single file application in a dist folder, CSS and JS is automatically detected from the file extension and a program such as a minifier will be called and output a production ready file as well.

It is essential to start Nut in the application root directory, a folder named `dist` should be there.

Base example for web. applications with JS and CSS (basic setup):
 * `uglifyjs` and `csso` should be installed with Node/NPM `npm install uglifyjs csso`
 * The app. folder should contain a `js` and `css` folder
 * "js" folder should contain a file named `app_[APP_NAME].js` where `[APP_NAME]` is your application name
 * "css" folder should contain a file named `app_[APP_NAME].css` where `[APP_NAME]` is your application name
 * Call Nut in the app. root directory with `anbexec nut [APP_NAME].js [APP_NAME].css`
 * The debug and production ready files will be available in the `dist` folder as `[APP_NAME].js` `[APP_NAME].css` `[APP_NAME].min.js` `[APP_NAME].min.css`

Features:
 - Automatized background build by comparing changes between build files and files in the `js` and `css` folder every two seconds (recursive)
 - Produce debug and production ready files, minified & optimized CSS and JS output in a `dist` folder
 - Parse `/*#include [FILENAME]*/` directives to provide **KISS** modularity
 - Relatively fast & minimalist :)

Recommendation: Only use the include directive in the entry point file for better clarity (or at most in files of the root src directory maybe), abusing the include directive can be fun but at the expense of clarity... :)

Not restricted to a single output, just create as many entry point files as wanted and pass a list of output files as argument.

Usage: `anbexec nut [output_filename].[js|css] ...`

---
by Julien Verneuil (grz0zrg) 2014/2017
