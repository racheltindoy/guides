# Creating a react app

  terminal
  
	```
	npx create-react-app my-app
	cd my-app
	npm start
	```
  
  
## react.new (website)
  
## Creating a component
  src > index.js
  
   ```
  import React from 'react';
  import ReactDOM from 'react-dom';
  import './index.css';

  ReactDOM.render(
  React.createElement(
  "h1", 
  {style: {color: "blue"}}, 
  "Heyyyy Everyone!"),
  document.getElementById('root')
  );
  ```
  
  
## JSX is javascript as XML. allows you to write tags directly in javascript

## start of code

> App.js

```
function Header() {
  return (
    <header>
      <h1>Coffee House</h1>
    </header>
  );
}


function App() {
  return (
    <div className="App">
      <Header />
      <Main />
      <Footer />
    </div>
  );
}
```


## Adding Component Properties

```
function Header(props) {
  console.log(props)
  return (
    <header>
      <h1>{props.name}'s Coffee House</h1>
    </header>
  );
}

function Main(props) {
  return (
    <section>
      <p>We serve {props.adjective} coffee.</p>
      <img src={banner} height={200} alt="newly brewed black coffee"/>
      <ul>
        {props.coffees.map((coffee) => (
          <li>{coffee}</li>
        ))}
      </ul>
    </section>
  );
}


function Footer(props) {
  return(
    <footer>
      <p>Copyright {props.year}</p>
    </footer>
  );
}


const coffees = [
  "Latte",
  "Espreso",
  "Iced"
]

function App() {
  return (
    <div className="App">
      <Header name="Binnie" />
      <Main adjective="amazing" coffees={coffees} />
      <Footer year={new Date().getFullYear()} />
    </div>
  );
}

export default App;
```

## display images and importing

> App.js

```
import banner from "./slider/1.jpg"

<img src={banner} height={200} alt="newly brewed black coffee"/>
```


## Add another component

> index.js

```
function AppTwo() {
  return(
    <h2>App Two</h2>
  );
}

ReactDOM.render(
 <React.Fragment>
  <App />
  <AppTwo />
 </React.Fragment>,
  document.getElementById('root')
);
```

### notes
use ```<React.Fragment>``` instead of ```<div>```
style: font-style should be fontStyle
className instead of class


## Conditional Rendering

> index.js

```
ReactDOM.render(
 <>
 <App authorized={true}/>
 </>,
  document.getElementById('root')
);
```

> App.js

```
function SecretComponent() {
  return(
    <h2>Authorized users only.</h2>
  );
}


function RegularComponent() {
  return(
    <h2>Everyone can see this.</h2>
  );
}


function App(props) {
  if(props.authorized) {
    return <SecretComponent />;
  } else {
    return <RegularComponent />;
  }
  
}
```

### Shortcut

function App(props) {
  return (
    <>
    {props.authorized ? <SecretComponent /> : <RegularComponent />}
    </>
  );
  
}


## Destructuring arrays and objects

```
function App({authorized}) {
  return (
    <>
    {authorized ? <SecretComponent /> : <RegularComponent />}
    </>
  );
  
}
```


```
const [, , light] = [
  "boots",
  "tent", 
  "headlamp"];
console.log(light);
```


## Understanding the useState hook

> index.js

```
import React, { useState } from 'react';
import './App.css';

function App() {
  const [emotion, setEmotion] = useState("happy");
  console.log(emotion);
  return (
    <>
     <h1>Current emotion is {emotion}.</h1>
     <button onClick={() => setEmotion("frustrated")}>Frustrated</button>
     <button onClick={() => setEmotion("enthusiastic")}>Enthusiastic</button>
    </>
  );
  
}

export default App;
```


## Working with useEffect
> App.js

```
import React, { useState , useEffect} from 'react';
import './App.css';

function App() {
  const [emotion, setEmotion] = useState("happy");
  const [secondary, setSecondary] = useState("tired");

  useEffect(() => {
    console.log("It's " + emotion + " around here!");
  }, [emotion]);

  useEffect(() => {
    console.log("It's " + secondary + " around here!");
  });

  return (
    <>
     <h1>Current emotion is {emotion} and {secondary}.</h1>
     <button onClick={() => setEmotion("frustrated")}>Frustrated</button>
     <button onClick={() => setEmotion("enthusiastic")}>Enthusiastic</button>
     <button onClick={() => setEmotion("mad")}>Mad</button>
      <br></br>
     <button onClick={() => setSecondary("Marvin Gaye")}>Marvin Gaye</button>
     <button onClick={() => setSecondary("Joyful")}>Joyful</button>
    </>
  );
  
}

export default App;
```

## Incorporating useReducer

> App.js

```
import React, { useState , useEffect, useReducer} from 'react';
import './App.css';


function App() {
  const [checked, toggle] = useReducer(
    (checked) => !checked,
    false
  );

  return (
    <>
     <input type="checkbox" value={checked} onChange={toggle} />
     <p>{checked ? "checked" : "not checked"}</p>
    </>
  );
  
}

export default App;
```
