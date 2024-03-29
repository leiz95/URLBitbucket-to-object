# URLBitbucket-to-object

A node module that extracts useful properties like `user` and
`repo` from various flavors of bitbucket URLs.

There's also a GitHub equivalent to this library: [urlgithub-to-object](https://github.com/leiz95/URLgithub-to-object).

## Installation

```sh
npm install urlbitbucket-to-object --save
```

## Usage

Pass whatever flavor of bitbucket URL you like:

```js
var bb = require('urlbitbucket-to-object')

bb('example/business')
bb('bitbucket:example/business')
bb('https://bitbucket.org/example/business')
bb('https://bitbucket.org/example/business.git')
bb('http://bitbucket.org/example/business')
bb('git://bitbucket.org/example/business.git')
```

Here's what you'll get:

```js
{
  user: 'example',
  repo: 'business',
  branch: 'master',
  https_url: 'https://bitbucket.org/example/business',
  tarball_url: 'https://bitbucket.org/example/business/get/master.tar.gz'
  travis_url: 'https://travis-ci.org/example/business',
}
```

The shorthand format lets you specify a branch:

```js
  bb('example/business#nachos')
{
  user: 'example',
  repo: 'business',
  branch: 'nachos',
  https_url: 'https://bitbucket.org/example/business/tree/nachos',
  tarball_url: 'https://bitbucket.org/example/business/get/nachos.tar.gz'
  travis_url: 'https://travis-ci.org/example/business',
}
```

If you provide a non-bitbucket URL or a falsy value, you'll get `null`.

## Test

```sh
npm install
npm test
```

## License

MIT
