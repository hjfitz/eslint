# eslint-config-hjf

> My personal eslint configs

## Rules and Rationale

**Typescript only**

I like to throw code around in JS every now and then, but for hacks and giggles.
When coding gets important, I bring tooling in, like the TypeScript compiler and ESLint.

**Tabs**

Anybody can pick their indent width this way: there's no argument between 2 or 4 spaces.

**Unix Line Endings**

These are portable, unlike windows line endings: publishing a CLI with these means that your shebang won't be recognised.

**Single Quotes**

Single quotes generally make it easier to deal with quoting a person. They're not ideal when you've got contractions though. It's the lesser of two evils. There's also one less keypress.

```ts 
// correct
const host = 'github.com'

// incorrect
const remoteHost = "something.com"

// WHY
const notAHost = `template literals are inconsistent across keyboards`
```

**Strict equality always**

It's JavaScript - `'1' == 1` is true. Let's ignore any confusion.

**No floating promises**

If something's a promise, we want to know - even if we're not awaiting it. This makes understanding a new codebase easier.

There are two ways of calling a promise:

```ts
// async-blocking
await makeApiRequest()

// just leave it to get picked up whenever in the microtask queue
void doSomething()
```

**Object curly spacing**

There's no functional reason for this: I just like the way it looks

```ts
import {pickBy, is} from 'ramda'

const isNumeric = is(Number)

const data = {a: 1, b: 'bar'}

const pickNumbers = pickBy(isNumeric)

const numbers = pickNumbers(data) // {a: 1}
```

**Returning `await`**

This is only acceptable in a try-catch. Returning `await` can throw. 

```ts
async function willThrow() {
	// will throw here, as we wait for r.json() to evaluate
	return await fetch('/not_json').then(r => r.json())
}
```

**Semicolons**

They're not necessary in JavaScript. Don't bother.

---
