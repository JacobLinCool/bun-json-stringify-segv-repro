# bun-json-stringify-segv-repro

Reproduction of a segfault when using `JSON.stringify` in bun.

## Run

```sh
bun crashing.js
```

## Source

### Crashing Source

[`crashing.js`](crashing.js)

```js
console.log(JSON.stringify(process, null, 4));
```

### Working Source

[`working.js`](working.js)

```js
console.log(process);
```

## Result

The crash report:

```sh
❯ bun crashing.js
Detected offset inconsistency: inlineOverflowAccordingToTotalSize doesn't match numberOfOutOfLineSlotsForMaxOffset!
this = 0x300011f10
transitionOffset = -1
maxOffset = 64
m_inlineCapacity = 65
propertyTable = 0x117425f80
numberOfSlotsForMaxOffset = 65
totalSize = 65
inlineOverflowAccordingToTotalSize = 0
numberOfOutOfLineSlotsForMaxOffset = 1

Crash at 4377300596


–––– bun meta ––––
Bun v0.1.5 macOS Silicon 21.4.0
AutoCommand: 
Elapsed: 65ms | User: 4ms | Sys: 15ms
RSS: 17.12MB | Peak: 17.12MB | Commit: 67.11MB | Faults: 578
–––– bun meta ––––

Ask for #help in https://bun.sh/discord or go to https://bun.sh/issues
```
