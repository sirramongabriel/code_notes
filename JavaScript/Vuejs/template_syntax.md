## Template Syntax

Vue.js uses an HTML-based template syntax that allows you to declaratively bind the rendered DOM to the underlying Vue instance’s data.

#### Interpolations

<b>Text</b>

Text interpolation using Mustache syntax:

```javascript
<span>Message: {{ message }}</span>
```

Being reactive means that ```message``` will be updated whenever the data object's ```message``` property changes.

You may also perform one-time interpolations that do not update on data change by using the [```v-once directive```](https://vuejs.org/v2/api/#v-once), but this will affect any binding on the same node:

```javascript
<span v-once>This will never change: {{ message }}</span>
```
<br>
<b>Raw HTML</b>

The dobule mustaches interprets the data as plain text, not HTML. In order to output real HTML, you will need to use the ```v-html``` directive: 

```javascript
<p>Using mustaches: {{ rawHtml }}</p>
<p> Using v-html directive: <span v-html="rawHtml"></span></p>
```
<p>
You cannot use ```v-html``` to compose template partials, because Vue is not a string-based templating engine. Instead, components are preferred as the fundamental unit for UI reuse and composition.
</p>

<p><b>Note:</b>
Dynamically rendering arbitrary HTML on your website can be very dangerous because it can easily lead to XSS vulnerabilities. Only use HTML interpolation on trusted content and never on user-provided content.
</p>

<br>
<b>Attributes</b>

Mushatches cannot be used inside of HTML attribtues. Instead, use a [```v-bind directive```](https://vuejs.org/v2/api/#v-bind).

```javascript
<div v-bind:id="dynamicId"></div>
```

In the case of boolean attributes, where their existence implies ```true```, ```v-bind``` works diffrently.

```javascript
<button v-bind:disabled="isButtonDisabled"></button>
```
if ```isButtonDisabled``` is ```null```, ```undefined``` or ```false```, the ```disabled``` attribute will not even be included in the rendered ```<button>``` element.

<br>
<b>Using JavaScript Expressions</b>
Vue.js supports the full power of JavaScript expressions inside all data bindings.

```javascript
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div v-bind:id=" 'list-' + id"></div>
```

These expressions will be evaluated as JavaScript in the data scope of the owner Vue instance. One restriction is that a binding can only contain a single expression. The following will not work:

```javascript
<!-- this is a statement, not an expression: -->
{{ var a = 1 }}

<!-- flow control won't work either, use ternary expressions -->
{{ if (ok) { return message } }}
```
<b>Note:</b> Template expressions are sandboxed and only have access to a whitelist of globals such as ```Math``` and ```Date```. You should not attempt to access user defined globals in template expressions.

<br>
#### Directives

Directives are special attributes with the ```v-``` prefix. Directive attribtue values are expected to be a single JavaScript expression (with the exception of ```v-for```. A directive's job is to reactively apply side effects to the DOM when the value of its expression changes. 

```javascript
<p v-if="seen">Now you see me</p>
```
 Here, the ```v-if``` directive would remove/insert the ```<p>``` element based on the truthiness of the value of the expression ```seen```.
 
 <br>
 <b>Arguments</b>
 
Some directives can take an “argument”, denoted by a colon after the directive name. For example, the v-bind directive is used to reactively update an HTML attribute:

```javascript
<a v-bind:href="url">...</a>
```

Here href is the argument, which tells the v-bind directive to bind the element’s href attribute to the value of the expression url.

Another example is the v-on directive, which listens to DOM events:

```javascript
<a v-on:click="doSomething">...</a>
```

Here the argument is the even name to listen to. 

<br>
<b>Modifiers</b>

Modifiers are special postfixes denoted by a dot, which indicate that a directive should be bound in some special way. For example, the .prevent modifier tells the v-on directive to call event.preventDefault() on the triggered event:

```javascript
<form v-on:submit.prevent="onSubmit">...</form>
```

<br>
<b>Shorthands</b>

Vue.js provides special shortahnds for two of the most often used directives, 
```v-bind``` and ```v-on```:

<b>v-bind Shorthand</b>

```javascript
<!-- full syntax -->
<a v-bind:href="url"> ... </a>

<!-- shorthand -->
<a :href="url"> ... </a>
```
<b>v-on Shorthand</b>

```javascript
<!-- full syntax -->
<a v-on:click="doSomething"> ... </a>

<!-- shorthand -->
<a @click="doSomething"> ... </a>
```