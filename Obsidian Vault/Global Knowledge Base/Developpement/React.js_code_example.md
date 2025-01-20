# React.js usage

## HTML

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- Import the index.jsx file into the html -->
    <script type="module" src="./index.js"></script>
    <!-- Link the html with the Stylesheets -->
    <link rel="stylesheet" href="./index.css" />
    <!-- Give a title to the web page -->
    <title>My React App</title>
  </head>
  <body>
    <!-- Create a main div to display the website -->
    <div id="root">loading</div>
  </body>
</html>
```

## index.jsx

```jsx
/* Import react in each file to use it */
import React from "react";
/* Import the createRoot function to render the website */
import { createRoot } from "react-dom/client";

/* Import the App component from the App.jsx file */
import App from "./App";

/* Get the html element with the root id to know where to render the components */
const rootElement = document.getElementById("root");
/* Use the createRoot function to connect to the html file */
const root = createRoot(rootElement);
/* Render the component on the html root div */
root.render(<App />);
```

## App.jsx

```jsx
/* Import React in each file to use it and useState to use state variables */
import React, { useState } from "react";

/* Import Welcome as a default exported component and Goodbye from the Messages.jsx file */
import Welcome, { Goodbye } from "./Messages";
/* Import Year as a default exported component and Name and Mood from the Counts.jsx file */
import Year, { Name, Mood } from "./Counts";
/* Import Reveal as a default exported component from the Buttons.jsx file */
import Reveal from "./Buttons";

/* Create a function to display components */
const App = () => {
  /* Create a state variable to display different components if the user is connected or not */
  const [connected, setConnected] = useState(false);

  /* Create a function to change the connected state */
  const handleClickConnect = () => {
    setConnected(true);
  };

  /* Create a userName variable to render user's custom messages */
  const userName = "Ethan";
  /* Create a userAge variable to render user's custom messages */
  const userAge = 20;
  /* Create a userMood variable to render user's custom messages */
  const userMood = true;

  /* Check if the user is not connected to render a goodbye message with a connect button */
  if (!connected) {
    return (
      <div>
        {/* Render the Goodbye component */}
        <Goodbye />
        {/* Create a button to allow the user to connect */}
        <button onClick={handleClickConnect}>Connect</button>
      </div>
    );
  }

  /* Render a page if the user is connected */
  return (
    <div>
      {/* Display the Welcome component */}
      <Welcome />
      {/* Display the Name component with the user's name */}
      <Name name={userName} />
      {/* Display the actual year with the user's age */}
      <Year age={userAge} />
      {/* Display the user's mood */}
      <Mood mood={userMood} />
      {/* Render a button to ask the user to reveal or not a phrase */}
      <Reveal />
    </div>
  );
};

/* Export the App component as a default output */
export default App;
```

## Messages.jsx

```jsx
/* Import react in each file to use it */
import React from "react";

/* Create a Welcome function that returns a JSX component with a paragrah inside */
const Welcome = () => {
  return <p>Welcome dear customer</p>;
};

/* Export a created function that returns a JSX component with a div with paragraphs inside */
export const Goodbye = () => {
  return (
    <div>
      <p>Thank you</p>
      <p>See you next time</p>
    </div>
  );
};

/* Export the Welcome component as a default output */
export default Welcome;
```

## Counts.jsx

```jsx
/* Import react in each file to use it */
import React from "react";

/* Create a function that returns the year based on the user's age */
const Year = (props) => {
  return <p>We are actually in the {props.age + 2005} year</p>;
};

/* Export a created function that returns a JSX component with a welcome message based on the user's name*/
export const Name = (props) => {
  return <p>Welcome dear {props.name}!</p>;
};

/* Export a created function that returns a JSX component based on the user's mood */
export const Mood = (props) => {
  /* Check if the suer's mood is true to render a good mood message */
  if (props.mood) {
    return <p>You are in a good mood : {String(props.mood)}</p>;
  }

  /* Render a bad mood message */
  return <p>Are you sad? Is everything okay?</p>;
};

/* Export the Year component as a default output */
export default Year;
```

## Buttons

```jsx
/* Import React in each file to use it and useState to use state variables */
import React, { useState } from "react";

/* Create a function that render a JSX component with a button and a paragraph to display a secret message */
const Reveal = () => {
  /* Create a state variable to display different components if the user want to reveal or not */
  const [reveal, setReveal] = useState(false);

  /* Create a function to change the reveal state */
  const handleClickReveal = () => {
    setReveal(!reveal);
  };

  /* Render a button and a paragraph based on the user's choice to reveal it or not */
  return (
    <div>
      {/* Set a button to change the reveal state */}
      <button onClick={handleClickReveal}>
        {reveal ? "Read Less" : "Read More"}
      </button>
      {/* Render a message based on the reveal state */}
      {(reveal && <p>This is a secret message that can be hide</p>) || (
        <p>You can't see this secret message</p>
      )}
    </div>
  );
};

/* Export the Reveal component as a default output */
export default Reveal;
```
