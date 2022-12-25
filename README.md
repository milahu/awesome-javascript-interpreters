# awesome-javascript-interpreters

## javascript interpreters

| repo | stars | last commit | comments |
-- | -- | -- | --
[bellard/quickjs](https://github.com/bellard/quickjs) | ![GitHub Repo stars](https://img.shields.io/github/stars/bellard/quickjs) | ![GitHub last commit](https://img.shields.io/github/last-commit/bellard/quickjs) | WASM, [benchmarks](https://bellard.org/quickjs/bench.html)
[patriksimek/vm2](https://github.com/patriksimek/vm2) | ![GitHub Repo stars](https://img.shields.io/github/stars/patriksimek/vm2) | ![GitHub last commit](https://img.shields.io/github/last-commit/patriksimek/vm2) | nodejs
[jterrace/js.js](https://github.com/jterrace/js.js) | ![GitHub Repo stars](https://img.shields.io/github/stars/jterrace/js.js) | ![GitHub last commit](https://img.shields.io/github/last-commit/jterrace/js.js) | based on SpiderMonkey, 2012
[NeilFraser/JS-Interpreter](https://github.com/NeilFraser/JS-Interpreter) | ![GitHub Repo stars](https://img.shields.io/github/stars/NeilFraser/JS-Interpreter) | ![GitHub last commit](https://img.shields.io/github/last-commit/NeilFraser/JS-Interpreter) | based on vm-browserify
[sablejs/sablejs](https://github.com/sablejs/sablejs) | ![GitHub Repo stars](https://img.shields.io/github/stars/sablejs/sablejs) | ![GitHub last commit](https://img.shields.io/github/last-commit/sablejs/sablejs) | [benchmarks](https://github.com/sablejs/sablejs#benchmark), ES5.1 = ES2009
[engine262/engine262](https://github.com/engine262/engine262) | ![GitHub Repo stars](https://img.shields.io/github/stars/engine262/engine262) | ![GitHub last commit](https://img.shields.io/github/last-commit/engine262/engine262) | ES2020, complex interface, stepped execution, empty sandbox
[bplok20010/eval5](https://github.com/bplok20010/eval5) | ![GitHub Repo stars](https://img.shields.io/github/stars/bplok20010/eval5) | ![GitHub last commit](https://img.shields.io/github/last-commit/bplok20010/eval5) | ES5 = ES2009, written in TypeScript
[Siubaak/sval](https://github.com/Siubaak/sval) | ![GitHub Repo stars](https://img.shields.io/github/stars/Siubaak/sval) | ![GitHub last commit](https://img.shields.io/github/last-commit/Siubaak/sval) | ES2019, simple interface
[metaes/metaes](https://github.com/metaes/metaes) | ![GitHub Repo stars](https://img.shields.io/github/stars/metaes/metaes) | ![GitHub last commit](https://img.shields.io/github/last-commit/metaes/metaes) |

### old projects

last commit is over 1 year ago

repo | stars | last commit | comments
-- | -- | -- | --
[bramblex/jsjs](https://github.com/bramblex/jsjs) | ![GitHub Repo stars](https://img.shields.io/github/stars/bramblex/jsjs) | ![GitHub last commit](https://img.shields.io/github/last-commit/bramblex/jsjs) |
[mozilla/narcissus](https://github.com/mozilla/narcissus) | ![GitHub Repo stars](https://img.shields.io/github/stars/mozilla/narcissus) | ![GitHub last commit](https://img.shields.io/github/last-commit/mozilla/narcissus) | archived
[zuluoaaa/makeJs](https://github.com/zuluoaaa/makeJs) | ![GitHub Repo stars](https://img.shields.io/github/stars/zuluoaaa/makeJs) | ![GitHub last commit](https://img.shields.io/github/last-commit/zuluoaaa/makeJs) |
[jrainlau/canjs](https://github.com/jrainlau/canjs) | ![GitHub Repo stars](https://img.shields.io/github/stars/jrainlau/canjs) | ![GitHub last commit](https://img.shields.io/github/last-commit/jrainlau/canjs) |
[hacksparrow/safe-eval](https://github.com/hacksparrow/safe-eval) | ![GitHub Repo stars](https://img.shields.io/github/stars/hacksparrow/safe-eval) | ![GitHub last commit](https://img.shields.io/github/last-commit/hacksparrow/safe-eval) | nodejs
[browserify/vm-browserify](https://github.com/browserify/vm-browserify) | ![GitHub Repo stars](https://img.shields.io/github/stars/browserify/vm-browserify) | ![GitHub last commit](https://img.shields.io/github/last-commit/browserify/vm-browserify) | substack/vm-browserify
[jkeylu/evil-eval](https://github.com/jkeylu/evil-eval) | ![GitHub Repo stars](https://img.shields.io/github/stars/jkeylu/evil-eval) | ![GitHub last commit](https://img.shields.io/github/last-commit/jkeylu/evil-eval) |

## selection criteria

- browser or nodejs: does it run in a browser (web APIs)?
- error handling: message, location, stack
- simple interface or complex interface
- how empty is the default sandbox? for example, does `console.log` work?
- simple interface between sandbox and environment: import, export, call, return, throw
- async code: does the interpreter block the main thread?
- stepped execution is supported? needed for debugging
- ecmascript version: what spec is implemented?
- spec compliance: how complete is the implementation?
- compatibility: can it run unmodified code?
- `createFunction` - does it have a replacement for `const f = new Function("x", "y", "return x + y")`?
- `createModule` - does it have a replacement for `const m = await import("data:text/javascript,export function f(x, y) { return x + y; }")`?
- performance: how much slower than native speed? is performance relevant for this use case?
- WASM or javascript? WASM is faster, but more complex

## ECMAScript version

some test code

```js
console.log("ES2009", Array.isArray([1, 2]))
console.log("ES2015", [1, 2].find(x => x == 1))
console.log("ES2016", [1, 2].includes(1))
console.log("ES2017", Object.entries({a: 1}))
console.log("ES2018", [ ...[1, 2] ])
console.log("ES2019", Object.fromEntries([["a",1]]))
console.log("ES2020", null ?? "asdf")
```

## see also

- https://npmtrends.com/evil-eval-vs-js-interpreter-vs-vm-browserify-vs-vm2
- https://github.com/search?l=JavaScript&q=javascript+interpreter
- https://github.com/search?l=TypeScript&q=javascript+interpreter
- https://www.w3schools.com/Js/js_versions.asp - ECMAScript Editions

