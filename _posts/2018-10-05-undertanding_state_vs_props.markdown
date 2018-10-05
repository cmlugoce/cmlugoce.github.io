---
layout: post
title:      "Undertanding State vs Props"
date:       2018-10-05 15:23:10 -0400
permalink:  undertanding_state_vs_props
---

Just like houses need a strong foundation, an app needs a strong foundation to work well. For a while, I thought that I had functional understanding of State vs. Props, until I was working with the React-Redux portfolio  😱😱😱!!

### Props

*Props* (short for properties) are a Component's configuration, its options . Props are used to customize Component when it’s being created and give it different parameters, and they are **immutable**!! Basically, they help the components to talk to each other. One of the most important features of props is that they can be passed down by a parent component to its child components. This allows us to create a component that can be customized with a new set of props every time we use it.

There is also the case that you can have default props so that props are set even if a parent component doesn’t pass them down.


<iframe height='265' scrolling='no' title='Props example' src='//codepen.io/cmlugoce/embed/OBNNMY/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/cmlugoce/pen/OBNNMY/'>Props example</a> by Cristina (<a href='https://codepen.io/cmlugoce'>@cmlugoce</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

In the previous example I used default props, the line ` name: "Cristina" ` creates a property name with value "Cristina". We can access the name property in line 6, by using `{this.props.name}`

Props are passed to the component and are fixed throughout its lifecycle. But there are cases when we want to use data that we know is going to change overtime (e.g. user inputs data directly into the component). In this case we use **state**.

### State

By default, components are *stateless*, meaning that they don't have state(only renders props). On the other hand, a component using state is known as *stateful*.  

Unlike `props`, `state`  strictly belongs to a single Component. It allows React components to dynamically change output over time in response to certain events. When a component needs to keep track of information between renderings, the component itself can create, update, and use` state`.

To understand `state` better, let's work with a simple app. We will build a clicker!


```
class Counter extends React.Component{

 // we use the constructor to set the INITIAL STATE
 
constructor(props) {
        super(props);
        this.state = { count: 0 };
    }  
	
    render() {
        return (
            <button onClick={ this.incrementCount }>
				Clicks: { this.state.count }
			</button>
        );
    }
}


```
We initialize the Component's state with `constructor(props) {
        super(props);
        this.state = { count: 0 };
    }  `

The button (in the render section) displays the current state of the component. The idea behind this, is that we want to see when the state changes. Go ahead and click the button!! *Click!*  Nothing happened! This is because we haven't given instructions to the app on how to update the counter.  To update the state, we need to use `setState()`. With `setState`  the state object updates (asynchronously) and re-renders the component automatically. 

>    When we execute `setState()`, it is non-blocking. It fires off a message to the React component's inner workings saying: "Hey, you need to update state to this value when you have a chance." The component finishes doing its current task before updating the state. In this case, it finishes executing the increment function in full before updating the state.
   
-Learn.co: State

```
class Counter extends React.Component{

 // we use the constructor to set the INITIAL STATE
 
constructor(props) {
        super(props);
        this.state = { count: 0 };
    }
		
	// our incrementCount method makes use of the 'setState' method, which is what we use to alter state
	
    incrementCount = () => {
    const newCount = this.state.count + 1
    this.setState({
      count: newCount
    })
  }
	
    render() {
        return (
            <button onClick={ this.incrementCount }>
				Clicks: { this.state.count }
			</button>
        );
    }
}
```
<iframe height='265' scrolling='no' title='State example: clicker' src='//codepen.io/cmlugoce/embed/QZKLpX/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/cmlugoce/pen/QZKLpX/'>State example: clicker</a> by Cristina (<a href='https://codepen.io/cmlugoce'>@cmlugoce</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

In the example above, when the user clicks the button, it calls the `incrementCount` function. In here, we defined a new constant `const newCount = this.state.count + 1` that will increment the state by 1. Then we finally make use of `setState()` to update our clicker count.


### Summary

*  `state` and `props` common ground:

     -   Both are plain JS objects

     - Both can have default values

     - Both `props` and `state` changes trigger a render update


* Props are used to pass data from parent to child or by the component itself. They are immutable and thus will not be changed.

* State is used for mutable data, or data that will change.

Sources:

[State](https://learn.co/tracks/full-stack-web-development-v6/react-redux/props/state#)

[Components and Props](https://reactjs.org/docs/components-and-props.html)

[State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)
