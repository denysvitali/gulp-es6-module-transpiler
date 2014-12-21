# gulp-es6-module-transpiler

[Gulp](https://github.com/gulpjs/gulp) plugin for the [ES6 Module Transpiler](https://github.com/esnext/es6-module-transpiler)

[![NPM][npm]](https://npmjs.org/package/gulp-es6-module-transpiler)
[![Dependency Status][dependencies]](https://david-dm.org/rkusa/gulp-es6-module-transpiler)

```js
npm install gulp-es6-module-transpiler
```

## Usage

### Basic usage

```js
var transpile  = require('gulp-es6-module-transpiler');

gulp.task('build', function() {
    return gulp.src('src/**/*.js')
        .pipe(transpile({
            formatter: 'bundle'
        }))
        .pipe(gulp.dest('lib'));
})
```

### With source maps

```js
var sourcemaps = require('gulp-sourcemaps');
var transpile  = require('gulp-es6-module-transpiler');

gulp.task('build', function() {
    return gulp.src('src/**/*.js')
        .pipe(sourcemaps.init())
        .pipe(transpile({
            formatter: 'bundle'
        }))
        .pipe(sourcemaps.write('./'))
        .pipe(gulp.dest('lib'));
 })
 ```


### Options

```formatter``` *```String|Formatter|Formatter constructor```* *[optional]*

Name of built-in formatter, formatter instance of formatter constructor function. Controls the output format of transpiler scripts. All built-in formatters are available as ```formatters``` property of required module ```require('gulp-es6-module-transpiler').formatters```.

Defaults to [es6-module-transpiler](https://github.com/esnext/es6-module-transpiler) default formatter.

```basePath``` *```String```* *[optional]*

All module names will be resolved and named relatively to this path.

Defaults to ```process.cwd()```.

```importPaths``` *```Array<String>```* *[optional]*

Array of path that will be used to resolve modules.

Defaults to ```[ options.basePath ]```.

```moduleName``` *```String```* *[optional]*

Explicit name of exported module.

If there is only one module being transpiled, program names the exported module by the first and only module being transpiled. If there were multiple modules registered (multiple sources piped in) program first looks for this option, then, if not set, names the module ```bundle```.

```sourceMaps``` *```Boolean```* *[optional]*

If set to ```false```, sourceMappingURL is not appended to transpiled files and source maps are not applied. Defaults to ```true```.


## MIT License

Copyright (c) 2014 Markus Ast

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

[npm]: http://img.shields.io/npm/v/gulp-es6mt.svg?style=flat-square
[dependencies]: http://img.shields.io/david/rkusa/gulp-es6mt.svg?style=flat-square
