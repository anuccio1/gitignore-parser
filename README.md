# Gitignore Parser

A very simple `.gitignore` parser for node.js.

[![Build Status](https://travis-ci.org/codemix/gitignore-parser.svg?branch=master)](https://travis-ci.org/codemix/gitignore-parser)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fanuccio1%2Fgitignore-parser.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fanuccio1%2Fgitignore-parser?ref=badge_shield)


## Installation

`npm install gitignore-parser`


## Usage

```js
var parser = require('gitignore-parser'),
    fs = require('fs');

var gitignore = parser.compile(fs.readFileSync('.gitignore', 'utf8'));

gitignore.accepts('LICENSE.md') === true;
gitignore.denies('LICENSE.md') === false;

gitignore.accepts('node_modules/mocha/bin') === false;
gitignore.denies('node_modules/mocha/bin') === true;


var files = [
  '.gitignore',
  '.travis.yml',
  'LICENSE.md',
  'README.md',
  'package.json',
  'lib/index.js',
  'test/index.js',
  'test/mocha.opts',
  'node_modules/mocha/bin/mocha',
  'node_modules/mocha/README.md'
];

// only files that are not gitignored
files.filter(gitignore.accepts);

// only files that *are* gitignored
files.filter(gitignore.denies);

```



[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fanuccio1%2Fgitignore-parser.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fanuccio1%2Fgitignore-parser?ref=badge_large)

### License

Apache 2, see [LICENSE.md](./LICENSE.md).