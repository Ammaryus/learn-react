# React Elements

Interacting with the DOM can be a frustrating experience. It requires lots of awkward lines of code where you tell the browser _exactly_ how to create an element with the right properties.

```javascript
const title = document.createElement("h1");
title.className = "title";
title.textContent = "Hello world!";
```

This is frustrating because there is a more declarative way to create elements: HTML.

```html
<h1 class="title">Hello world!</h1>
```

Unfortunately we can't use HTML inside JavaScript files. HTML can't create elements dynamically as a user interacts with our app. This is where React comes in:

```jsx
const title = <h1 className="title">Hello world!</h1>;
```

This variable is a _React element_. It's using a special syntax called [JSX](https://reactjs.org/docs/introducing-jsx.html) that lets us write HTML-like elements within our JavaScript.

### Technical sidenote

JSX is _not JavaScript_. It's an extra addon to make writing React elements more like writing HTML. This means browsers don't understand it. React apps use a tool called [Babel](https://babeljs.io/) to turn this non-standard syntax into regular JS function calls that the browser can run.

The example above will be transformed into:

```javascript
const title = React.createElement("h1", { className: "title" }, "Hello world!");
```

This function call will return an object that describes your element:

```javascript
// over-simplified for examples sake
const title = {
  type: "h1",
  props: {
    className: "title",
    children: "Hello world!",
  },
};
```

React builds up one big tree structure of all these element objects that represents your entire app. It then uses this tree to create the actual DOM elements for you. (This is called the [virtual DOM](https://reactjs.org/docs/reconciliation.html), but you don't need to worry about that right now)

It can be helpful to remember that the HTML-like syntax is really normal function calls that return objects.

### Important warning

Since JSX is closer to JS than HTML **we have to use the camelCase versions of HTML attributes**: `class` becomes `className`, `for` becomes `htmlFor` and `tabindex` becomes `tabIndex` etc.

Also self-closing tags (like `<img>`) must have a closing slash: `<img />`. This is optional in HTML but required in JSX.

[Next section](/02-component-proponent)
