# Preact Store

> A fork of [solid's store](https://github.com/solidjs/solid/tree/main/packages/solid/store), switching out its underlying signal implementation for [@preact/signals](https://github.com/preactjs/signals). Missing API to make this store fully featured is a port of `untrack`/`.peek`. 

This submodules contains the means for handling deeps nested reactivity. It provides 2 main primitives `createStore` and `createMutable` which leverage proxies to create dynamic nested reactive structures.

This also contains helper methods `produce` and `reconcile` which augment the behavior of the store setter method to allow for localized mutation and data diffing.

For full documentation, check out the [website](https://www.solidjs.com/docs/latest/api).

## Example

```js
import { useStore } from "deeep";

const [store, setStore] = useStore({
  user: {
    firstName: "John",
    lastName: "Smith"
  }
});

// update store.user.firstName
setStore("user", "firstName", "Will");
```

```js
import { useMutable } from "deeep";

const store = useMutable({
  user: {
    firstName: "John",
    lastName: "Smith"
  }
});

// update store.user.firstName
store.user.firstName = 'Will';
``` 

## Acknowledgement

- check out [deepsignal](https://github.com/luisherranz/deepsignal) for another implementation of a mutable proxy.
