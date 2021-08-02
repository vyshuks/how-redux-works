# How Redux Works

![alt text](https://programmersought.com/images/74/3faeca10d527956f85c4c82d584fe142.png)

```
// import redux library
const redux = require('redux');
```

## REDUCER
```
Create a Reducer.
Reducer is a normal javascript function that accepts two-parameter.
1. state
2. action

the state is the new state object that needs to be saved on the store.
an action is an object that is used to determine the type of action.

const counterReducer = (state = {counter: 0}, action) => {

    if(action.type === 'increment') {
        return {
            counter: state.counter + 1
        }
    }

    if(action.type === 'decrement') {
        return {
            counter: state.counter - 1
        }
    }

    return state;

}


```

## STORE

```
/*
  Create a store. 
 A store is a place where all the states of an application are stored.
 The store is created by redux's `createStore` function.
*/
const store = redux.createStore(counterReducer);
```

## COMPONENT
```
/*
The states of a store are used by components.
The component subscribes store. When a state change, redux call the subscribed function.
*/
const counterSubscribe = () => {
    const latestState = store.getState();
    console.log(latestState);
}

// subscribe function to store
// this function will be called by redux when a change in the state occurs.
store.subscribe(counterSubscribe);
```


## ACTIONS
```
// Dispatch method is used to dispatch an action, this later triggers the reducer function.
store.dispatch({type: 'increment'});

store.dispatch({type: 'decrement'});
```






