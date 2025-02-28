# Items

Count: 8

## Item 1: Stmt 0, `VarDeclarator(0)`

```js
let clientComponentLoadStart = 0;

```

- Declares: `clientComponentLoadStart`
- Write: `clientComponentLoadStart`

## Item 2: Stmt 1, `VarDeclarator(0)`

```js
let clientComponentLoadTimes = 0;

```

- Declares: `clientComponentLoadTimes`
- Write: `clientComponentLoadTimes`

## Item 3: Stmt 2, `VarDeclarator(0)`

```js
let clientComponentLoadCount = 0;

```

- Declares: `clientComponentLoadCount`
- Write: `clientComponentLoadCount`

## Item 4: Stmt 3, `Normal`

```js
export function wrapClientComponentLoader(ComponentMod) {
    if (!('performance' in globalThis)) {
        return ComponentMod.__next_app__;
    }
    return {
        require: (...args)=>{
            const startTime = performance.now();
            if (clientComponentLoadStart === 0) {
                clientComponentLoadStart = startTime;
            }
            try {
                clientComponentLoadCount += 1;
                return ComponentMod.__next_app__.require(...args);
            } finally{
                clientComponentLoadTimes += performance.now() - startTime;
            }
        },
        loadChunk: (...args)=>{
            const startTime = performance.now();
            try {
                clientComponentLoadCount += 1;
                return ComponentMod.__next_app__.loadChunk(...args);
            } finally{
                clientComponentLoadTimes += performance.now() - startTime;
            }
        }
    };
}

```

- Hoisted
- Declares: `wrapClientComponentLoader`
- Reads (eventual): `clientComponentLoadStart`
- Write: `wrapClientComponentLoader`
- Write (eventual): `clientComponentLoadStart`, `clientComponentLoadCount`, `clientComponentLoadTimes`

## Item 5: Stmt 4, `Normal`

```js
export function getClientComponentLoaderMetrics(options = {}) {
    const metrics = clientComponentLoadStart === 0 ? undefined : {
        clientComponentLoadStart,
        clientComponentLoadTimes,
        clientComponentLoadCount
    };
    if (options.reset) {
        clientComponentLoadStart = 0;
        clientComponentLoadTimes = 0;
        clientComponentLoadCount = 0;
    }
    return metrics;
}

```

- Hoisted
- Declares: `getClientComponentLoaderMetrics`
- Reads (eventual): `clientComponentLoadStart`, `clientComponentLoadTimes`, `clientComponentLoadCount`
- Write: `getClientComponentLoaderMetrics`
- Write (eventual): `clientComponentLoadStart`, `clientComponentLoadTimes`, `clientComponentLoadCount`

# Phase 1
```mermaid
graph TD
    Item1;
    Item2;
    Item3;
    Item4;
    Item5;
    Item6;
    Item6["ModuleEvaluation"];
    Item7;
    Item7["export wrapClientComponentLoader"];
    Item8;
    Item8["export getClientComponentLoaderMetrics"];
```
# Phase 2
```mermaid
graph TD
    Item1;
    Item2;
    Item3;
    Item4;
    Item5;
    Item6;
    Item6["ModuleEvaluation"];
    Item7;
    Item7["export wrapClientComponentLoader"];
    Item8;
    Item8["export getClientComponentLoaderMetrics"];
    Item7 --> Item4;
    Item8 --> Item5;
```
# Phase 3
```mermaid
graph TD
    Item1;
    Item2;
    Item3;
    Item4;
    Item5;
    Item6;
    Item6["ModuleEvaluation"];
    Item7;
    Item7["export wrapClientComponentLoader"];
    Item8;
    Item8["export getClientComponentLoaderMetrics"];
    Item7 --> Item4;
    Item8 --> Item5;
    Item4 --> Item1;
    Item4 --> Item3;
    Item4 --> Item2;
    Item5 --> Item1;
    Item5 --> Item2;
    Item5 --> Item3;
```
# Phase 4
```mermaid
graph TD
    Item1;
    Item2;
    Item3;
    Item4;
    Item5;
    Item6;
    Item6["ModuleEvaluation"];
    Item7;
    Item7["export wrapClientComponentLoader"];
    Item8;
    Item8["export getClientComponentLoaderMetrics"];
    Item7 --> Item4;
    Item8 --> Item5;
    Item4 --> Item1;
    Item4 --> Item3;
    Item4 --> Item2;
    Item5 --> Item1;
    Item5 --> Item2;
    Item5 --> Item3;
```
# Final
```mermaid
graph TD
    N0["Items: [ItemId(Export((&quot;getClientComponentLoaderMetrics&quot;, #2), &quot;getClientComponentLoaderMetrics&quot;))]"];
    N1["Items: [ItemId(Export((&quot;wrapClientComponentLoader&quot;, #2), &quot;wrapClientComponentLoader&quot;))]"];
    N2["Items: [ItemId(0, VarDeclarator(0))]"];
    N3["Items: [ItemId(1, VarDeclarator(0))]"];
    N4["Items: [ItemId(2, VarDeclarator(0))]"];
    N5["Items: [ItemId(3, Normal)]"];
    N6["Items: [ItemId(4, Normal)]"];
    N7["Items: [ItemId(ModuleEvaluation)]"];
    N1 --> N5;
    N0 --> N6;
    N5 --> N2;
    N5 --> N4;
    N5 --> N3;
    N6 --> N2;
    N6 --> N3;
    N6 --> N4;
```
# Entrypoints

```
{
    Export(
        "getClientComponentLoaderMetrics",
    ): 0,
    ModuleEvaluation: 7,
    Exports: 8,
    Export(
        "wrapClientComponentLoader",
    ): 1,
}
```


# Modules (dev)
## Part 0
```js
import { a as getClientComponentLoaderMetrics } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
export { getClientComponentLoaderMetrics };

```
## Part 1
```js
import { b as wrapClientComponentLoader } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -5
};
export { wrapClientComponentLoader };

```
## Part 2
```js
let clientComponentLoadStart = 0;
export { clientComponentLoadStart as c } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 3
```js
let clientComponentLoadTimes = 0;
export { clientComponentLoadTimes as d } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 4
```js
let clientComponentLoadCount = 0;
export { clientComponentLoadCount as e } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 5
```js
import { d as clientComponentLoadTimes } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -3
};
import { c as clientComponentLoadStart } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -2
};
import { e as clientComponentLoadCount } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
function wrapClientComponentLoader(ComponentMod) {
    if (!('performance' in globalThis)) {
        return ComponentMod.__next_app__;
    }
    return {
        require: (...args)=>{
            const startTime = performance.now();
            if (clientComponentLoadStart === 0) {
                clientComponentLoadStart = startTime;
            }
            try {
                clientComponentLoadCount += 1;
                return ComponentMod.__next_app__.require(...args);
            } finally{
                clientComponentLoadTimes += performance.now() - startTime;
            }
        },
        loadChunk: (...args)=>{
            const startTime = performance.now();
            try {
                clientComponentLoadCount += 1;
                return ComponentMod.__next_app__.loadChunk(...args);
            } finally{
                clientComponentLoadTimes += performance.now() - startTime;
            }
        }
    };
}
export { wrapClientComponentLoader as b } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 6
```js
import { e as clientComponentLoadCount } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
import { c as clientComponentLoadStart } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -2
};
import { d as clientComponentLoadTimes } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -3
};
function getClientComponentLoaderMetrics(options = {}) {
    const metrics = clientComponentLoadStart === 0 ? undefined : {
        clientComponentLoadStart,
        clientComponentLoadTimes,
        clientComponentLoadCount
    };
    if (options.reset) {
        clientComponentLoadStart = 0;
        clientComponentLoadTimes = 0;
        clientComponentLoadCount = 0;
    }
    return metrics;
}
export { getClientComponentLoaderMetrics as a } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 7
```js
"module evaluation";

```
## Part 8
```js
export { getClientComponentLoaderMetrics } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export getClientComponentLoaderMetrics"
};
export { wrapClientComponentLoader } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export wrapClientComponentLoader"
};

```
## Merged (module eval)
```js
"module evaluation";

```
# Entrypoints

```
{
    Export(
        "getClientComponentLoaderMetrics",
    ): 0,
    ModuleEvaluation: 7,
    Exports: 8,
    Export(
        "wrapClientComponentLoader",
    ): 1,
}
```


# Modules (prod)
## Part 0
```js
import { a as getClientComponentLoaderMetrics } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
export { getClientComponentLoaderMetrics };

```
## Part 1
```js
import { b as wrapClientComponentLoader } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -5
};
export { wrapClientComponentLoader };

```
## Part 2
```js
let clientComponentLoadStart = 0;
export { clientComponentLoadStart as c } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 3
```js
let clientComponentLoadTimes = 0;
export { clientComponentLoadTimes as d } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 4
```js
let clientComponentLoadCount = 0;
export { clientComponentLoadCount as e } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 5
```js
import { d as clientComponentLoadTimes } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -3
};
import { c as clientComponentLoadStart } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -2
};
import { e as clientComponentLoadCount } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
function wrapClientComponentLoader(ComponentMod) {
    if (!('performance' in globalThis)) {
        return ComponentMod.__next_app__;
    }
    return {
        require: (...args)=>{
            const startTime = performance.now();
            if (clientComponentLoadStart === 0) {
                clientComponentLoadStart = startTime;
            }
            try {
                clientComponentLoadCount += 1;
                return ComponentMod.__next_app__.require(...args);
            } finally{
                clientComponentLoadTimes += performance.now() - startTime;
            }
        },
        loadChunk: (...args)=>{
            const startTime = performance.now();
            try {
                clientComponentLoadCount += 1;
                return ComponentMod.__next_app__.loadChunk(...args);
            } finally{
                clientComponentLoadTimes += performance.now() - startTime;
            }
        }
    };
}
export { wrapClientComponentLoader as b } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 6
```js
import { e as clientComponentLoadCount } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
import { c as clientComponentLoadStart } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -2
};
import { d as clientComponentLoadTimes } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -3
};
function getClientComponentLoaderMetrics(options = {}) {
    const metrics = clientComponentLoadStart === 0 ? undefined : {
        clientComponentLoadStart,
        clientComponentLoadTimes,
        clientComponentLoadCount
    };
    if (options.reset) {
        clientComponentLoadStart = 0;
        clientComponentLoadTimes = 0;
        clientComponentLoadCount = 0;
    }
    return metrics;
}
export { getClientComponentLoaderMetrics as a } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 7
```js
"module evaluation";

```
## Part 8
```js
export { getClientComponentLoaderMetrics } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export getClientComponentLoaderMetrics"
};
export { wrapClientComponentLoader } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export wrapClientComponentLoader"
};

```
## Merged (module eval)
```js
"module evaluation";

```
