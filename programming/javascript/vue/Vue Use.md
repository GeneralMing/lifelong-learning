https://vueuse.org/guide/best-practice.html

- `watch` and `computed` that will be disposed when the component is unmounted
- All VueUse functions follow this convention.
- To manually dispose the side-effects, some functions return a stop handler just like the `watch` function.
- Not all functions return a `stop` handler so a more general solution is to use the [**`effectScope` API**](https://vuejs.org/api/reactivity-advanced.html#effectscope) from Vue.
## Reactive arguments
- You can use either a non-reactive or a reactive argument.
- The [`useTitle`](https://vueuse.org/core/useTitle/) composable helps you get and set the current page's `document.title` property.

``` typescript
const isDark = useDark()
const title = useTitle('Hello')

console.log(document.title) // "Hello"

watch(isDark, () => {
  title.value = isDark.value ? '🌙 Good evening!' : '☀️ Good morning!'
})
```

###### Ref Argument[​](https://vueuse.org/guide/best-practice.html#ref-argument)

You can pass a ref into [`useTitle`](https://vueuse.org/core/useTitle/) instead of using the returned ref.

``` typescript
const isDark = useDark()
const title = computed(() => isDark.value ? '🌙 Good evening!' : '☀️ Good morning!')

useTitle(title)
```

## Configurations
- Event filters - control when events get triggered
- For example, you can use `throttleFilter` and `debounceFilter` or  `pausableFilter` to throttle.

## Components
- Renderless components - something like this
``` typescript
<script setup>
import { OnClickOutside } from '@vueuse/components'

function close() {
  /* ... */
}
</script>

<template>
  <OnClickOutside @trigger="close">
    <div>
      Click Outside of Me
    </div>
  </OnClickOutside>
</template>
```


Continue - https://vueuse.org/guidelines.html

Michael Thiessen - https://michaelnthiessen.com/clean-components-toolkit
https://michaelnthiessen.com/12-design-patterns-vue


## Handling large lists efficiently in Vue
- `useVirtualList` - for showing only visible items
- `v-for` with key
- lazy loading for fetching

## Multi-tenancy in Nuxt
https://www.adamdehaven.com/articles/powering-multi-tenant-applications-with-nuxt
- Detecting which tenant - custom fetch with `x-tenant-hostname` to figure out what tenant the thing is
- `useAsyncData` - to avoid double-fetching data during server-side rendering
- Tenant context to identify and attach the tenant info to the `event.context` so it's available to all server routes and middleware
	- **H3EventContext** is a TypeScript interface used in the [h3](https://h3.unjs.io/) framework, which underpins the server engine for Nuxt 3 (and Nitro). It represents the context object attached to each HTTP event (request) processed by your server-side handlers.
	- In Nuxt 3, the `defineEventHandler` function is used to define server-side API and middleware handlers inside the `server/` directory of your project. It is the recommended way to create API endpoints, middleware, and server routes in Nuxt's server engine (Nitro)
	- This pattern is used in files under `server/api`, `server/routes`, or `server/middleware`
- Nuxt Content?



## Announcing Oxlint 1.0
https://voidzero.dev/posts/announcing-oxlint-1-stable
- 50-100x faster than ESLint with the same setup

## Biomejs
- 35x faster than prettier? https://biomejs.dev/



GPT
- Voice mode
- Mac Whisper or Superwhisper?
- Supherhuman
- Deep Wiki, Git Diagram