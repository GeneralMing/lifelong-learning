# 3 - Patterns for Testing Props

- Your user interface is a function of your data.
- Side effects:
	- `watchEffect` and `watch` - these are basically to "do something in reaction to a side effect"
	- `computed` cannot be marked as `async`.
``` vue
<script lang="ts" setup>
import { ref, watchEffect } from 'vue';

const n1 = ref(0);
const n2 = ref(0);
const result = ref(0);

watchEffect(async () => {
  const url = '/sum?' + new URLSearchParams({
    n1: n1.value.toString(),
    n2: n2.value.toString(),
  }).toString();

  const data = await window.fetch(url);
  result.value = await data.json();
});
</script>

<template>
  <input v-model.number="n1" />
  <input v-model.number="n2" />
  <div>{{ n1 }} + {{ n2 }} is {{ result }}.</div>
</template>

```

# 4 - Writing Testable Forms

- Skip for now

# 5 - Emitting Events

- `defineEmits` - you need this for type safety.
- Vue vs React
	- Vue will pass a native event. A `PointerEvent`, in fact, with `type: "click"`, `x` and `y` values, and various other interesting things. There isn’t anything Vue specific about it. It’s the raw HTML event from the underlying `<input>`.
	- React is a little different. React will pass something they call a **SyntheticBaseEvent**. React has its own event system that wraps the native events. It does give you native event under the `nativeEvent` property, so it’s there if you want it.


``` vue

<!-- Not a template. This is just HTML-->
<script> function count() { console.log(arguments) } </script> <button onclick="count()">Counter</button>
```

Clicking this logs ... nothing. Changing it to `onclick="count()"` will call `count()`, but you won’t get the native event. If you want that, you need to write some JavaScript:

``` js
document.querySelector('button').addEventListener('click', event => {
// event is PointerEvent
})
```

- This is what Vue and React are doing under the hood—actually, if you use dom listeners, they use the native event object, but if you use an inline JS handler, you don’t get the event object as expected.
- There’s one more improvement we can make. If you are writing a form, specifically, you always should use the **submit** event. The **click** event on the `<button>` is not only not necessary, but not correct. Forms should be accessible, and part of that is allowing them to be submitted without a mouse, for example by pressing enter. **@submit** handles this, but **@click** won’t.
****

# 6 - HTTP and API Requests
- Skip but can do when testing

# 7 - Renderless components

- 