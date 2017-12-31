## Computed Properties and Watchers

#### Computed Properties

In-template expressions are very convenient, but they are meant for simple operations. Putting too much logic in your templates can make them bloated and hard to maintain. For example:

```javascript
<div id="example">
  {{ message.split('').reverse().join('') }}
</div>
```
At this point, the template is no longer simple and declarative.

The problem is made worse when you want to include the reversed message in your template more than once.

That’s why for any complex logic, you should use a computed property.

<br>
<b>Basic Example</b>

```html
<div id="example">
  <p>Original message: "{{ message }}"</p>
  <p>Computed reversed message: "{{ reversedMessage }}"</p>
</div>
```

```javascript
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
    // a computed getter
    reversedMessage: function () {
      // `this` points to the vm instance
      return this.message.split('').reverse().join('')
    }
  }
})
```

Here we have declared a computed property ```reversedMessage```. The function we provided will be used as the getter function for the property ```vm.reversedMessage```:

```javascript
console.log(vm.reversedMessage) // => 'olleH'
vm.message = 'Goodbye'
console.log(vm.reversedMessage) // => 'eybdooG'
```

You can data-bind to computed properties in templates just like a normal property. Vue is aware that ```vm.reversedMessage``` depends on ```vm.message```, so it will update any bindings that depend on ```vm.reversedMessage``` when ```vm.message``` changes. And the best part is that we’ve created this dependency relationship declaratively: the computed getter function has no side effects, which makes it easier to test and understand.

<br>
<b>Computed Caching vs Methods</b>

You may have noticed we can achieve the same result by invoking a method in the expression:

```html
<p>Reversed message: "{{ reverseMessage() }}"</p>
```

```javascript
// in component
methods: {
  reverseMessage: function () {
    return this.message.split('').reverse().join('')
  }
}
```

Instead of a computed property, we can define the same function as a method instead. 

For the end result, the two approaches are indeed exactly the same. However, the difference is that computed properties are cached based on their dependencies. 

A computed property will only re-evaluate when some of its dependencies have changed. This means as long as message has not changed, multiple access to the ```reversedMessage``` computed property will immediately return the previously computed result without having to run the function again.

This also means the following computed property will never update, because ```Date.now()``` is not a reactive dependency:

```javascript
computed: {
  now: function () {
    return Date.now()
  }
}
```

In comparison, a method invocation will always run the function whenever a re-render happens.

Why do we need caching? Imagine we have an expensive computed property ```A```, which requires looping through a huge Array and doing a lot of computations. Then we may have other computed properties that in turn depend on ```A```. Without caching, we would be executing ```A```’s getter many more times than necessary! In cases where you do not want caching, use a method instead.

<br>
<b>Computed vs Watched Property</b>

Vue does provide a more generic way to observe and react to data changes on a Vue instance: watch properties. 

It is often a better idea to use a computed property rather than an imperative watch callback. Consider this example:

```html
<div id="demo">{{ fullName }}</div>
```

```javascript
var vm = new Vue({
  el: '#demo',
  data: {
    firstName: 'Foo',
    lastName: 'Bar',
    fullName: 'Foo Bar'
  },
  watch: {
    firstName: function (val) {
      this.fullName = val + ' ' + this.lastName
    },
    lastName: function (val) {
      this.fullName = this.firstName + ' ' + val
    }
  }
})
```

This code above is imperative and repetitive. Compare it with a computed property version:

```javascript
var vm = new Vue({
  el: '#demo',
  data: {
    firstName: 'Foo',
    lastName: 'Bar'
  },
  computed: {
    fullName: function () {
      return this.firstName + ' ' + this.lastName
    }
  }
})
```
<br>
<b>Computed Setter</b>

Computed properties are by default getter-only, but you can provide a setter when needed like so:

```javascript
// ...
computed: {
  fullName: {
    // getter
    get: function () {
      return this.firstName + ' ' + this.lastName
    },
    // setter
    set: function (newValue) {
      var names = newValue.split(' ')
      this.firstName = names[0]
      this.lastName = names[names.length - 1]
    }
  }
}
// ...
```

Now when you run ```vm.fullName = 'John Doe'```, the setter will be invoked and ```vm.firstName``` and ```vm.lastName``` will be updated accordingly.


####Watchers

While computed properties are more appropriate in most cases, there are times when a custom watcher is necessary. That’s why Vue provides a more generic way to react to data changes through the watch option. This is most useful when you want to perform asynchronous or expensive operations in response to changing data.

example:

```html
<div id="watch-example">
  <p>
    Ask a yes/no question:
    <input v-model="question">
  </p>
  <p>{{ answer }}</p>
</div>
```

```html
<!-- Since there is already a rich ecosystem of ajax libraries    -->
<!-- and collections of general-purpose utility methods, Vue core -->
<!-- is able to remain small by not reinventing them. This also   -->
<!-- gives you the freedom to use what you're familiar with. -->
<script src="https://cdn.jsdelivr.net/npm/axios@0.12.0/dist/axios.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/lodash@4.13.1/lodash.min.js"></script>
<script>
var watchExampleVM = new Vue({
  el: '#watch-example',
  data: {
    question: '',
    answer: 'I cannot give you an answer until you ask a question!'
  },
  watch: {
    // whenever question changes, this function will run
    question: function (newQuestion) {
      this.answer = 'Waiting for you to stop typing...'
      this.getAnswer()
    }
  },
  methods: {
    // _.debounce is a function provided by lodash to limit how
    // often a particularly expensive operation can be run.
    // In this case, we want to limit how often we access
    // yesno.wtf/api, waiting until the user has completely
    // finished typing before making the ajax request. To learn
    // more about the _.debounce function (and its cousin
    // _.throttle), visit: https://lodash.com/docs#debounce
    getAnswer: _.debounce(
      function () {
        if (this.question.indexOf('?') === -1) {
          this.answer = 'Questions usually contain a question mark. ;-)'
          return
        }
        this.answer = 'Thinking...'
        var vm = this
        axios.get('https://yesno.wtf/api')
          .then(function (response) {
            vm.answer = _.capitalize(response.data.answer)
          })
          .catch(function (error) {
            vm.answer = 'Error! Could not reach the API. ' + error
          })
      },
      // This is the number of milliseconds we wait for the
      // user to stop typing.
      500
    )
  }
})
</script>
```