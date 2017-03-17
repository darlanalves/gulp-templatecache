gulp-templatecache
============

Gulp plugin to join AngularJS templates in one JavaScript template cache

### Similar plugin: [gulp-angular-templatecache](https://github.com/miickel/gulp-angular-templatecache)

## Information

## Install

Install with [npm](https://npmjs.org/package/gulp-templatecache)


`npm install --save-dev gulp-templatecache`

## Usage

```javascript

gulp.task('templates', function() {
    var templateCache = require('gulp-templatecache');
    var options = {
        output: 'templates.js',
        stripFromPath: '/src/templates',
        prependToPath: '/app',
        moduleName: 'app.templates',
        minify: true
    }

  gulp.src('src/templates/**/*.html')
    .pipe(templateCache(options))
    .pipe(gulp.dest('./dist/'))
    
  // the result is a file (dist/templates.js) that has all templates 
  // converted to JS strings and injected into $templateCache of a 
  // module called 'app.templates', for all HTML files found inside
  // src/templates. A file under src/templates/foo.html will be injected
  // as /app/foo.html into template cache

```

## Overview

This plugin converts HTML templates to JavaScript (HTML escaped as JS) and put them inside a `module.run()` block to inject them right into $templateCache

## API

### templateCache(options)

## Options

#### output
Type: `String`

The output filename

#### moduleName
Type: `String`

The AngularJS module name to use. If the module does not exists yet, it will create one.

#### stripFromPath

Type: `String`
Default: ``

Path fragment to remove from template path (from beginning of all template paths)

#### prependToPath

Type: `String`
Default: ``

Path fragment to insert at beginning of all template paths

#### minify

Type: `Object|Boolean`
Default: `false`

Configs to pass on [html-minifier](https://github.com/kangax/html-minifier). 
If ommitted or `false`, the HTML is kept untouched

## LICENSE

[MIT License](http://en.wikipedia.org/wiki/MIT_License)

[npm-url]: https://npmjs.org/package/gulp-templateCache