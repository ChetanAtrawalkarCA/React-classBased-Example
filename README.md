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

### The Wrong Way:-
```jsx
this.setState({ value: this.state.value + 1 });
```
+ This can lead to unexpected behavior in your app if the code above is called multiple times in the same update cycle. To avoid this you can pass an updater callback function to setState instead of an object.

### The Right Way:-
```jsx
this.setState(prevState => ({ value: prevState.value + 1 }));
```

### The Cleaner Way:-
```jsx
this.setState(({ value }) => ({ value: value + 1 }));
```
+ When only a limited number of fields in the state object is required, object destructing can be used for cleaner code.

## React State VS Props Example
When we start working with React components, we frequently hear two terms. They are state and props. So, in this article we will explore what are those and how they differ.

### State:
+ State is something that a component owns. It belongs to that particular component where it is defined. For example, a person’s age is a state of that person.
+ State is mutable. But it can be changed only by that component that owns it. As I only can change my age, not anyone else.
+ You can change a state by using this.setState()

**See the below example to get an idea of state:

### Person.js
```JSX
  import React from 'react';

  class Person extends React.Component{
    constructor(props) {
      super(props);
      this.state = {
        age:0
      this.incrementAge = this.incrementAge.bind(this)
    }

    incrementAge(){
      this.setState({
        age:this.state.age + 1;
      });
    }

    render(){
      return(
        <div>
          <label>My age is: {this.state.age}</label>
          <button onClick={this.incrementAge}>Grow me older !!<button>
        </div>
      );
    }
  }

  export default Person;
  ```
+ In the above example, age is the state of Person component.

## Props:
+ Props are similar to method arguments. They are passed to a component where that component is used.
+ Props is immutable. They are read-only.

**See the below example to get an idea of Props:

### Person.js
```JSX
  import React from 'react';

  class Person extends React.Component{
    render(){
      return(
        <div>
          <label>I am a {this.props.character} person.</label>
        </div>
      );
    }
  }

  export default Person;
const person = <Person character = "good"></Person>
```
+ In the above example, ``const person = <Person character = "good"></Person>`` we are passing ``character = "good"`` prop to ``Person`` component.

+ It gives output as “I am a good person”, in fact I am.

