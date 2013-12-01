# SYNOPSIS
Provides pipes by operator instead of a chain.

# DESCRIPTION
Pipe streams together with a simpler syntax, like `a | b | c`

# EXAMPLES
`pipe` does not require `through`, i just like using through.

```js
var through = require('through')
require('pipe').install()

var a = through(function(d) {
  this.queue(d.toString().toUpperCase())
})

var b = through(function(d) {
  this.queue(d.split('-').join(','))
})

var c = through(function(d) {
  this.queue(d.split(',').reverse().toString())
})

a | b | c | process.stdout

a.write('a-s-d-f') // OMG WTF? => F,D,S,A
```
