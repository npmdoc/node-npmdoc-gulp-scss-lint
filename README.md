# api documentation for  [gulp-scss-lint (v0.4.0)](http://github.com/juanfran/gulp-scss-lint)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-scss-lint.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-scss-lint) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-scss-lint.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-scss-lint)
#### Validate `.scss` files with `scss-lint`

[![NPM](https://nodei.co/npm/gulp-scss-lint.png?downloads=true)](https://www.npmjs.com/package/gulp-scss-lint)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-scss-lint/build/screenCapture.buildNpmdoc.browser.%2Fhome%2Ftravis%2Fbuild%2Fnpmdoc%2Fnode-npmdoc-gulp-scss-lint%2Ftmp%2Fbuild%2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-scss-lint/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-scss-lint/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-scss-lint/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Juanfran Alcántara"
    },
    "bugs": {
        "url": "https://github.com/juanfran/gulp-scss-lint/issues"
    },
    "dependencies": {
        "bluebird": "^3.3.5",
        "dargs": "~4.1.0",
        "event-stream": "~3.3.2",
        "gulp-util": "~3.0.7",
        "pretty-data": "^0.40.0",
        "shell-escape": "^0.2.0",
        "slash": "^1.0.0",
        "sync-exec": "~0.6.2",
        "vinyl": "^1.1.1",
        "vinyl-fs": "^2.4.3",
        "xml2js": "^0.4.16"
    },
    "description": "Validate '.scss' files with 'scss-lint'",
    "devDependencies": {
        "chai": "~3.5.0",
        "mocha": "~2.4.5",
        "proxyquire": "^1.7.4",
        "sinon": "^1.17.4",
        "vinyl-fs": "^2.4.3"
    },
    "directories": {},
    "dist": {
        "shasum": "4a3b688db5d2b113f44f6374681e46f39dc341e7",
        "tarball": "https://registry.npmjs.org/gulp-scss-lint/-/gulp-scss-lint-0.4.0.tgz"
    },
    "engines": {
        "node": ">= 0.10"
    },
    "gitHead": "fcd4e085362d48c42d80eb7bca5c1e9efb9fb7d5",
    "homepage": "http://github.com/juanfran/gulp-scss-lint",
    "keywords": [
        "gulpplugin",
        "scss-lint",
        "scsslint",
        "sass-lint",
        "scss",
        "lint",
        "gulp"
    ],
    "license": "MIT",
    "main": "./src/index.js",
    "maintainers": [
        {
            "name": "juanfran",
            "email": "juanfran.ag@gmail.com"
        }
    ],
    "name": "gulp-scss-lint",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/juanfran/gulp-scss-lint.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "0.4.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-scss-lint](#apidoc.module.gulp-scss-lint)
1.  [function <span class="apidocSignatureSpan">gulp-scss-lint.</span>defaultReporter (file)](#apidoc.element.gulp-scss-lint.defaultReporter)
1.  [function <span class="apidocSignatureSpan">gulp-scss-lint.</span>failReporter (severity)](#apidoc.element.gulp-scss-lint.failReporter)
1.  object <span class="apidocSignatureSpan">gulp-scss-lint.</span>checkstyle
1.  object <span class="apidocSignatureSpan">gulp-scss-lint.</span>reporters

#### [module gulp-scss-lint.checkstyle](#apidoc.module.gulp-scss-lint.checkstyle)
1.  [function <span class="apidocSignatureSpan">gulp-scss-lint.checkstyle.</span>toJSON (report, cb)](#apidoc.element.gulp-scss-lint.checkstyle.toJSON)

#### [module gulp-scss-lint.reporters](#apidoc.module.gulp-scss-lint.reporters)
1.  [function <span class="apidocSignatureSpan">gulp-scss-lint.reporters.</span>defaultReporter (file)](#apidoc.element.gulp-scss-lint.reporters.defaultReporter)
1.  [function <span class="apidocSignatureSpan">gulp-scss-lint.reporters.</span>failReporter (severity)](#apidoc.element.gulp-scss-lint.reporters.failReporter)



# <a name="apidoc.module.gulp-scss-lint"></a>[module gulp-scss-lint](#apidoc.module.gulp-scss-lint)

#### <a name="apidoc.element.gulp-scss-lint.defaultReporter"></a>[function <span class="apidocSignatureSpan">gulp-scss-lint.</span>defaultReporter (file)](#apidoc.element.gulp-scss-lint.defaultReporter)
- description and source-code
```javascript
defaultReporter = function (file) {
  if (!file.scsslint.success) {
    gutil.log(colors.cyan(file.scsslint.issues.length) + ' issues found in ' + colors.magenta(file.path));

    file.scsslint.issues.forEach(function (issue) {
      var severity = issue.severity === 'warning' ? colors.yellow(' [W] ') : colors.red(' [E] ');
      var linter = issue.linter ? (issue.linter + ': ') : '';
      var logMsg =
        colors.cyan(file.relative) + ':' + colors.magenta(issue.line) + severity + colors.green(linter) + issue.reason;

      gutil.log(logMsg);
    });
  }
}
```
- example usage
```shell
...
}

files[i].scsslint = lintResult;

if (options.customReport) {
  options.customReport(files[i], stream);
} else {
  reporters.defaultReporter(files[i]);
}

if (!options.filePipeOutput) {
  if (options.src) {
    stream.push(files[i]);
  } else {
    stream.emit('data', files[i]);
...
```

#### <a name="apidoc.element.gulp-scss-lint.failReporter"></a>[function <span class="apidocSignatureSpan">gulp-scss-lint.</span>failReporter (severity)](#apidoc.element.gulp-scss-lint.failReporter)
- description and source-code
```javascript
failReporter = function (severity) {
  return es.map(function(file, cb) {
    var error;

    if (!file.scsslint.success) {
      if (!severity || severity === 'E' && file.scsslint.errors > 0) {
        error = new gutil.PluginError('gulp-scss-lint', {
          message: 'ScssLint failed for: ' + file.relative,
          showStack: false
        });
      }
    }

    cb(error, file);
  });
}
```
- example usage
```shell
...

'''js
var scsslint = require('gulp-scss-lint');

gulp.task('scss-lint', function() {
  return gulp.src('/scss/*.scss')
    .pipe(scsslint())
    .pipe(scsslint.failReporter())
});
'''

if you just want 'failReporter' to fail just with errors pass the 'E' string

'''js
var scsslint = require('gulp-scss-lint');
...
```



# <a name="apidoc.module.gulp-scss-lint.checkstyle"></a>[module gulp-scss-lint.checkstyle](#apidoc.module.gulp-scss-lint.checkstyle)

#### <a name="apidoc.element.gulp-scss-lint.checkstyle.toJSON"></a>[function <span class="apidocSignatureSpan">gulp-scss-lint.checkstyle.</span>toJSON (report, cb)](#apidoc.element.gulp-scss-lint.checkstyle.toJSON)
- description and source-code
```javascript
toJSON = function (report, cb) {
  var obj = {};
  var xmlReport = pd.xml(report);
  var error = [];

  xml2js(xmlReport, function(err, report) {
    report.checkstyle.file = report.checkstyle.file || [];

    report.checkstyle.file.forEach(function(file) {
        obj[file.$.name] = [];

        file.error.forEach(function(error) {
          error.$.linter = error.$.source;
          error.$.reason = error.$.message;

          obj[file.$.name].push(error.$);
        });
    });

    cb([obj, xmlReport]);
  });
}
```
- example usage
```shell
...
        }
      } else if (error && error.code === 1 && report.length === 0) {
        reject('Error code ' + error.code + '\n' + error);
      } else  {
        if (options.format === 'JSON'){
          resolve([JSON.parse(report)]);
        } else {
          checkstyle.toJSON(report, resolve);
        }
      }
    });
  });
}

module.exports = function(filePaths, options) {
...
```



# <a name="apidoc.module.gulp-scss-lint.reporters"></a>[module gulp-scss-lint.reporters](#apidoc.module.gulp-scss-lint.reporters)

#### <a name="apidoc.element.gulp-scss-lint.reporters.defaultReporter"></a>[function <span class="apidocSignatureSpan">gulp-scss-lint.reporters.</span>defaultReporter (file)](#apidoc.element.gulp-scss-lint.reporters.defaultReporter)
- description and source-code
```javascript
defaultReporter = function (file) {
  if (!file.scsslint.success) {
    gutil.log(colors.cyan(file.scsslint.issues.length) + ' issues found in ' + colors.magenta(file.path));

    file.scsslint.issues.forEach(function (issue) {
      var severity = issue.severity === 'warning' ? colors.yellow(' [W] ') : colors.red(' [E] ');
      var linter = issue.linter ? (issue.linter + ': ') : '';
      var logMsg =
        colors.cyan(file.relative) + ':' + colors.magenta(issue.line) + severity + colors.green(linter) + issue.reason;

      gutil.log(logMsg);
    });
  }
}
```
- example usage
```shell
...
}

files[i].scsslint = lintResult;

if (options.customReport) {
  options.customReport(files[i], stream);
} else {
  reporters.defaultReporter(files[i]);
}

if (!options.filePipeOutput) {
  if (options.src) {
    stream.push(files[i]);
  } else {
    stream.emit('data', files[i]);
...
```

#### <a name="apidoc.element.gulp-scss-lint.reporters.failReporter"></a>[function <span class="apidocSignatureSpan">gulp-scss-lint.reporters.</span>failReporter (severity)](#apidoc.element.gulp-scss-lint.reporters.failReporter)
- description and source-code
```javascript
failReporter = function (severity) {
  return es.map(function(file, cb) {
    var error;

    if (!file.scsslint.success) {
      if (!severity || severity === 'E' && file.scsslint.errors > 0) {
        error = new gutil.PluginError('gulp-scss-lint', {
          message: 'ScssLint failed for: ' + file.relative,
          showStack: false
        });
      }
    }

    cb(error, file);
  });
}
```
- example usage
```shell
...

'''js
var scsslint = require('gulp-scss-lint');

gulp.task('scss-lint', function() {
  return gulp.src('/scss/*.scss')
    .pipe(scsslint())
    .pipe(scsslint.failReporter())
});
'''

if you just want 'failReporter' to fail just with errors pass the 'E' string

'''js
var scsslint = require('gulp-scss-lint');
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
