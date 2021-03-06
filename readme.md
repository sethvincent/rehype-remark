# rehype-remark [![Build Status][travis-badge]][travis] [![Coverage Status][codecov-badge]][codecov]

Bridge / mutate from [**rehype**][rehype] to [**remark**][remark].

Tiny wrapper around [`hdast-util-to-mdast`][to-mdast].

## Installation

[npm][npm-install]:

```bash
npm install rehype-remark
```

## Usage

Say our `example.js` looks as follows:

```js
var unified = require('unified');
var parse = require('rehype-parse');
var rehype2remark = require('rehype-remark');
var stringify = require('remark-stringify');

process.stdin
  .pipe(unified())
  .use(parse)
  .use(rehype2remark)
  .use(stringify)
  .pipe(process.stdout);
```

Now, when running the following in a terminal (`2>/dev/null` is just to
silence Curl’s debugging output):

```sh
curl https://example.com 2>/dev/null | node example.js
```

**stdout**(4) yields:

```markdown
# Example Domain

This domain is established to be used for illustrative examples in documents. You may use this domain in examples without prior coordination or asking for permission.

[More information...](http://www.iana.org/domains/example)
```

## API

### `origin.use(rehype2remark[, destination])`

Either bridge or mutate from [**rehype**][rehype] ([HAST][]) to
[**remark**][remark] ([MDAST][]).

###### `destination`

If given ([`Unified`][processor]), runs the destination processor
with the new MDAST tree, then, after running discards that tree and
continues on running the origin processor with the original tree
([bridge-mode][bridge]).  Otherwise, passes the tree to further
plug-ins (mutate-mode).

## License

[MIT][license] © [Titus Wormer][author]

<!-- Definitions -->

[travis-badge]: https://img.shields.io/travis/wooorm/rehype-remark.svg

[travis]: https://travis-ci.org/wooorm/rehype-remark

[codecov-badge]: https://img.shields.io/codecov/c/github/wooorm/rehype-remark.svg

[codecov]: https://codecov.io/github/wooorm/rehype-remark

[npm-install]: https://docs.npmjs.com/cli/install

[license]: LICENSE

[author]: http://wooorm.com

[mdast]: https://github.com/syntax-tree/mdast

[hast]: https://github.com/syntax-tree/hast

[remark]: https://github.com/wooorm/remark

[rehype]: https://github.com/wooorm/rehype

[processor]: https://github.com/wooorm/unified#processor

[bridge]: https://github.com/wooorm/unified#bridge

[to-mdast]: https://github.com/syntax-tree/hast-util-to-mdast
