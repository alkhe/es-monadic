# es-monadic
Monadic Assignment for Javascript Promises.

- utilizes the __do-notation__ [strawman proposal](http://wiki.ecmascript.org/doku.php?id=strawman:do_expressions)
- introduces a cleaner and more readable syntax for asynchronous control flow
- inspired by controversy arising from [this tweet](https://twitter.com/izs/status/694321665430261760)
- further reading: https://en.wikibooks.org/wiki/Haskell/do_notation
- similar to async/await syntax

__Monadic Assignment__
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

__async/await (esnext)__
```js
let finalPromise = (async () => {
	let a = await promiseA;
	let b = await promiseB;
	let c = f(a, b);
	return g(a, b, c);
})();
```

__Promise (ES6)__
```js
let finalPromise = promiseA.then(a =>
	promiseB.then(b => {
		let c = f(a, b);
		return g(a, b, c);
	})
);
```
