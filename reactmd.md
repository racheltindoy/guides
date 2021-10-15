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
