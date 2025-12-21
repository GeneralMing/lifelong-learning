
Internals that I need to study
Understanding Vue’s internals can help you write more efficient, maintainable, and robust applications. Here are some key Vue internals and concepts you should know:

## Reactivity System

- **Reactivity Tracking:**  
    Vue tracks dependencies between reactive data and effects (like computed properties or watchers) using a system of getters/setters (for refs) and Proxies (for reactive objects). This allows automatic updates when data changes910.
    
- **Effect Scheduler:**  
    Vue batches updates and schedules them asynchronously to avoid unnecessary re-renders and improve performance.
    

## Rendering Mechanism

- **Template Compilation:**  
    Vue compiles templates into render functions, which produce virtual DOM trees[3](https://vuejs.org/guide/extras/rendering-mechanism).
    
- **Virtual DOM and Diffing:**  
    Vue uses a virtual DOM to efficiently update the real DOM. It compares the previous and new virtual DOM trees and applies only the necessary changes[3](https://vuejs.org/guide/extras/rendering-mechanism).
    
- **Static Node Optimization:**  
    Vue identifies and caches static parts of templates, skipping unnecessary virtual DOM diffing for these nodes on re-renders[3](https://vuejs.org/guide/extras/rendering-mechanism).
    

## Component System

- **Component Lifecycle:**  
    Components go through creation, mounting, updating, and destruction phases, with lifecycle hooks (like `created`, `mounted`, `updated`, `unmounted`) available for custom logic[1](https://vuejs.org/guide/essentials/component-basics)[2](https://012.vuejs.org/guide/).
    
- **Slot and Content Projection:**  
    Vue provides slots (and scoped slots) for advanced content projection, allowing flexible component composition[5](https://012.vuejs.org/guide/components.html).
    
- **Props and Events:**  
    Data flows down via props, and events flow up via `$emit`, promoting a clear parent-child communication model[1](https://vuejs.org/guide/essentials/component-basics)[5](https://012.vuejs.org/guide/components.html).
    

## Application Architecture

- **MVVM Pattern:**  
    Vue follows the Model-View-ViewModel (MVVM) architecture, separating the UI (View), data (Model), and the logic that binds them (ViewModel)[2](https://012.vuejs.org/guide/)[7](https://dev.to/ravi_makhija/what-architecture-does-vuejs-use-1n6l).
    
- **State Management:**  
    For complex state, Vue offers composables (Composition API), Pinia, or Vuex for centralized and reactive state management[6](https://github.com/imhotepper/vuejs-architecture-features)10.
    

## Other Internals

- **Directives:**  
    Vue’s built-in directives (like `v-if`, `v-for`, `v-on`, `v-bind`) are compiled into JavaScript logic that manipulates the DOM or binds data[4](https://delftswa.gitbooks.io/desosa2018/content/vuejs/chapter.html).
    
- **Transition System:**  
    Vue provides a transition component and hooks for animating elements entering, leaving, or changing state[5](https://012.vuejs.org/guide/components.html).
    
- **Plugins and Mixins:**  
    Vue supports plugins and mixins for reusing logic across components, though composables are now preferred for new code910.
    

---

**In summary:**  
Understanding Vue’s reactivity system, rendering mechanism, component lifecycle, and architectural patterns will help you leverage Vue’s full potential and troubleshoot issues more effectively.

1. [https://vuejs.org/guide/essentials/component-basics](https://vuejs.org/guide/essentials/component-basics)
2. [https://012.vuejs.org/guide/](https://012.vuejs.org/guide/)
3. [https://vuejs.org/guide/extras/rendering-mechanism](https://vuejs.org/guide/extras/rendering-mechanism)
4. [https://delftswa.gitbooks.io/desosa2018/content/vuejs/chapter.html](https://delftswa.gitbooks.io/desosa2018/content/vuejs/chapter.html)
5. [https://012.vuejs.org/guide/components.html](https://012.vuejs.org/guide/components.html)
6. [https://github.com/imhotepper/vuejs-architecture-features](https://github.com/imhotepper/vuejs-architecture-features)
7. [https://dev.to/ravi_makhija/what-architecture-does-vuejs-use-1n6l](https://dev.to/ravi_makhija/what-architecture-does-vuejs-use-1n6l)
8. [https://www.reddit.com/r/vuejs/comments/1cnad4h/implementing_an_architecture_type/](https://www.reddit.com/r/vuejs/comments/1cnad4h/implementing_an_architecture_type/)
9. [programming.vue_composition_api](https://www.perplexity.ai/search/programming.vue_composition_api)
10. [programming.state_management](https://www.perplexity.ai/search/programming.state_management)


Async without await - https://michaelnthiessen.com/tips/async-without-await
``` ts
export default useAsyncState(promise) {
  // 1. Create state ref synchronously
  const state = ref(null);

  const execute = async () => {
    // 3. Reactivity will update this when it resolves
    state.value = await promise;
  }

  // 2. Execute promise asynchronously in the background
  execute();
  return state;
}
```

# `reactive`, `toRefs`
``` ts
import { reactive, toRefs } from 'vue'

const state = reactive({
  user: {
    name: '',
    isLoggedIn: false,
  }
})

export function useUserStore() {
  const { user } = toRefs(state)

  function login(name) {
    user.value.name = name
    user.value.isLoggedIn = true
  }

  function logout() {
    user.value.name = ''
    user.value.isLoggedIn = false
  }

  return {
    user,
    login,
    logout
  }
}

```
- `reactive` creates a **reactive object** in Vue. This means Vue tracks changes to the object’s properties, so when they change, your UI updates automatically.
- `toRefs` **converts a reactive object’s properties into refs**.  A `ref` is a special object that wraps a value, making it reactive and allowing you to access it with `.value`.
- The type of `reactive` and `ref` is whatever the initial value was. You can specify a type expliclitly (and also by default, it doesn't have `undefined`)
	- But, you can use `Ref<T>`.


# [# Why you should be using Vue 3's Composition API](https://michaelnthiessen.com/why-you-should-use-composition-api/)

- No need for a wrapper div, in Vue 3 you can have more than one top-level element under the template tag.
- dqw



https://app.currents.dev/projects/xFFsR0/insights/specs?sort=flakiness&sort_order=desc - flaky tests