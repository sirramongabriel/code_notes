##JavaScript

####The Object Model
---
*Class-based vs. prototype-based languages*


Class-based object-oriented languages, such as Java and C++, are founded on the concept of two distinct entities: classes and instances.

A class defines all of the properties (considering methods and fields in Java, or members in C++, to be properties) that characterize a certain set of objects. A class is an abstract thing, rather than any particular member of the set of objects it describes. For example, the Employee class could represent the set of all employees.

An instance, on the other hand, is the instantiation of a class; that is, one of its members. For example, Victoria could be an instance of the Employee class, representing a particular individual as an employee. An instance has exactly the same properties of its parent class (no more, no less).

A prototype-based language, such as JavaScript, does not make this distinction: it simply has objects. A prototype-based language has the notion of a prototypical object, an object used as a template from which to get the initial properties for a new object. Any object can specify its own properties, either when you create it or at run time. In addition, any object can be associated as the prototype for another object, allowing the second object to share the first object's properties.

---

source: [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Details_of_the_Object_Model) 

---

#### Create a DOM element
---

How to create a new element and attach it to the DOM tree.

Use the ```createElement()``` method for creating a DOM element:

```javascript
var el = document.createElement('div');
```
<br>
Fill the new element with any HTML content:

```javascript
el.innerHTML = '<p>Hello World!</p>';
```
<br>
Alternatively, use DOM methods for creating content nodes and append them to the new element. This approach requires more code, and is in general slower or equally fast as working with innerHTML:

```javascript
var textnode = document.createTextNode('Hello World!');
el.appendChild(textnode); 
```
<br>
"el" can now be inserted into the DOM tree:

```javascript
document.body.appendChild(el);
```

---

source: [plainjs.com](https://plainjs.com/javascript/manipulation/create-a-dom-element-51/)

---

####Replace a DOM element

---

Remove an element from the DOM tree and insert a new one in its place.

Replacing one element with another by use of the cross-browser safe DOM method ```replaceChild()```

```javascript
// select the element that will be replaced
var el = document.querySelector('div');

// <a href="/javascript/manipulation/creating-a-dom-element-51/">
//  create a new element</a> that will take the place of "el"
var newEl = document.createElement('p');
newEl.innerHTML = '<b>Hello World!</b>';

// replace el with newEL
el.parentNode.replaceChild(newEl, el);

```
<br>
---

####Unwrap a DOM element

---

Remove the parents of an element from the DOM, leaving the element's content in place.

How to unwrap an element with cross browser safe DOM methods:

```javascript
// select element to unwrap
var el = document.querySelector('div');

// get the element's parent node
var parent = el.parentNode;

// move all children out of the element
while (el.firstChild) parent.insertBefore(el.firstChild, el);

// remove the empty element
parent.removeChild(el);
```
<br>
The code is straight forward and much faster than the corresponding jQuery's method ```$.unwrap()```.
<br>
---

####Get & Set the HTML content of an element

---

Read or write the HTML content of an element.

The element property innerHTML is used for getting and setting the HTML content of en element in vanilla JavaScript:

```javascript
var el = document.querySelector('div');

// get HTML content
console.log(el.innerHTML);

// set HTML content
el.innerHTML = '<p>Hello World!</p>'
```
<br>
jQuery's ```$.html()``` method does exactly that in the background.
<br>
---

####Wrap an HTML structure around an element

---
How to use a given container as wrapper for another DOM element.

Wrap a given element in a new container element using plain JavaScript:

```javascript

// element that will be wrapped
var el = document.querySelector('div.wrap_me');

// create wrapper container
var wrapper = document.createElement('div');

// insert wrapper before el in the DOM tree
el.parentNode.insertBefore(wrapper, el);

// move el into wrapper
wrapper.appendChild(el);

```
<br>
The same procedure in the form of a helper function:

```javascript
function wrap(el, wrapper) {
    el.parentNode.insertBefore(wrapper, el);
    wrapper.appendChild(el);
}

// example: wrapping an anchor with class "wrap_me" into a new div element
wrap(document.querySelector('a.wrap_me'), document.createElement('div'));

```
<br>

