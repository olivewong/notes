# Vue

## Basics

- Can use JSX or templates (HTML-like)
- Declarative (data inputs always produce same outputs)
- Not made by a megacorporation like React
- Props: `:users`
-

### Reactive

- data() object: if used in template, `{{ likes }}` accessed, it will rerender if something inside here changes
-

## Vs. React

- VueX (state management): React's Redux
- `v-if` `v-else` directives: JSX's ternary `{ value ? "if" : "else" }`
- `@click="handler"`: JSX's `onClick={handler}`
  - also v-on click?
  - `handler()` can be defined in the setup function
- `precomputed` like useMemo
- lifecycle hooks: `onMounted`
  - like a useEffect with no dependency array that only runs once once mounted

## VueX

- State management - SR uses this

### Store

- State: the info you're sharing throughout the app (ex. `users`, `registrations: [{id: x, name: x}]`)
- Mutations: SYNCHRONOUS ways to update the state (setCurrentUser(state, payload) => state.currentUser = "fred")
- Actions: ASYNCHRONOUS ways to update state (ex. fetch from API -

  ```
  actions: {
      async setCurrentUser(state, payload) =>
          await fetch(url, headers, ...)`
          j = await json
          state.commit("setCurrentUser", j.User")
  }
  ```

- Modules
- Getters: Ways you can grab information and store it throughout your app
  - ex. `getCurrentUser: (state) => state.currentUser`

#### Grabbing stuff from the store

use $store
Component:
### Dispatching: using the actions
th

```

export default {
    name: "home",
    data: () => ({
        user: ''
    }),
    computed: {
        user() {
            return this.$store.getters.getCurrentUser // prevents race condition with mounted
        }
    },
    methods: {
        // dispatches when button clicked
        addUser() {
            this.$store.dispatch("setCurrentUser");
        }
    },
    mounted: () => {
       //  this.user = this.$store.getters.getCurrentUser; race condition
    }
}



in component:
<button onclick="adduser" /> or sth

```

Store:

```

<template>
    <div id="registration">
        <h3>Register here</h3>
        <hr>
        <div class="row" v-for="user in users">
            <h4>{{ user.name }}</h4>
            <button @click="registerUser(user)">Register</button>
        </div>
    </div>
</template>

<script>
    export default {
        computed: {
          users() {
              return this.$store.getters.unregisteredUsers;
          }
        },
        methods: {
            registerUser(user) {
                this.$store.dispatch('register', user.id);
            }
        }
    }
</script>

```

```

```

```

```
