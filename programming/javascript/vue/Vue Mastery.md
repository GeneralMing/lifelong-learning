https://www.vuemastery.com/blog/best-vueuse-composables/#4-usestorage

- `onClickOutside`
- `useFocusTrap` - `useFocusTrap(container, { immediate: true })` - to set focus to the first focusable element inside the container
- `useHead` - Easy way to update the head section of the app
- `useStorage` - syncs your ref to local storage
	- `const input = useStorage('unique-key', 'Hello, world!', sessionStorage)` - also works for session storage
	- And you can use any storage system you want, as long as it implements
``` js
export interface StorageLike {
  getItem(key: string): string | null
  setItem(key: string, value: string): void
  removeItem (key: string): void
}
```

- `useVModel` - syntactic sugar that makes two-way data bind easier.
- `useImage` - can be used using Vue use.
	- There is also a renderless `UseImage` component
``` vue
<template>
  <UseImage src="https://source.unsplash.com/random/401x301">
    <!-- Loading slot -->
    <template #loading>
      <div class="loading gradient"></div>
    </template>
    <!-- Error slot -->
    <template #error>
      Oops!
    </template>
  </UseImage>
</template>

```
- `useDark` - encapsulates the system settings for us.