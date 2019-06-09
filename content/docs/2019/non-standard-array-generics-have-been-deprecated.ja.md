---
title: "非標準の `Array` 汎用メソッドが廃止予定となりました"
date: "2019-06-09T06:34:00-04:00"
categories: ["javascript"]
tags: []
versions: ["68"]
references:
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=1536860"
      title: "Bug 1536860 - Add telemetry and warning for Array generics"
---
[JavaScript 1.6](https://developer.mozilla.org/docs/Web/JavaScript/New_in_JavaScript/1.6) で導入された非標準で Firefox 独自の [`Array` 汎用メソッド](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array#Array_generic_methods) は廃止予定となり、近い将来削除されることとなりました。これらの汎用・静的メソッドには以下のものが含まれます。

* `Array.concat`
* `Array.every`
* `Array.filter`
* `Array.forEach`
* `Array.indexOf`
* `Array.join`
* `Array.lastIndexOf`
* `Array.map`
* `Array.pop`
* `Array.push`
* `Array.reduce`
* `Array.reduceRight`
* `Array.reverse`
* `Array.shift`
* `Array.slice`
* `Array.some`
* `Array.sort`
* `Array.splice`
* `Array.unshift`

以下に汎用メソッドの代替策をいくつか挙げます。

```js
// 非推奨
Array.forEach(obj, callback);
// 代替策 1: スプレッド構文
[...obj].forEach(callback);
// 代替策 2: Array.from メソッド
Array.from(obj).forEach(callback);
// 代替策 3: 昔ながらの方法
// (オブジェクトがまだ反復可能となっていない場合)
Array.prototype.forEach.call(obj, callback);
```

なお、[`Array.prototype`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype) 上の標準インスタンスメソッドには当然ながら影響はありません。以下の静的メソッドも ECMAScript 2015 (ES6) 仕様に含まれており、削除される予定はありません。

* [`Array.from`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/from)
* [`Array.isArray`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)
* [`Array.of`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/of)

なお、`String` 汎用メソッドは既に [Firefox 68 で削除されています](https://www.fxsitecompat.com/ja/docs/2019/non-standard-string-generics-have-been-removed/)。