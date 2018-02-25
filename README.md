[![](https://img.shields.io/badge/SLOC-1-brightgreen.svg)](https://github.com/jnvm/eachvar/blob/master/eachVar.js#L1)
[![David](https://img.shields.io/david/jnvm/eachvar.svg?maxAge=360000)]()
# eachVar

Instead this:

```javascript
let thing = some.operator('thing')
let aThing = some.operator('aThing')
let thisThing = some.operator('thisThing')
let thatThing = some.operator('thatThing')
let theOtherThing = some.operator('theOtherThing')
//...and so on!
```

Do this:

```javascript
const eachVar = require('eachvar')
let {thing, aThing, thisThing, 
	thatThing, theOtherThing} = eachVar(some.operator)
```

...and through the magic of [destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) and [proxies](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/get), never stutter variables in code again!

More signal, less noise.

## How It Works

`eachVar(iterateeFunction)` is a function which invokes its input function with a string of each variable name on the left of the destructuring assignment in order,
removing the need to repeat them on each side of the equal sign, and maybe encouraging more meaningful names.

Or you could describe it as an iterator across variable names.

## More Examples
```javascript
const eachVar = require('eachvar')
const dryquire = eachVar(require)
const {fs, crypto, util, http, os, repl, express, "package.json":{scripts}} = dryquire
const {sqlA, sqlB, sqlC, sqlD} = eachVar(s => fs.readFileSync(`${__dirname}/${s}.sql`))
```
----
#### see also
* [`new Proxy()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
* [`destructuring`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)