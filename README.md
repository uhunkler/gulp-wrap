# gulp-wrap [![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Dependency Status][depstat-image]][depstat-url]

> A gulp plugin to wrap the stream contents with a lodash template. [gulp](https://github.com/gulpjs/gulp)

## Usage

First, install `gulp-wrap` as a development dependency:

```shell
npm install --save-dev gulp-wrap
```

Then, add it to your `gulpfile.js`:

**Wrap the contents with an inline template:**

```javascript
var wrap = require("gulp-wrap");

gulp.src("./src/*.json")
	.pipe(wrap('angular.module(\'text\', []).value(<%= contents %>);'))
	.pipe(gulp.dest("./dist"));
```

**Wrap the contents with a template from file:**

```javascript
var wrap = require("gulp-wrap");

gulp.src("./src/*.json")
	.pipe(wrap({ src: 'path/to/template.txt'}))
	.pipe(gulp.dest("./dist"));
```

**Provide additional data and options for template processing:**

```javascript
var wrap = require("gulp-wrap");

gulp.src("./src/*.json")
	.pipe(wrap('BEFORE <%= data.contents %> <%= data.someVar %> AFTER', { someVar: 'someVal'}, { variable: 'data' }))
	.pipe(gulp.dest("./dist"));
```

## API

### wrap(template\[,data\]\[,options\])

#### template
Type: `String` or `Object

The template to used. When a `String` then it will be used as the template. When an `Object` then the template will be loaded from file.

#### template.src
Type: `String`

The file location of the template.

#### data
Type: `Object`

The data object that is passed on to the [lodash](http://lodash.com/docs#template) template call.

#### options
Type: `Object`

The options object that is passed on to the [lodash](http://lodash.com/docs#template) template call.

## License

[MIT License](http://en.wikipedia.org/wiki/MIT_License)

[npm-url]: https://npmjs.org/package/gulp-wrap
[npm-image]: https://badge.fury.io/js/gulp-wrap.png

[travis-url]: http://travis-ci.org/adamayres/gulp-wrap
[travis-image]: https://secure.travis-ci.org/adamayres/gulp-wrap.png?branch=master

[depstat-url]: https://david-dm.org/adamayres/gulp-wrap
[depstat-image]: https://david-dm.org/adamayres/gulp-wrap.png