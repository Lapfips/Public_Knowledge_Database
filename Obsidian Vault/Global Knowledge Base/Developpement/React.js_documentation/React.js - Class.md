# Intro to React

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
const App = () => {
	return <h1> {15 + 27} </h1>;
};
```

But there's much more than simple calculation. JSX gives us the full power of JavaScript, and we can also reference variables inside JSX.

For example, we can display variables inside an embedded expression.

```jsx
const name = "Alice";

const App = () => {
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

# Buttons

Let's explore how to make our React apps more interactive.

First, add a button with some text.

```jsx
const App = () => {
	return (
		<div>
			<h1>Click the button</h1>
			<button>Click me</button>
		</div>
	);
};
```

We can add the `onClick` event handler to handle clicks on the button.

In React, it follows camelCase, so it becomes `onClick`. This is slightly different from the HTML/JavaScript click handler `onclick`.

To run JavaScript, we add an embedded expression.

To call a function, we need to reference it without parentheses. First, we define an arrow function and assign it to a variable.

We then pass that variable to `onClick` as a reference, so the function runs when the button is clicked.

We can also run JavaScript directly inside the embedded expression.

However, it's executed without clicking the button because the function is called immediately instead of being passed as an event handler.

This is usually not what we want. To avoid this, we wrap the code in an arrow function.

The arrow function doesn’t run right away. It waits until the event triggers it. Now, the code will be executed on button click.

# State

Often, we need to remember certain things. Like how many times a button has been clicked.

We'll now learn about **state**, a special way in React to make components remember values.

To render JavaScript, we need an embedded expression.

We use state to make React components remember values between renders, like tracking how many times a button has been clicked.

Import `useState` from the `"react"` package. As this is a named export, we use `{ }` to specify which part we want to import.

```jsx
import React, { useState } from "react";
```

Defining state looks a bit funky. We use an array structure and put the name of the variable we want to use inside the array.

Next, we assign a value with the `useState` function.

`useState` is a special function (called a hook) in React that allows components to remember and update values over time.

```jsx
const [count] = useState();
```

We pass the initial value we want to set as argument to the `useState` function.

We can now display the value, but not update it yet. We define a second array entry, `setCount`, to update a state.

This function is used specifically to change the value of `count` and trigger a re-render.

We can use the `setCount` function to update the `count` variable automatically when we call the function and pass a new value as the argument.

Whenever `setCount` is called the `count` variable is updated and re-rendered.

```jsx
const App = () => {
	const [count, setCount] = useState(0);

	const handleClick = () => {
		console.log("Button clicked");
		setCount(count+1);
	};

	return (
		<div>
			<p>You clicked the button {count} time(s).</p>
			<button onClick={handleClick}>Click me</button>
		</div>
	);
};
```

Hooks, such as `useState,` are crucial parts of React. They allow us to add features to components, making them more powerful and interactive.

Using them allows us to remember things. Such as if we have the light turned on or off.

When using React, we're not limited to one state variable. We can have as many as we want.

We can decide the initial value. It can be anything we want.

We're not limited to numbers when it comes to state variables.

Booleans can also be used for state variables.

We can use a non-state variable and render it.

However, when we update a variable that's also rendered, React doesn't update the HTML it displays.

To ensure React renders the updated HTML, we need to use the setter for the state variable.

Never update a state variable directly, but only through the setter.

State updates are asynchronous. When you call the setter function, React schedules the update but doesn’t apply it immediately.

If we use the updated state value right after calling the setter, it may still reflect the previous value.

We'll soon learn about another hook to observe state changes.

For now, remember that hooks, such as `useState`, run asynchronously. We can't know when the variable is updated and the HTML re-rendered.

# Using Stylesheets

What's a sophisticated React app without some beautiful styling?

Let's dive into how to use CSS to style our single-page applications.

When creating a React app, we can use a normal CSS file. Within that file, we can define any CSS rule that we want.

To apply the CSS, we need to import the CSS file. We do this directly in a component.

We can use CSS rules to target an element with a certain ID, as we would when using CSS with HTML.

Now, let's use a rule to target elements with a particular class attached.

In JSX, we use the keyword `className` to apply a class to an element, similar to the `class` attribute in HTML.

Use `className` to set a CSS class on an element in JSX, just like the class attribute in HTML.

```jsx
import "./App.css";

const App = () => {
	return (
		<div>
			<h1>Welcome</h1>
			<div className="box"></div>
		</div>
	);
};
```

We need to link the stylesheet `index.css` in the HTML because the bundler needs this to load our CSS files properly.

We need to always reference an `index.css` file but should not actually use a file with this name.

```jsx
<html>
	<head>
		<script type="module" src="./index.js"></script>
		<link rel="stylesheet" href="./index.css">
	</head>
	<body>
		<div id="root">loading</div>
	</body>
</html>
```

When coding React, we need a bundler, a tool that combines all our files to make the app work.

The bundler requires the link to an `index.css` file. However, we don't need to create the file. The bundler does that for us.

When we import a CSS file in one of our files, the styling will be applied to everything that's rendered.

It doesn't matter which component loads the CSS.

To keep the CSS nicely separated, it's best practice to include only a few global styles, such as general styles, in the `App.css` file.

To avoid styling specific components in the `App.css` file, declare only one rule to target the `body`.

```css
body {
	font-family: Arial, sans-serif;
	background: linear-gradient(to bottom, #FFFFFF, #E0E0E0);
}
```

It's best to create a CSS file for each component and keep styles scoped to that component.

Once we have a dedicated CSS file for a component, we can use this file to define CSS that is specific for this class.

However, if you import a CSS file in a specific component, the CSS will still be applied globally.

To avoid unwanted side effects in other parts of the app, it's best to use component-specific classes and target those.

In React, we can use the passed properties to adapt a generic component to our liking.

Like changing the size of a box.

When we define a property and pass different values to it, we can use that property to customize the generic component later.

A neat way to adapt the design to our liking is to create classes for our elements based on the passed properties.

Use the passed property `size` in the conditional statement to check which size was passed.

We can then adapt the value of the string of the `boxClass` variable.

The `boxClass` variable holds either only the standard `box` class or `box` and a more specific size class.

```jsx
import React from "react";
import "./Box.css";

cosnt Bot = (props) => {
	let boxClass = "box";

	if (props.size === "small") {
		boxClass = "box box--small";
	} else if (props.size === "medium") {
		boxClass = "box box--medium";
	} else if (props.size === "large") {
		boxClass = "box box--large";
	}

	return (
		<div className={boxClass}>
			<span>{props.size}</span>
		</div>
	);
};

export default Box;
```

We can also use a shorter version using template literals and string interpolation.

```jsx
const Box = (props) => {
	return (
		<div className={'box box--${props.size}'}>
			<span>{props.size}</span>
		</div>
	);
};
```

Another great way to create CSS classes on the fly is to use state variables.

Use string interpolation to construct the individual classes based on the state variable `mode`.

```jsx
const App = () => {
	const [mode, setMode] = useState("light");

	const toggleTheme = () => {
		if (mode === "light") {
			setMode("dark");
		} else {
			setMode("light");
		}
	};

	return (
		<div id="app-wrapper" className={'theme-${mode}'}>
			<h1>Welcome to my page</h1>
			<p>Do you want it like this?</p>
			<button onClick={toggleTheme}>Change Theme</button>
		</div>
	);
};
```

# Using Style Properties

Like HTML + CSS, we can use the style property to style specific elements inline without using a dedicated CSS file.

We can do the same in React.

Unlike in HTML, the `style` property doesn't expect a string but an object.

We pass an object that includes the styling rules.

Note the `{{` and `}}` is a combination of a JSX expression and an object.

The rules are defined as an object with key-value pairs.

If we want to add multiple rules, we separate them by comma.

Remember, this is a JavaScript object, as you have seen and used many times before.

Since we use a JavaScript object, we use camel case instead of hyphens.

We can also define the object first and pass a reference to the `style` property.

```jsx
const App = () => {
	const buttonStyle = {color:"white", backgroundColor:"red"};
	return (
		<div>
			<h1>Click the button</h1>
			<button style={buttonStyle}>Click me</button>
		</div>
	);
};
```

# Conditional Rendering

React allows us to change what we display based on the code and the user's input.

Rendering JSX based on certain conditions is called **conditional rendering**.

We can use an `if/else` statement to introduce JavaScript logic into JSX and control what is rendered based on a condition.

We use embedded expressions to embed the JSX into other JSX codes.

This is useful if we want to control smaller dynamic elements while keeping the greater JSX structure intact.

Conditional statements become more relevant when working with properties.

If we don't hardcode a value we test against but pass it as a property, we make the component reusable and useful for other components.

When working with properties, we can go further with conditional rendering to make the component as flexible as possible.

Let's check out how we can decide whether to render something or avoid it.

If we don't want to show an element in a certain condition, we can set it to `null`.

The embedded expression will always render the content that's referenced by the `element` variable.

However, when this variable holds the value `null`, there is nothing to display.

This concept becomes more relevant when working with state variables.

If we transform `showSecret` into a state variable, we can toggle whether to render it with the click of a button.

When working with properties, we can go further with conditional rendering to make the component as flexible as possible.

Rendering JSX based on certain conditions is called **conditional rendering**.

We can move the conditional statement inside the embedded

We can shorten this by using the AND operator to render the `prize` variable only if the condition on the left side evaluates as `true`.

```jsx
const App = () => {
	const [prize, setPrize] = userState(undefined);

	const openMysteryBox = () => {
		setPrize("Your gift");
	};

	return (
		<div>
			<h1>Mystery Box :</h1>
			<p>{prize !== undefined && prize}</p>
			<button onClick={openMysteryBox}>Open</button>
		</div>
	);
};
```

We don't have to render a variable that references JSX. We can directly render JSX, too.

We can also use the logical OR operator. This operator will first try to render the left side.

If the left side evaluates as `falsy`, which are `false`-like values, it will render the right side.

If the left side is `false`, `null`, `undefined`, `0`, `NaN`, or an empty string, the OR operator will return the right side to be rendered.

Set the initial value to an empty string instead of `undefined`.

We can go one step further and only put the variable inside an embedded expression.

If the variable is not `falsy`, React will render it.

A common use case for conditional rendering is to display parts of the elements based on a user action or the result of a calculation.

If we use the AND operator, we can pass a multi-line JSX snippet with one parent and multiple child elements.

```jsx
import React, { useState } from "react";

const App = () => {
	const [showMore, setShowMore] = useState(false);

	const toggleContent = () => {
		setShowMore(!showMore);
	};

	return (
		<div>
			<h1>Our Story</h1>
			<p>We started with a simple idea.</p>
			{showMore && (
				<div>
				    <p>Over time, we grew, learned, and continued to innovate.</p>
			        <p>Today, we're excited about what the future holds!</p>
				</div>
			)}
			<button onClick={toggleContent}>
				{showMore ? "Read Less" : "Read More"}
		    </button>
		</div>
	);
};

export default App;
```

We can use multiple embedded expressions for conditional rendering.

```jsx
const App = () => {
	const [showMore, setShowMore] = useState(false);

	const toggleContent = () => {
		setShowMore(!showMore);
	};

	return (
		<div>
			<h1>Our Story</h1>
			<p>We started with a simple idea.{!showMore && ".."}</p>
			{showMore && (
				<div>
				    <p>Over time, we grew, learned, and continued to innovate.</p>
			        <p>Today, we're excited about what the future holds!</p>
				</div>
			)}
			<button onClick={toggleContent}>
				{showMore ? "Read Less" : "Read More"}
		    </button>
		</div>
	);
};
```

We can add a third embedded expression that returns different text for the button based on how much we are rendering.

Or hide the button entirely after it is clicked once. The possibilities with embedded expressions and conditional rendering are endless.

This is a bit of a brain-twister. If `showMore` is not `true`, we show the button. As soon as it is `true`, we hide it.

```jsx
{!showMore && <button onClick={toggleContent}>Read More</button>}
```

Sometimes, we want to show a radically different UI based on a condition.

Think about a loading state. A loading state might be much, much simpler than the view with all the data loaded and presented.

We can use conditional rendering to display those two states inside an embedded expression.

Based on the `loading` variable, display either a simple loading message or a complex UI with the loaded data.

```jsx
const App = () => {
	const [loading, setLoading] = useState(true);

	return (
		<div>
			{loading ? (
				<p>Loading your data ...</p>
			) : (
				<div>
					<h1>Your Data</h1>
				</div>
			)}
		</div>
	);
};
```

Returning early is a common pattern for conditional rendering based on specific states, such as loading, error, or authentication state.

We can use multiple early returns to handle several scenarios in a single component.

First, check if the data is still loading, then check if an error occurred, and finally, return the data.

Another common use case is authentication.

Add a conditional statement to check if the passed property `authenticated` is `false`. If that's the case, return a prompt to log in.

```jsx
const App = () => {
	const [loading, setLoading] = useState(true);
	const [error, setError] = useState(undefined);

	if (!props.authenticated) {
		return (
			<div>
				<h1>Not authenticated</h1>
				<p>Please log in first</p>
				<button>Log in</button>
			</div>
		);
	}

	if (loading) {
		return <p>Loading your data ...</p>;
	}
	
	if (error) {
		return (
			<div>
				<p>Error loading your data.</p>
				<button>Try again</button>
			</div>
		);
	}
	
	return (
		<div>
			<h1>Your Data</h1>
			<p>The first data point ...</p>
		    <p>We also want to highlight ...</p>
	    </div>
	);
};
```

# Fragments

When working with JSX, we can only ever return one element.

We end up wrapping our elements in one parent element, like a `div,` to return them as JSX.

Instead of returning a `div`, we can use React fragments. Fragments let us group multiple elements without adding extra nodes to the DOM.

A fragment is written by `<>` and `</>`.

```jsx
const App = () => {
	return (
		<>
			<h1>Joke</h1>
			<p>Why did the developer go broke?</p>
			<p>Because they used up all their cache!</p>
		</>
	);
};
```

Fragments are useful when a component needs to return multiple elements, as React components can only return one element by default.

`<>` and `</>` are only the shorthand. We can also use the full `<React.Fragment>` and `</React.Fragment>` syntax.

React fragments are lightweight by design. We can't add attributes like `className` or `style`. However, we can set a `key`.

When we want to set a key, we can't use the shorthand `<>`, but we have to use the `<React.Fragment>` with an explicit `key` prop.

```jsx
const App = () => {
	return (
		<React.Fragment key={key}>
			<h1>Joke</h1>
			<p>Why did the developer go broke?</p>
			<p>Because they used up all their cache!</p>
		</React.Fragment>
	);
};
```

React requires key props on list items to help it efficiently update and reorder elements without causing issues in the DOM.

Notice we use multiple fragments, all wrapped in one outer fragment, with unique keys for efficient updates and a clean DOM.

# Destructing Properties

Properties (props) make components flexible by allowing us to pass in data.

However, typing `props.propName` every time can get repetitive. There's a better way.

Destructuring properties helps make code cleaner and more readable by directly extracting values passed to components.

Destructuring lets us extract properties directly from the function parameters instead of accessing `props.propName`.

```jsx
const Catchphrase = ({character, phrase}) => {
	return (
		<div>
			<h2>{character}:</h2>
			<p>"{phrase}"</p>
		</div>
	);
};
```

Using `{}` in a function parameter allows us to destructure an object, extracting specific properties directly by name.

Inside `{}`, we specify the property names we want to extract, allowing us to access these directly.

Once we have extracted properties, we can use them directly in our component without prefixing them with `props.` each time.

Display first `character` and then `phrase` directly, making the code cleaner and more concise.

Destructuring makes it easy to access specific properties directly, keeping our code cleaner and reducing repetition when using props.

Instead of destructuring in the function’s arguments, we can do it inside the function body.

This is helpful if we want to separate the destructuring step.

```jsx
const {name, price} = props;
```

However, the syntax stays the same whether we use destructing inside the function's argument or outside.

Inside `{}`, we specify the property names we want to extract, allowing us to access these directly.

# Default Properties

Properties are a powerful tool we relly on heavily when working with React.

If some properties aren’t provided and we don’t handle this case, we may get unexpected output, like an empty element.

If a property is not provided, nothing will be rendered.

If we try to print a non-existing property, it will print `undefined`.

Undefined values inside JSX don't render.

We can use conditional rendering to show only the whole element or section if the property is provided.

Use an embedded expression with conditional rendering to avoid rendering a broken UI if `level` is not provided.

```jsx
const Profile = (props) => {
	console.log(porps.level);

	return (
		<div>
			<h2>Player: {props.name}</h2>
			{props.level && <p>Level: {props.level}</p>}
		<div>
	);
};
```

To handle not provided props gracefully, we can set a fallback directly in the JSX using a ternary operator.

Code the inline if-else to render `level` if it was provided. Otherwise, render `"Unranked"` as default value.

```jsx
const Profile = (props) => {
	return (
		<div>
			<h2>Player: {props.name}</h2>
			<p>Level: {prop.level ? props.level : "Unranked"}</p>
		</div>
	);
};
```

When properties aren’t provided, default values ensure components still display correctly, providing a reliable fallback.

Let’s look at a cleaner, more efficient way to set and use default values.

A neat way to set default properties and keep the JS clean is to use object destructuring.

We assign a default value inside `{}` that will be taken if no property will be passed with that name.

```jsx
const Guest = ({name = "Guest"}) => {
	return (
		<div>
			<h2>Welcome, {name}!</h2>
			<p>Hope you have a great experience!</p>
		</div>
	);
};
```

We can set default values for every single property we expect.

Whenever a value is provided, it will be used. If we don't receive one, the default value will be the fallback.

No matter where we desctruct the properties, we can set default values.

```jsx
const Guest = (props) => {
	const { name="Guest", room="Standard"} = props;

	return (
		<div>
			<h2>Welcom, {name}!</h2>
			<p>Booked room: {room}</p>
			<p>We hope you enjoy your stay!</p>
		</div>
	);
};
```

# Complex Properties

Let's explore complex property types. We'll start with arrays.

If the array's values are of type string, we can render them directly. Notice that there is no whitespace between the rendered elements.

However, there are much better ways to render arrays in React. We'll learn about them soon.

Objects can also be passed as properties.

We can pass the object directly instead of saving it in a variable first.

Here, we see two opening and two closing curly braces. It might look odd, but both JSX and objects use curly braces.

```jsx
const App = () => {
	return (
		<div>
		    <img src="https://mimo.app/i/earth.png" />
		    <Greeting
			    name="Adam"
		        location="Eden"
		        age={69}
		        nice={true}
		        friends={["Eve", "Snake"]}
		        description={{ title: "forager", hobby: "napper" }}
			/>
		</div>
	);
};
```

We can't directly render objects, but we can log them.

We can use dot notation to access the values of the `description` object, which is part of the `props` object.

# Arrays in React

In React, arrays enable dynamic list rendering and easy data sharing between components, making UIs more interactive and responsive.

Let's learn how to use them in React.

Similar to passing simple values, we can pass an array as a prop to a component.

Logging the array to the console can help us understand its structure and debug any issues.

React allows us to display arrays directly in our JSX by mapping over them to create elements for each item.

Start by creating an unordered list element to serve as a wrapper for the list items.

We can use the ES6 array method `map` to iterate over all elements inside an embedded expression.

We define the element inside the parameter of the `map` function.

Define `student` as the parameter to allow us to later access the individual element by the variable `student`.

We want to return a `li` element for every element of the `students` that can be rendered by React.

Inside the `li` element, we can use another embedded expression to render the array's element.

```jsx
const House = ({ students }) => {
	console.log(students);

	return (
		<ul>
			{students.map((student) => (
				<li>{student}</li>
		    ))}
		</ul>
	);
};
```

