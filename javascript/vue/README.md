## What *is* Vue?
[Vue](https://vuejs.org/) is a **progressive framework** written in javascript to build user interfaces. The core library is focused on the **View layer** of the MVC model only, and it's easy to integrate with other libraries or existing projects. Do you want a deeper dive into frameworks and why you should pick Vue? Check out this [comparison of Vue against other modern frameworks](https://vuejs.org/v2/guide/comparison.html).

## How do I use it?
To use Vue, you need to load it as a script, or in your project as a package.
### Use Via Package (Recommended)
Make sure you have node/npm installed (and create a project directory, gulpfile, and package.json), then run the following command in your terminal:
```
# latest stable
$ npm install vue
```
### Use Via Script
All you need to do is include this link right before your ```</body>``` tag.
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.2.6/vue.min.js"></script>
```

## Rendering Data
Vue uses a straightforward template syntax to render data to the DOM, and support components. Take the following trivial example (it should be noted I'm using the **package** method of installing Vue):
```
/* In index.html */
/*****************/
<html>
  <body>
    <!-- This is the "placeholder" for our application -->
    <div id="app"></div>
    <!-- These are the brains of our application -->
    <script src="main.js"></script>
  </body>
</html>

/* In main.js */
/**************/
import Vue from "vue" // I can do this because I have the package downloaded via npm.
import App from "app.vue"

var app = new Vue({
  el: '#app',
  render: h => h(App)
})

/* In app.vue (The Component) */
/******************************/
<!-- <template>s are used in Vue to categorize renderable chunks of data, -->
<!-- and every component is encased in them. -->
<template>
  <div id="app">
    {{ message }}
  </div>
</template>

<script>
// We have to return at least a blank object by default
export default {
  data() {
    return {
      message: 'Hello Vue!'
    }
  }
}
</script>
```

This will output the following in your index.html page:
```
Hello Vue!
```

## Conditionally Rendering Data
Take the following abstract Vue component:
```
/* In app.vue (The Component) */
/******************************/
<template>
  <div id="app">
    <!-- v-if="variableName" says "Render this thing if the variableName inside the quotes is true" -->
    <p v-if="message">Hello Vue, message is true!</p>
    <!-- v-else will do the opposite. "Render this thing if the variableName inside the v-if above is false" -->
    <p v-else>Hello Vue, sorry to say that message is false.</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      /* Notice how in this example, we are keying off of a boolean
       * value, not a string. This boolean value is being used in
       * the <template> up top to determine if the <p> should show. */
      message: true
    }
  }
}
</script>
```

This code will output ```Hello Vue, message is true!```, unless message was false, in which case it would render ```Hello Vue, sorry to say that message is false.```

## Loops
Take the following abstract Vue component:
```
<template>
  <div id="app">
    <ol>
      <li v-for="todo in todos">
        {{ todo.text }}
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  data() {
    return {
      /* So now we're returning an array - we need to loop through
       * our entries in the view (Vue? hah!) */
      todos: [
        { text: 'Learn JavaScript' },
        { text: 'Learn Vue' },
        { text: 'Build something awesome' }
      ]
    }
  }
}
</script>
```

This code will output
```
1. Learn JavaScript
2. Learn Vue
3. Build something awesome
```

## User Input
Handling user input is so easy in Vue - it shouldn't even work!
```
<template>
  <div id="app">
    <p>{{ message }}</p>
    <!-- v-model essentially means "I'll be responsible for manipulating the variable in these quotes" -->
    <input v-model="message">
  </div>
</template>

<script>
export default {
  data() {
    return {
      /* Back to our old friend, 'Hello Vue!', but
       * this value can now be modified by the input
       * using v-model, because it's using this variable
       * in the v-model. */
      message: 'Hello Vue!'
    }
  }
}
</script>
```

You'll notice that when you compile this code, you'll get a message then a text input box beneath it, both displaying the text ```Hello Vue!``` You can type in the input, and the message is updated as well. This is due to **reactivity** in Vue.

## Composing Views With Components
The components in Vue allow us abstraction to build large-scale applications that are agnostic of what they are contained in. Using them takes a little bit more time, but the payoff is immense when the layout gets complex or modular.

Take the follow Vue components point-of-view for an app:
```
/* In navigation.vue */
/*********************/
<template>
  <nav>
    <!-- Test links, so src doesn't matter -->
    <a src="#">Home</a>
    <a src="#">Profile</a>
  </nav>
</template>
<script>
export default {
  data() {
    return {
    }
  }
}
</script>

/* In app.vue */
/**************/
<template>
  <div id="app">
    <navigation></navigation>
    <p>{{ message }}</p>
  </div>
</template>

<script>
// We have to import the navigation component to use it here.
import Navigation from "navigation.vue"

export default {
  /* This is how we tell Vue we have custom
   * components to render - the components: {}
   * return object. */
  components: { Navigation },
  /* And now we just send back our data function
   * like normal, filled with our message. */
  data() {
    return {
      message: 'Hello Vue!'
    }
  }
}
</script>
```

Now when you render this app - you'll see both the navigation and the message!


## Reactivity
Vue does a much better job of this than me, so check out their [Reactivity In Depth](https://vuejs.org/v2/guide/reactivity.html) article!

## Lifecycle
Check out what [Vue has to say about their Lifecycle](https://vuejs.org/v2/guide/instance.html#Lifecycle-Diagram) - it's very pretty!
