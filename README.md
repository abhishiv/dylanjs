# DylanJS

Fine grained reactive UI Library

[![Version](https://img.shields.io/npm/v/dylanjs.svg?color=success&style=flat-square)](https://www.npmjs.com/package/dylanjs)
[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![Build Status](https://github.com/abhishiv/dylanjs/actions/workflows/ci.yml/badge.svg)](https://github.com/abhishiv/dylanjs/actions/workflows/ci.yml)
![Badge size](https://img.badgesize.io/https://cdn.jsdelivr.net/npm/dylanjs/+esm?compression=gzip&label=gzip&style=flat-square)

**npm**: `npm i dylanjs`  
**cdn**: https://cdn.jsdelivr.net/npm/dylanjs/+esm

---

-   **Small.** hello world at `~3kB` gzip.
-   **Truly reactive.** automatically derived from the app state.
-   **DevEx.** no compile step needed, choose your view syntax: `h` or `<JSX/>`.

#### Example

[Counter - Codesandbox](https://codesandbox.io/s/counter-demo-dylanjs-t7ift3?file=/src/index.tsx)

```tsx
/** @jsx h **/

import { component, h, render } from "dylanjs/dom";

export const HomePage = component<{ name: string }>(
    "HomePage",
    (props, { signal, wire }) => {
        const count = signal(0);
        return (
            <div id="home">
                <p>Hey, {props.name}</p>
                <button
                    onclick={() => {
                        count(count() + 1);
                    }}
                >
                    Increment to {wire(count)}
                </button>
            </div>
        );
    }
);

render(<HomePage name="John Doe" />, document.body);
```

## Motivation

The state part of this library is based on [haptic](https://github.com/heyheyhello/haptic) specially the concept of aptly named Signals and Wires. Like haptic it also favours manual subscription model instead of automatic subscriptions model.

```tsx
/** @jsx h **/
```

It's also influenced by Sinuous, Solid, & S.js

## API

-   signal
-   wire
-   getContext
-   setContext
