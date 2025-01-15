# Introduction

Welcome! **React** is a JavaScript library for creating web apps called single-page applications.

Single-page applications load as a single web page and dynamically update parts as you interact with it.

React simplifies the development of web apps by allowing us to break code into reusable components.

You can picture those components as reusable blocks of code like bricks that you can use to build your application.

Let's look at a simple example, which returns _Welcome to React_.


```jsx
function Welcome() {
	return "Welcome to React";
}
```

A component in React is just a function that returns something you want to show on the screen.

In React, we usually create components using the modern ES6 syntax for creating functions.

However, both do the same thing. They're just different ways of writing a function that returns something React will display.

```jsx
const WelcomeToTheNewWorld = () => {
	return "Hello, new world";
};

function WelcomeToTheOldWorld() {
	return "Hello, old world";
}
```

From now on, we'll use the **ES6 syntax** for writing components. We’ll stick with the newer one because it’s shorter and more modern.

If you see the old style somewhere, it’s still perfectly fine to use.

Think of a component like a recipe: it tells React what to "cook" (or display), and you can reuse that recipe whenever you need it.

Whatever we return will be displayed once the component is rendered.

Another way to think about a component is as custom HTML tags with superpowers.

The function's name defines the component, allowing you to reuse it just like an HTML tag but with added functionality and flexibility.

Typically components start with an uppercase letter so that we can tell them apart from regular HTML tags.

Unlike normal JavaScript functions, React components are capitalized.

In React, a component doesn’t just return plain text. It can return **HTML**, too.

We can create a component that returns an HTML heading with a certain text.

```jsx
const WelcomeComponent = () => {
	return <h1>Hello, world</h1>
};
```

What we see here is **JSX**, which looks like HTML but isn’t. JSX is a special syntax that React uses to write HTML-like code inside JavaScript.

Despite JSX not being real HTML, JSX looks and feels like HTML. It works similarly, so if you know HTML, JSX will be familiar to you.

React converts JSX into real HTML, so your browser can understand and display it just like normal HTML.

React generates and then inserts HTML into our webpage's preexisting HTML container, like a `div` element.

```html
<html>
	<body>
		<div id="root">loading</div>
	</body>
</html>
```

As a next step, we need to link to our JavaScript file. When using React, typically, we do that within the `head` element.

```html
<html>
	<head>
		<script src="./index.js"></script>
	</head>
	<body>
		<div id="root">loading</div>
	</body>
</html>
```

By specifying `type="module"` in the `<script>` tag, we tell the browser that we'll use features like imports and exports.

It’s required for React to work correctly.

```html
<html>
	<head>
		<script type="module" src="./index.js"></script>
	</head>
	<body>
		<div id="root">loading</div>
	</body>
</html>
```

That’s it! When working with React, we typically only need a very basic HTML page.

React will render the components we add inside the `div` element with the ID `"root"` and replace the _loading_ placeholder.

After setting up the basic HTML code, we switch to our `index.jsx` file to work on the React code.

In the HTML file, we reference our React file as `index.js`, but the file ends in `.jsx` because it contains both JavaScript and HTML-like JSX.

To make React work as expected, we need to import the **React** package into your JavaScript file.

```jsx
import React from "react";
```

Next, we import the `createRoot` function from the `react-dom/client` package, which can render our React components.

This function allows us to initialize a root in the DOM, where React can efficiently manage and render its components.

```jsx
import { createRoot } from "react-dom/client";
```

Before using the `createRoot` function, we need an HTML element as the basis for that root.

Use `document.getElementById` to get the `div` element with the ID `"root"`.

```jsx
const rootElement = document.getElementById("root");
```

Now, we can call the `createRoot` function and pass the reference to the `div` element as the parameter.

We save the returned value in a variable called `root`, which gives us control over rendering components within the specified DOM element.

```jsx
const root = createRoot(rootElement);
```

To render our component, we call the `render` function on the newly created `root` object.

```jsx
root.render();
```

Last but not least, we need to pass the component we want to render as an argument to the function.

We need to wrap the component's name in angular brackets `<>`, like `<MyComponent />`, to render it in JSX.

```jsx
root.render(<MyComponent />);
```

# Components

In React, organizing components into their own files is a good practice.

Creating a file per component keeps our project nice and tidy.

We need to import `React` from the React package in every file we use for React.

After we made sure to import `React`, we can create our functional component.

To use the component elsewhere, we need to export it.

We use the default export `export default Greeting` to make the `Greeting` component available in other files.

```jsx
import React from "react";

const Greeting = () => {
  return <h1>Hello, there!</h1>;
};

export default Greeting;
```

To import the component, we use `import` followed by its name, then the path to the file after the `from` keyword.

`./` means _the current folder_ in a file path. It tells the code to look for the file in the same folder as the current file.

Lastly, we can render the component in the `root` element.

However, we can create as many components as we want.

For example, we can create a `Greeting` component next to our `App` component. We do this in another file to keep everything nice and tidy.

```jsx
import React from "react";
import { createRoot } from "react-dom/client";
import App from "./App";

const rootElement = document.getElementById("root");
const root = createRoot(rootElement);
root.render(<App />);
```

```jsx
import React from "react";

const App = () => {
  return <h1>Welcome to my React app!</h1>;
};

export default App;
```

```jsx
import React from "react";

const Greeting = () => {
  return <h1>Hello, there!</h1>;
};

export default Greeting;
```

We can now, use the new `Greeting` component inside the `App` component.

If we want to use a component from another file, we must import it via the `import` statement we already know.

Every component can only return one element. If we want to include the new component, we must wrap the existing JSX in an element.

Add a `div` element around the JSX that the component returns.

```jsx
import React from "react";
import Greeting from "./Greeting";

const App = () => {
	return (
		<div>
			<h1>Welcome to my React app!</h1>
		</div>
	);
};

export default App;
```

If we return more than one line of JSX, we wrap the returned JSX inside parentheses.

If we return a wrapper element, like the `div` element, we can add as many elements as we want inside.

It's time to add the `Greeting` component. We add it like any other element.

Add the imported `Greeting` element to display the `Greeting` component inside the `App` component.

```jsx
import React from "react";
import Greeting from "./Greeting";

const App = () => {
	return (
	    <div>
			<h1>Welcome to my React app!</h1>
		    <p>I'm happy that you are here.</p>
		    <Greeting />
		</div>
	);
};

export default App;
```

A component is a building block, just like an element. We can add a component as often as we want.

The `App` component can display the `Greeting` component as often as we want.

We can also put multiple components into one file.

If we want to use a component that was defined in the same file, we can use it directly.

Components are like the building blocks we use to build our React app, so we can use them as often as we want.

We can also export multiple classes using **named exports** instead of a default export.

We put the `export` keyword in front of every component we want to export.

```jsx
import React from "react";

export const Article = () => {
	return (
		<div>
			<h2>Loading Article...</h2>
			<p>Content is on its way. Please wait.</p>
		</div>
	);
};
```

To import multiple named exports, we list each item we want to import in curly braces.

We can also decide to import only one of the exported components.

When we export multiple components, we can also choose to make one of the exports the default export.

To import a named export alongside a default exported component, we list them in curly braces and add them to the same import statement.

Alongside the `Header` component, import the `Recipe` component as a named export from the `Components` file.

```jsx
import React from "react";
import Header, { Recipe } from "./Components";

const App = () => {
	return (
		<div>
			<Header />
			<Recipe />
		</div>
	);
};

export default App;
```

We can ignore the default export and import only named exports instead.

# JSX

We use JSX to create HTML-like code in JavaScript when using React. It looks and feels like HTML, but it’s actually JavaScript.

JSX is so helpful because it makes our components more readable and familiar.

JSX uses syntax that is almost identical to HTML. HTML elements are created in JSX as they are in HTML.

We can only return one element when creating a component using JSX.

However, we can add multiple elements inside a `div` element and return the `div` element.

We can either directly return a tag or use parentheses `()` to return a multiple-line JSX snippet.

If the JSX spans multiple lines, it’s better to wrap it in parentheses for clarity.

If we return a single line, we can just add the JSX after the `return` statement to return it.

Even though JSX looks like HTML, it’s actually JavaScript under the hood. Using JavaScript to define our layout comes with some benefits.

Like in plain JavaScript, we can perform calculations in JSX.

Any such embedded expressions need to go between curly braces `{}`.

```jsx
const App = () )> {
	return <h1> {15 + 27} </h1>;
};
```

But there's much more than simple calculation. JSX gives us the full power of JavaScript, and we can also reference variables inside JSX.

For example, we can display variables inside an embedded expression.

```jsx
const name ) "Alice";

const App = () )> {
	return <h1> {name} </h1>;
};
```

We can perform calculations, reference variables, or use any other valid JavaScript expression inside the curly braces.

When using JSX, we can use all the tags we already know from regular HTML, including `<div>`, `<h1>`, `<p>`, and `<footer>`.

Some elements are self-closing, which means they only have a single tag that ends with a slash `/`.

Unlike HTML, JSX requires any self-closing tag to end with a slash `/`.

We can also store JSX inside a variable.

This is useful when you want to write JSX in some part of your code and then refer to it somewhere else in a more readable way.

We can also reference other JSX elements using a JSX expression with curly braces `{}`

To include multiple JSX expressions within a single component, we need to use curly braces for each expression.

We can even use embedded expressions to pass values into a JSX element's attributes.

Embedded expressions are a powerful tool in our React toolkit and allow for nifty interactions with your app's user interface.

# Properties

In React, properties, or props for short, are a way to pass data to a component.

They allow components to be dynamic and customizable.

So far, we've created components without passing any arguments, meaning they always display the same static content.

However, to make components more dynamic, we can pass `props` as arguments to the components to customize what they show.

```jsx
const Greeting = (props) => {};
```

We pass one argument, `props`, representing an object that holds all the data passed to the component in one place.

In the component, we access props as we access any passed parameters.

As `props` is an object, we can access the properties of that object.

To access the name, we use `props.name`.

We can also use props inside JSX.

Display the name by accessing the `name` property of the `props` object inside the curly braces by coding `props.name`.

```jsx
const Greeting = (props) => {
	return <h1>Hi, {props.name}!</h1>;
};
```

When using JavaScript inside JSX, we need to put the JavaScript inside curly braces.

To pass a property to a component, add it as an attribute in the component’s tag, similar to setting attributes in HTML.

First, define the attribute's name, then assign it a value inside quotes.

We're not limited to only passing one property. If we want to pass multiple properties, we can do so.

We can access every passed property as we've done before.

If we pass multiple properties, they become part of the `props` object, allowing us to access each one through it.

Log the `props` object to see what properties have been passed and their values.

We can pass other types as properties as well, such as numbers.

When passing non-strings, like numbers, we need to wrap the value in curly braces `{}`.

When accessing a passed property, the type doesn’t matter; whether it’s a number or a string, we access them all by their key.

Passing booleans works similarly.

However, in React, we can't render a boolean directly as a string. We won't see anything if we try to render a boolean value directly.

If we want to render a boolean (or a number) as a string, we can use the `String(value)` to convert a given variable called `value` to a string.

Use the `String` function and pass `props.nice` as the argument to get a string back that we can display.

```jsx
const Greeting = (props) => {
	return (
		<div>
			<p>Are you nice? {String(props.nice)}</p>
		</div>
	);
};
```

