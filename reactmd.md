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
