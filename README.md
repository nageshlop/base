# base-methods [![NPM version](https://badge.fury.io/js/base-methods.svg)](http://badge.fury.io/js/base-methods)

> Starter for creating a node.js application with a handful of common methods, like `set`, `get`, and `del`.

## Install

Install with [npm](https://www.npmjs.com/)

```sh
$ npm i base-methods --save
```

## Usage

```js
var Base = require('base-methods');
```

## API

### [Base](index.js#L25)

Create an instance of `Base` with optional `options`.

**Params**

* `options` **{Object}**

**Example**

```js
var app = new Base();
app.set('foo', 'bar');
console.log(app.get('foo'));
//=> 'bar'
```

### [.set](index.js#L63)

Assign `value` to `key`. Also emits `set` with the key and value.

**Params**

* `key` **{String}**
* `value` **{*}**
* `returns` **{Object}**: Returns the instance for chaining.

**Example**

```js
app.on('set', function(key, val) {
  // do something when `set` is emitted
});

app.set(key, value);

// also takes an object or array
app.set({name: 'Halle'});
app.set([{foo: 'bar'}, {baz: 'quux'}]);
console.log(app);
//=> {name: 'Halle', foo: 'bar', baz: 'quux'}
```

### [.get](index.js#L90)

Return the stored value of `key`. Dot notation may be used to get [nested property values][get-value].

**Params**

* `key` **{*}**
* `escape` **{Boolean}**
* `returns` **{*}**

**Example**

```js
app.set('foo', 'bar');
app.get('foo');
// => "bar"
```

### [.del](index.js#L111)

Delete `key` from the instance. Also emits `del` with the key of the deleted item.

**Params**

* `key` **{String}**
* `returns` **{Object}**: Returns the instance for chaining.

**Example**

```js
app.del(); // delete all
// or
app.del('foo');
// or
app.del(['foo', 'bar']);
```

### [.define](index.js#L137)

Define a non-enumerable property on the instance.

**Params**

* `key` **{String}**
* `value` **{any}**
* `returns` **{Object}**: Returns the instance for chaining.

**Example**

```js
// arbitrary `render` function using lodash `template`
define('render', function(str, locals) {
  return _.template(str)(locals);
});
```

### [.visit](index.js#L153)

Visit `method` over the items in the given object, or map
visit over the objects in an array.

**Params**

* `method` **{String}**
* `val` **{Object|Array}**
* `returns` **{Object}**: Returns the instance for chaining.

### [.extend](index.js#L182)

Static method for inheriting both the prototype and static methods of the `Base` class.

**Params**

* `Ctor` **{Function}**: The constructor to extend.

**Example**

```js
function MyApp(options) {
  Base.call(this, options);
}
Base.extend(MyApp);

// Optionally pass another object to extend onto `MyApp`
function MyApp(options) {
  Base.call(this, options);
  Foo.call(this, options);
}
Base.extend(MyApp, Foo.prototype);
```

## Related projects

* [collection-visit](https://www.npmjs.com/package/collection-visit): Visit a method over the items in an object, or map visit over the objects… [more](https://www.npmjs.com/package/collection-visit) | [homepage](https://github.com/jonschlinkert/collection-visit)
* [component-emitter](https://www.npmjs.com/package/component-emitter): Event emitter | [homepage](https://github.com/component/emitter)
* [define-property](https://www.npmjs.com/package/define-property): Define a non-enumerable property on an object. | [homepage](https://github.com/jonschlinkert/define-property)
* [get-value](https://www.npmjs.com/package/get-value): Use property paths (`  a.b.c`) to get a nested value from an object. | [homepage](https://github.com/jonschlinkert/get-value)
* [set-value](https://www.npmjs.com/package/set-value): Create nested values and any intermediaries using dot notation (`'a.b.c'`) paths. | [homepage](https://github.com/jonschlinkert/set-value)
* [unset-value](https://www.npmjs.com/package/unset-value): Delete nested properties from an object using dot notation. | [homepage](https://github.com/jonschlinkert/unset-value)

## Running tests

Install dev dependencies:

```sh
$ npm i -d && npm test
```

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/jonschlinkert/base-methods/issues/new).

## Author

**Jon Schlinkert**

+ [github/jonschlinkert](https://github.com/jonschlinkert)
+ [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

## License

Copyright © 2015 Jon Schlinkert
Released under the MIT license.

***

_This file was generated by [verb-cli](https://github.com/assemble/verb-cli) on August 29, 2015._

[collection-visit]: https://github.com/jonschlinkert/collection-visit
[component-emitter]: https://github.com/component/emitter
[define-property]: https://github.com/jonschlinkert/define-property
[get-value]: https://github.com/jonschlinkert/get-value
[set-value]: https://github.com/jonschlinkert/set-value
[unset-value]: https://github.com/jonschlinkert/unset-value
