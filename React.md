Web Development
Summer 2025
**Slumber**
## What you should know
- HTML
- CSS
- JavaScript
## What is React?
React is a JavaScript library for building dynamic and interactive user interfaces.

HTML → parsed by browser → creates DOM
Source code/text file to the in-memory representation (tree-like structure).
Each HTML element becomes a **node** (object in that tree).
The DOM can be **read and modified** using JavaScript.

```
Document
 └── html
      ├── head
      └── body
           └── p
                └── "Hello, world!"

```

**![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc4IuYSmkWVaC6wPimdQD2LIOQFf1q4O5h72ZZyqHLYe2gc4XfKbXB1Wrjgh_fnZghvicg4z3F94tjWijmJY9oml47l-giMX1mXnvUcXINHiCCo3XZQ7XdP5I1ekTwzk0OXx-HAUw?key=JdQOKBNmsMOfiMwiEtXD2g)**
**![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXe_A9O8LoTM8HjB18T10SwZ4ofqh9R37o15PKyyCGIBqMwmMxsRsutPnwblFog4GLY8egq7ZV9qYHcd5-Eae1jlE7zRjT2QyhHZUxwQupsXwCpqcr60ZF72UKGld2jVH4LvvdfRmg?key=JdQOKBNmsMOfiMwiEtXD2g)**

![img](/media/DOM.png)
## Setting up the Development Environment

For this tutorial you will need [Node.js](https://nodejs.org/en) version 16 or higher.
## Creating a React App

There are two ways to create a React APP:
- Create React APP (CRA)
- Vite
## Create React App
Create React APP using Vite CLI
- reminder to create the React app in a designated folder.
Open the current directory in VS Code if you have not done so.
``` title:"git bash"
code .
```

*To open the terminal: "ctrl + \`"*

Tutorial Vite Version
```
npm create vite@4.1.0
```
Latest Vite Version
```
npm create vite@4.1.0
```

- Y to proceed
- Name the project and package
- Select React and Typescript

Install dependencies
```
npm install
```
or
```
npm i
```

Run the development server
```
npm run dev
```

Open the React app in the browser

```
http://localhost:5173
```

Create a file **Message.tsx**.

```tsx title:"Message.tsx"
// PascalCasing

function Message() {

    // JSX: JavaScript XML

    return <h1>This is my first react element!</h1>;

}

export default Message;
```

Start the App.tsx from scratch.

```tsx title='App.tsx'
import Message from './Message';

function App () {

  // return <div><Message></Message> </div>

  return <div><Message /> </div>
}

export default App;
```

- Delete index.css
- install bootstrap

```
npm install bootstrap@5.2.3
```

- Replace "import '/index.css'" with "import 'bootstrap/dist/css/bootstrap.css'"
- Make App.css blank

Create a 'components' folder in the 'src' folder by convention.

- Create a file named 'ListGroup.tsx' (reminder to follow PascalCase for React components)

```tsx title:"ListGroup.tsx"
function ListGroup() {
    return <h1>List Group</h1>
}

export default ListGroup;
```

Comment out "import Message from './Message';" in App.tsx and replace it with "import ListGroup from './components/ListGroup'"

Rewrite App.tsx
```tsx title:'App.tsx' hl:1,7
import ListGroup from './components/ListGroup'

function App () {

  // return <div><Message></Message> </div>

  return <div><ListGroup /> </div>
}

export default App;
```

Go to the [BootStrap Website](https://getbootstrap.com/docs/5.3/components/list-group/) and replace the group list text with the html example.

```tsx title:"ListGroup.tsx"
function ListGroup() {
    return <ul class="list-group">
  <li class="list-group-item">An item</li>
  <li class="list-group-item">A second item</li>
  <li class="list-group-item">A third item</li>
  <li class="list-group-item">A fourth item</li>
  <li class="list-group-item">And a fifth one</li>
</ul>
}

export default ListGroup;
```

(move) Notice that the file does not auto format on save.
Do "shift + ctrl + p" and search format document. Confirm and select Prettier.
**Reminder** to review the extension that auto formats code upon save and settings.

```tsx title:"ListGroup.tsx"
function ListGroup() {
  return (
    <ul className="list-group">
      <li className="list-group-item">An item</li>
      <li className="list-group-item">A second item</li>
      <li className="list-group-item">A third item</li>
      <li className="list-group-item">A fourth item</li>
      <li className="list-group-item">And a fifth one</li>
    </ul>
  );
}

export default ListGroup;
```

A **function** can only return *one* element, so in order to return multiple elements i.e. h1 and ul from html.

Here are **two** ways to solve this:
- Wrap the expression in a div.
- Fragment

## Wrapping the expression in a Div
Highlight the given elements.
Open the command palette (view -> command palette) and search for "Emmet: Wrap with Abbreviation."

Enter Abbreviation: "div"

This is inefficient, it is more efficient to use a fragment.

```tsx title:"ListGroup.tsx"
function ListGroup() {
  return (
    <div>
      <h1>My Favorite Novels</h1>
      <ul className="list-group">
        <li className="list-group-item">Shadow Slave</li>
        <li className="list-group-item">Lord of the Mysteries</li>
        <li className="list-group-item">Reverend Insanity</li>
        <li className="list-group-item">A fourth item</li>
        <li className="list-group-item">And a fifth one</li>
      </ul>
    </div>
  );
}

export default ListGroup;
```

## Using a fragment

Append this to the top of ListGroup.tsx
```tsx
import { Fragment } from "react";
```

```tsx title="ListGroup.tsx"
import { Fragment } from "react";

function ListGroup() {
  return (
    <Fragment>
      <h1>My Favorite Novels</h1>
      <ul className="list-group">
        <li className="list-group-item">Shadow Slave</li>
        <li className="list-group-item">Lord of the Mysteries</li>
        <li className="list-group-item">Reverend Insanity</li>
        <li className="list-group-item">A fourth item</li>
        <li className="list-group-item">And a fifth one</li>
      </ul>
    </Fragment>
  );
}

export default ListGroup;
```

## Simpler way (Fragment)

Remove the import and remove fragment from the <> and </> and it will do the same thing
```tsx title="ListGroup.tsx"
function ListGroup() {
  return (
    <>
      <h1>My Favorite Novels</h1>
      <ul className="list-group">
        <li className="list-group-item">Shadow Slave</li>
        <li className="list-group-item">Lord of the Mysteries</li>
        <li className="list-group-item">Reverend Insanity</li>
        <li className="list-group-item">A fourth item</li>
        <li className="list-group-item">And a fifth one</li>
      </ul>
    </>
  );
}

export default ListGroup;
```


## Rendering Dynamic Lists
Since the lists is useless since the items are hard coded, we can create a list of items such that it is easily interchangeable.

We can use a list such as :

```tsx
    const items = [
        'Shadow Slave',
        'Lord of the Mysteries',
        'Reverend Insanity',
        'A fourth item',
        'And a fifth one'
    ];
```

and replace the li elements with this:

```tsx
items.map(item => <li>{item}</li>)
```

This expression cannot be done in jsx markup, only html and other react components. In order to 
use this to render the data dynamically, it needs to be wrapped in braces.

```tsx
{items.map(item => <li>{item}</li>)}
```

**Before Prettier**

```tsx title:"ListGroup.tsx"
// import { Fragment } from "react";

function ListGroup() {

    const items = [
        'Shadow Slave',
        'Lord of the Mysteries',
        'Reverend Insanity',
        'A fourth item',
        'And a fifth one'
    ];
  
    return (
        <>
      <h1>My Favorite Novels</h1>
      <ul className="list-group">

        {items.map(item => <li>{item}</li>)}
      </ul>
    </>
  );
}

export default ListGroup;
```

**After Prettier**

```tsx title:"ListGroup.tsx" hl:15
function ListGroup() {
  const items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];
  
  return (
    <>
      <h1>My Favorite Novels</h1>
      <ul className="list-group">
        {items.map((item) => (
          <li>{item}</li>
        ))}
      </ul>
    </>
  );
}

export default ListGroup;
```

There is an error, each item needs a unique key using the map method.

```tsx title:"ListGroup.tsx" hl:15
function ListGroup() {
  const items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];
  
  return (
    <>
      <h1>My Favorite Novels</h1>
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}

export default ListGroup;
```

## If Statement (optional)
Suppose you want to display a separate message if there are zero items in the list.

```tsx title:"ListGroup.tsx" hl:2,9,11-17
function ListGroup() {
  let items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];
  items = [];
  
  if (items.length === 0)
    return (
      <>
        <h1>My List</h1>
        <p>No items found!</p>
      </>
    );

  return (
    <>
      <h1>My Favorite Novels</h1>
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}

export default ListGroup;
```
The **issue** with this code is that it has **duplication**.

## Conditional Rendering

```tsx title:'ListGroup.tsx' hl:14,10
function ListGroup() {
  let items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];
  items = [];
  
  return (
    <>
      <h1>My Favorite Novels</h1>
      {items.length === 0 ? <p>No items found</p> : null}
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}

export default ListGroup;
```

If the given conditional expression is too complicated, it can be replaced with a substitute.
```tsx title:"example"
const message = items.length === 0? <p>No item found</p>: null
```

```tsx title:"example"
{message}
```

```tsx title:"ListGroup.tsx" hl:11,16
function ListGroup() {
  let items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];
  items = [];
  
  const message = items.length === 0 ? <p>No item found</p> : null;

  return (
    <>
      <h1>My Favorite Novels</h1>
      {message}
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}
 
export default ListGroup;
```

In the instance that you want a more **nuanced** response, you can replace the constant variable with a **function**.

```tsx title:"example"
  const getMessage = () => {

    return items.length === 0 ? <p>No item found</p> : null;

  };

// ....

{getMessage()}
```

## Clever trick to render dynamically

When the first condition is true, it will return the string.
```tsx
{true && 'placeHolder'} // returns 'placeHolder'
```

When the first condition is false, it will return false.
```tsx
{false && 'placeHolder'} // returns 'false'
```

**Final Conditional File**

```tsx title:"ListGroup.tsx"
function ListGroup() {
  let items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];
  //   items = [];
  
  return (
    <>
      <h1>My Favorite Novels</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}

export default ListGroup;
```

## Handling Events

```tsx title="ListGroup.tsx" hl:21,17
function ListGroup() {
  let items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];

  //   items = [];
  
  return (
    <>
      <h1>My Favorite Novels</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className="list-group-item"
            key={item}
            onClick={(event) => console.log(item, index)}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}

export default ListGroup;
```

**Note**: you can replace "item, index" on line 21 with event to see the type of event that occurs when you click each item.
![img](/media/onClickEvent.png)

Suppose you you want to do a more complicated event/function definition outside the return statement. You can do something like this.

```tsx title:"ListGroup.tsx"
import { MouseEvent } from "react";

function ListGroup() {
  let items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];

  // Event Handler
  const handleClick = (event: MouseEvent) => console.log(event); // type annotation in typescript
  
  return (
    <>
      <h1>My Favorite Novels</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li className="list-group-item" key={item} onClick={handleClick}>
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}

export default ListGroup;
```

**Cool Trick**
If you autocomplete a function from a library that is installed, but is not imported to the file, it will auto import for you.

**useState** in React is considered a hook that allows you to add a local state(data) to functional components. In this case:

```tsx title='example'
const [selectedIndex, setSelectedIndex] = useState(-1);
```

The hook can be de-structured to an array two elements, SelectedIndex (variable) and set SelectedIndex (updater function). When the function is called, it alters the state (variable). When the variable is altered, react is notified and re-render the component, which updates DOM. Which means with react, you almost never have to touch the DOM directly.

### Using useState

```tsx title="ListGroup.tsx" hl:14,24-30
import { useState } from "react";
  
function ListGroup() {
  let items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];
  
  // Hook, a funciton that allows us to tap into React's features like state
  // useState is a hook that allows us to manage state in functional components
  const [selectedIndex, setSelectedIndex] = useState(-1);
  
  return (
    <>
      <h1>My Favorite Novels</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className={
              selectedIndex === index
                ? "list-group-item active"
                : "list-group-item"
            }
            key={item}
            onClick={() => {
              setSelectedIndex(index);
            }}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}

export default ListGroup;
```

**Note** that each iteration of this component will have its own state such that if there is another instance of ListGroup.tsx in App.tsx, the two variables are local to each other and do not influence external duplicate components.

## Passing Data Via Props

In the interest of using reusable code, it would be nice to pass different labels like cities, names, colors, and so on.

First you must determine the shape of the input to this component i.e.
```tsx title:'example'
// { items: [], heading: string }
```

To do this we can use the typescript feature: interface.

Moved the definitions of the list to App.tsx and copied/passed the values for the items and heading.

```tsx title:'App.tsx'
import ListGroup from "./components/ListGroup";
  
function App() {
  let items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];
  // return <div><Message></Message> </div>
  return (
    <div>
      <ListGroup items={items} heading="Light Novels" />{" "}
    </div>
  );
}

export default App;
```

Created an interface that declared the type of the variable.
"Props are arguments passed into React components."
Destructured  prop into { items, heading} so items.map would not have to be prefaced with prop such that it is labeled prop.items.map...

```tsx title='ListGroup.tsx'
import { useState } from "react";
interface Props {
  items: string[];
  heading: string;
}
  
function ListGroup({ items, heading }: Props) {
  // Hook, a funciton that allows us to tap into React's features like state
  // useState is a hook that allows us to manage state in functional components
  const [selectedIndex, setSelectedIndex] = useState(-1);
  
  return (
    <>
      <h1>{heading}</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className={
              selectedIndex === index
                ? "list-group-item active"
                : "list-group-item"
            }
            key={item}
            onClick={() => {
              setSelectedIndex(index);
            }}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}

export default ListGroup;
```

## Passing Functions Via Props

What if after highlighting the items in the list, we want an event to occur afterwards such as redirecting or filtering items. We need a mechanism to notify the consumer or the parent of this component that an item has been selected such as app, where it is called by App.tsx.

Similar to hooks, we can add a third property, a function to the interface that is already defined.

Defined a handler and passed the function to the third property.
```tsx title="App.tsx"
import ListGroup from "./components/ListGroup";

function App() {
  let items = [
    "Shadow Slave",
    "Lord of the Mysteries",
    "Reverend Insanity",
    "A fourth item",
    "And a fifth one",
  ];
  
  const handleSelectItem = (item: string) => {
    console.log(item);
  };
  return (
    <div>
      <ListGroup
        items={items}
        heading="Light Novels"
        onSelectItem={handleSelectItem}
      />{" "}
    </div>
  );
}
  
export default App;
```

Defined the third property in the interface and added it to parameters + run the function when an item is selected on screen. The function runs the function which logs it for App.tsx to be notified.
```tsx title="ListGroup.tsx"
import { useState } from "react";
interface Props {
  items: string[];
  heading: string;
  onSelectItem: (item: string) => void;
}
  
function ListGroup({ items, heading, onSelectItem }: Props) {
  // Hook, a funciton that allows us to tap into React's features like state
  // useState is a hook that allows us to manage state in functional components
  const [selectedIndex, setSelectedIndex] = useState(-1);
  
  return (
    <>
      <h1>{heading}</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className={
              selectedIndex === index
                ? "list-group-item active"
                : "list-group-item"
            }
            key={item}
            onClick={() => {
              setSelectedIndex(index);
              onSelectItem(item);
            }}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}
  
export default ListGroup;
```

## Props versus State
**Props** are the input passed to a component as seen in the *items* and *heading*. Similar to function arguments. Should be treated as immutable.

In the case of the previous files,  *heading* should not be changed in the ListGroup.tsx.

**State** is the data managed by a component as seen in the *index* which changed dynamically as different items were selected from the list. Similar to local variables. Should be treated as mutable.

In the case of the previous files, the *index* or rather the *selectedIndex* should change dynamically in ListGroup.tsx as the user selects different items from the list.

The difference lies between when/where/how the change occurs. The one similarity is that react will re-render our component and thus the DOM when there are any changes in value.
## Passing Children

## Using an extension to create a frame of a 
```
rafce
```
'rafce' is short for react arrow function component export using the extension [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
In the case of the file *alert.tsx*, when this command is ran, it is replaced with a snipper.
```tsx title='alert.tsx'
import React from 'react'

const Alert = () => {
  return (
    <div>Alert</div>
  )
}

export default Alert
```

Go to the [BootStrap Website](https://getbootstrap.com/docs/5.3/components/alerts/) and under Docs -> Components -> Alerts

To style a text with an alert, it will need an alert + alert variant class to determine the visual change.

Assuming that the App.tsx is loading an alert component, if we experiment:

```tsx title='Alert.tsx'
const Alert = () => {
  return <div className="alert alert-success">Alert</div>;
};
  
export default Alert;
```

![img](/media/greenAlert.png)

If the second class is changed to any other variant, the color scheme will change accordingly.

Here is another example:
![img](/media/redAlert.png)

**Using props to pass strings to the alert class**

```tsx title='Alert.tsx'
interface Props {
  text: string;
}
  
const Alert = ({ text }: Props) => {
  return <div className="alert alert-success">{text}</div>;
};
  
export default Alert;
```

```tsx title='App.tsx'
import Alert from "./components/Alert";
  
function App() {
  return (
    <div>
      <Alert text="Warning: This is a success alert!" />
    </div>
  );
}
  
export default App;
```

Would it not be nice to have it function similar to html like this:

```tsx title='example'
<Alert>
	Hello World!
</Alert>
```

There is a special reserved **prop** that all **React components** can use: the **children** prop, In Alert.tsx, replacing very instance of 'text' with 'children' allows 'App' to pass and render the string (or other valid React elements/components) nested between the Alert component opening and closing tags.

```tsx title='Alert.tsx'
interface Props {
  children: string;
}
  
const Alert = ({ children }: Props) => {
  return <div className="alert alert-success">{children}</div>;
};
  
export default Alert;
```

```tsx title='App.tsx'
import Alert from "./components/Alert";
  
function App() {
  return (
    <div>
      <Alert>Warning: This is a success alert!</Alert>
    </div>
  );
}
  
export default App;
```

HTML content will not pass here. In order to use HTML content, the children prop will need to be of type **ReactNode**.

```tsx title='App.tsx excerpt'
      <Alert>
        Warning: <span style={{ color: "red" }}>This is a success alert!</span>
      </Alert>'
```

![img](htmlAlert.png)

## Inspecting Components with React Dev Tools
A useful browser extension [React Developer Tools](https://chromewebstore.google.com/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) makes it easier to view the DOM and see the hierarchy of each component.

## Exercise: Building a Button Component

[BootStrap](https://getbootstrap.com/docs/5.3/components/buttons/) buttons -> Self Guided Exercise

It has two classes the base class btn and the class that identifies the color.

```tsx title='App.tsx'
import Alert from "./components/Alert";
import Button from "./components/Button";
  
function App() {
  return (
    <div>
      <Alert>
        Warning: <span style={{ color: "red" }}>This is a success alert!</span>
      </Alert>
  
      {/* if you put the wrong color, it will not look as intended */}
      <Button color="warning" onClick={() => console.log("clicked")}>
        Click Me
      </Button>
    </div>
  );
}
  
export default App;
```

```tsx title='Button.tsx'
import React from "react";
  
interface Props {
  children: string;
  color?: //explicitly defining the type of color prop gives a
  // complotion error if the color is not one of the specified values.
  | "primary"
    | "secondary"
    | "success"
    | "danger"
    | "warning"
    | "info"
    | "light"
    | "dark"; // ? makes it optional when filling out component props.
  onClick: () => void;
}
  
const Button = ({ children, onClick, color = "primary" }: Props) => {
  return (
    <button className={"btn btn-" + color} onClick={onClick}>
      {children}
    </button>
  );
};
  
export default Button;
```

## Exercise: Showing an alert

```tsx title='App.tsx'
import { useState } from "react";
import Alert from "./components/Alert";
import Button from "./components/Button";
  
function App() {
  const [alertVisible, setAlertVisibility] = useState(false);
  
  return (
    <div>
      {alertVisible && (
        <Alert onClose={() => setAlertVisibility(false)}>
          Warning:{" "}
          <span style={{ color: "red" }}>This is a success alert!</span>
        </Alert>
      )}
  
      {/* if you put the wrong color, it will not look as intended */}
      <Button color="warning" onClick={() => setAlertVisibility(true)}>
        Click Me
      </Button>
    </div>
  );
}
  
export default App;
```

```tsx title='Button.tsx'
import React from "react";
  
interface Props {
  children: string;
  color?: //explicitly defining the type of color prop gives a
  // complotion error if the color is not one of the specified values.
  | "primary"
    | "secondary"
    | "success"
    | "danger"
    | "warning"
    | "info"
    | "light"
    | "dark"; // ? makes it optional when filling out component props.
  onClick: () => void;
}
  
const Button = ({ children, onClick, color = "primary" }: Props) => {
  return (
    <button className={"btn btn-" + color} onClick={onClick}>
      {children}
    </button>
  );
};
  
export default Button;
```

```tsx title='Alert.tsx'
import { ReactNode } from "react";
  
interface Props {
  children: ReactNode;
  onClose: () => void;
  // The children prop allows us to pass any React elements as children to the Alert component.
}
  
const Alert = ({ children, onClose }: Props) => {
  return (
    <div className="alert alert-success alert-dismissible">
      {children}
      <button
        type="button"
        className="btn-close"
        onClick={onClose}
        data-bs-dismiss="alert"
        aria-label="Close"
      ></button>
    </div>
  );
};
  
export default Alert;
```

![img](/media/dynamicAlert.png)

## Side Notes:

note if you want to see how jsx is converted to js, you can view it at [babeljs](babeljs.io/repl).
![img](/media/babel.png)

**nodes_modules**: library files.

**public**: media files like images.

**src**: source code of the application. 

Extensions of TypeScript files should be .tsx (React components) or .ts (plain TypeScript files).

Function components are more popular. When creating function components, always follow PascalCasing

![img](/media/hmr.png)

**HMR**:  Hot Modular Replacement

**BootStrap** is a popular css library

