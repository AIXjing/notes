# Vue3 and Javascript

### How to create a dynamic router on a page

[Vue-router Programmatic Navigation](https://router.vuejs.org/guide/essentials/navigation.html)

```js
const userId = '123'
router.push({ name: 'user', params: { userId } }) // -> /user/123
router.push({ path: `/user/${userId}` }) // -> /user/123
// This will NOT work
router.push({ path: '/user', params: { userId } }) // -> /user
```

In my case,
``` js
// In the component of Tombview
methods: {
    open: function (userId) {
      router.push({name: 'userTomb', params: {userId}})
    }
```
[Dynamic Route Matching](https://router.vuejs.org/guide/essentials/dynamic-matching.html#reacting-to-params-changes)
```js
// in the "router.js" file
const routes = [
    {name: 'userTomb', path: '/userTomb/:userId', component: userTomb}
]
// : refers to params
```

```js
// In the new router page
const User = {
  template: '<div>User {{ $route.params.id }}</div>'
}
```

In my case,
```js
{{ $route.params.userId }} // use this code to pass dynamic paramters.
```
When it is used in <script></script>
```js
{{ this.$route.params.userId }} 
```

