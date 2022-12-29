# awesome-javascript-interpreters

## javascript interpreters

| repo | stars | last commit | comments |
-- | -- | -- | --
[bellard/quickjs](https://github.com/bellard/quickjs) | ![GitHub Repo stars](https://img.shields.io/github/stars/bellard/quickjs) | ![GitHub last commit](https://img.shields.io/github/last-commit/bellard/quickjs) | WASM, [benchmarks](https://bellard.org/quickjs/bench.html)
[patriksimek/vm2](https://github.com/patriksimek/vm2) | ![GitHub Repo stars](https://img.shields.io/github/stars/patriksimek/vm2) | ![GitHub last commit](https://img.shields.io/github/last-commit/patriksimek/vm2) | nodejs
[NeilFraser/JS-Interpreter](https://github.com/NeilFraser/JS-Interpreter) | ![GitHub Repo stars](https://img.shields.io/github/stars/NeilFraser/JS-Interpreter) | ![GitHub last commit](https://img.shields.io/github/last-commit/NeilFraser/JS-Interpreter) | based on vm-browserify, old, no package
[sablejs/sablejs](https://github.com/sablejs/sablejs) | ![GitHub Repo stars](https://img.shields.io/github/stars/sablejs/sablejs) | ![GitHub last commit](https://img.shields.io/github/last-commit/sablejs/sablejs) | [benchmarks](https://github.com/sablejs/sablejs#benchmark), ES5.1 = ES2009
[engine262/engine262](https://github.com/engine262/engine262) | ![GitHub Repo stars](https://img.shields.io/github/stars/engine262/engine262) | ![GitHub last commit](https://img.shields.io/github/last-commit/engine262/engine262) | ES2020, complex interface, stepped execution, empty sandbox
[bplok20010/eval5](https://github.com/bplok20010/eval5) | ![GitHub Repo stars](https://img.shields.io/github/stars/bplok20010/eval5) | ![GitHub last commit](https://img.shields.io/github/last-commit/bplok20010/eval5) | ES5 = ES2009
[Siubaak/sval](https://github.com/Siubaak/sval) | ![GitHub Repo stars](https://img.shields.io/github/stars/Siubaak/sval) | ![GitHub last commit](https://img.shields.io/github/last-commit/Siubaak/sval) | ES2019, simple interface
[metaes/metaes](https://github.com/metaes/metaes) | ![GitHub Repo stars](https://img.shields.io/github/stars/metaes/metaes) | ![GitHub last commit](https://img.shields.io/github/last-commit/metaes/metaes) |

### old projects

last commit is over 1 year ago

repo | stars | last commit | comments
-- | -- | -- | --
[bramblex/jsjs](https://github.com/bramblex/jsjs) | ![GitHub Repo stars](https://img.shields.io/github/stars/bramblex/jsjs) | ![GitHub last commit](https://img.shields.io/github/last-commit/bramblex/jsjs) |
[jterrace/js.js](https://github.com/jterrace/js.js) | ![GitHub Repo stars](https://img.shields.io/github/stars/jterrace/js.js) | ![GitHub last commit](https://img.shields.io/github/last-commit/jterrace/js.js) | based on SpiderMonkey, last version 2012
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

## use cases

when do we need a javascript interpreter?

### inject script

workaround for

```js
globalThis.callback = (value) => console.log(value == 3)
const source = `
  const x = 1
  const y = 2
  globalThis.callback(x + y)
`
const script = document.createElement("script")
script.textContent = source
document.body.append(script)
```

which can break with CSP

> Refused to execute inline script because it violates the following Content Security Policy directive: "script-src 'self'".

### eval code

workaround for

```js
const x = 1
const y = 2
const v = eval("x + y")
console.log(v == 3)
```

which can break with CSP

> EvalError: Refused to evaluate a string as JavaScript because 'unsafe-eval' is not an allowed source of script in the following Content Security Policy directive: "script-src 'self'".


### compile functions

workaround for

```js
const f = new Function("x", "y", "return x + y")
console.log(f(1, 2) == 3)
console.log(f(3, 4) == 7)
```

which can break with CSP

> EvalError: Refused to evaluate a string as JavaScript because 'unsafe-eval' is not an allowed source of script in the following Content Security Policy directive: "script-src 'self'".

### compile modules

workaround for

```js
(async () => {
const m = await import("data:text/javascript,export function f(x, y) { return x + y; }")
console.log(m.f(1, 2) == 3)
console.log(m.f(3, 4) == 7)
})()
```

which can break with CSP

> Refused to load the script ... because it violates the following Content Security Policy directive: "script-src 'self'". Note that 'script-src-elem' was not explicitly set, so 'script-src' is used as a fallback.

## not needed

a javascript interpreter is not needed is some cases

### web extensions

https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Content_scripts#loading_content_scripts

<blockquote>

Loading content scripts

You can load a content script into a web page in one of three ways:

1\. At install time, into pages that match URL patterns.

Using the [content_scripts](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/content_scripts) key in your manifest.json, you can ask the browser to load a content script whenever the browser loads a page whose URL matches a given pattern.

2\. At runtime, into pages that match URL patterns.

Using the [contentScripts](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/contentScripts) API, you can ask the browser to load a content script whenever the browser loads a page whose URL matches a given pattern. (This is similar to method 1, except that you can add and remove content scripts at runtime.)

3\. At runtime, into specific tabs.

In Manifest V2, using tabs.executeScript(), or Manifest V3, using [scripting.executeScript()](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/scripting/executeScript), you can load a content script into a specific tab whenever you want. (For example, in response to the user clicking on a browser action.)

There is only one global scope per frame, per extension. This means that variables from one content script can directly be accessed by another content script, regardless of how the content script was loaded.

Using methods (1) and (2), you can only load scripts into pages whose URLs can be represented using a match pattern.

Using method (3), you can also load scripts into pages packaged with your extension, but you can't load scripts into privileged browser pages (like "about:debugging" or "about:addons").

</blockquote>

https://github.com/violentmonkey/violentmonkey/blob/master/src/background/utils/preinject.js

```js
const contentScriptsAPI = browser.contentScripts;

// ...

function registerScriptDataFF(inject, url) {
  for (const scr of inject[ENV_SCRIPTS]) {
    scr.code = scr[__CODE];
  }
  return contentScriptsAPI.register({
    js: [{
      code: `${resolveDataCodeStr}(${JSON.stringify(inject)})`,
    }],
    matches: url.split('#', 1),
    runAt: 'document_start',
  });
}
```

## see also

- https://npmtrends.com/evil-eval-vs-js-interpreter-vs-vm-browserify-vs-vm2
- https://github.com/search?l=JavaScript&q=javascript+interpreter
- https://github.com/search?l=TypeScript&q=javascript+interpreter
- https://www.w3schools.com/Js/js_versions.asp - ECMAScript Editions
- https://skratchdot.com/2013/05/userscripts-and-content-security-policy/
