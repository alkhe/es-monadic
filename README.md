# es-monadic
Monadic Assignment for Javascript Promises.

Utilizes the __do-notation__ [strawman proposal](http://wiki.ecmascript.org/doku.php?id=strawman:do_expressions).

Introduces a cleaner and more readable syntax for asynchronous control flow.

Inspired by [this tweet](https://twitter.com/izs/status/694321665430261760).

Further Reading: https://en.wikibooks.org/wiki/Haskell/do_notation

Similar to async/await syntax.

Monadic Assignment
```js
let finalPromise = do {
	let a <- promiseA;
	let b <- promiseB;
	let c = f(a, b);
	g(a, b, c)
}
// returns another Promise
// if an error (e) is thrown, finalPromise will reject with (e)
```

async/await (esnext)
```js
let finalPromise = (async () => {
	let a = await promiseA;
	let b = await promiseB;
	let c = f(a, b);
	return g(a, b, c);
})();
```

Promise (ES6)
```js
let finalPromise = Promise.all(promiseA, promiseB)
	.then((a, b) => {
		let c = f(a, b);
		return g(a, b, c);
	});
```
