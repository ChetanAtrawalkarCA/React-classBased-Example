# 🔯 React-classBased-Example
## Stateful
## Class Type Components
```js
class Cat extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      humor: 'happy'
    }
  }
  render() {
    return(
      <div>
        <h1>{this.props.name}</h1>
        <p>
          {this.props.color}
        </p>
      </div>
    );
  }
}
```
## React State Example
+ State is the place where the data comes from.

+ We should always try to make our state as simple as possible and minimize the number of stateful components. If we have, for example, ten components that need data  from the state, we should create one container component that will keep the state for all of them.

+ State is basically like a global object that is available everywhere in a component.

### Example of a Stateful Class Component:
```jsx
import React from 'react';

class App extends React.Component {
  constructor(props) {
    super(props);
      
    // We declare the state as shown below
    
    this.state = {                           
      x: "This is x from state",    
      y: "This is y from state"
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.x}</h1>
        <h2>{this.state.y}</h2>
      </div>
    );
  }
}
export default App;
```
### Another Example:-
```jsx
import React from 'react';

class App extends React.Component {
  constructor(props) {
    super(props);
    
    // We declare the state as shown below
    this.state = {                           
      x: "This is x from state",    
      y: "This is y from state"
    }
  }

  render() {
    let x1 = this.state.x;
    let y1 = this.state.y;

    return (
      <div>
        <h1>{x1}</h1>
        <h2>{y1}</h2>
      </div>
    );
  }
}
export default App;
```
## Updating State
+ You can change the data stored in the state of your application using the setState method on your component.
```js
this.setState({ value: 1 });
```
+ Keep in mind that setState is asynchronous so you should be careful when using the current state to set a new state. A good example of this would be if you want to increment a value in your state.

###The Wrong Way
```jsx
this.setState({ value: this.state.value + 1 });
```
+ This can lead to unexpected behavior in your app if the code above is called multiple times in the same update cycle. To avoid this you can pass an updater callback function to setState instead of an object.

###The Right Way
```jsx
this.setState(prevState => ({ value: prevState.value + 1 }));
```
