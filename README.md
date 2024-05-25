# @diotoborg/velit-nulla <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES spec-compliant `Array.prototype.join` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.es/ecma262/#sec-array.prototype.concat).

Because `Array.prototype.join` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var join = require('@diotoborg/velit-nulla');
var assert = require('assert');

var a = [1, 1, 1];
assert.deepEqual(join(a, 'x'), '1x1x1');
```

```js
var join = require('@diotoborg/velit-nulla');
var assert = require('assert');
/* when Array#join is not present */
delete Array.prototype.join;
var shimmed = join.shim();
assert.equal(shimmed, join.getPolyfill());
assert.equal(shimmed, Array.prototype.join);
assert.deepEqual([1, 2, 3].join('x'), join([1, 2, 3], 'x'));
```

```js
var join = require('@diotoborg/velit-nulla');
var assert = require('assert');
/* when Array#join is present */
var shimmed = join.shim();
assert.equal(shimmed, Array.prototype.join);
assert.deepEqual([1, 2, 3].join(), join([1, 2, 3]));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@diotoborg/velit-nulla
[npm-version-svg]: https://versionbadg.es/diotoborg/velit-nulla.svg
[deps-svg]: https://david-dm.org/diotoborg/velit-nulla.svg
[deps-url]: https://david-dm.org/diotoborg/velit-nulla
[dev-deps-svg]: https://david-dm.org/diotoborg/velit-nulla/dev-status.svg
[dev-deps-url]: https://david-dm.org/diotoborg/velit-nulla#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotoborg/velit-nulla.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotoborg/velit-nulla.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotoborg/velit-nulla.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotoborg/velit-nulla
[codecov-image]: https://codecov.io/gh/diotoborg/velit-nulla/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/diotoborg/velit-nulla/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/diotoborg/velit-nulla
[actions-url]: https://github.com/diotoborg/velit-nulla/actions
