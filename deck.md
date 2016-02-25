# The Art of Reduxion

---

> "The point of philosophy is to start with something so simple as not to seem worth stating, and to end with something so paradoxical that no one will believe it."

##### Bertrand Russell

---

> A system can be understood from studying it’s individual parts

##### Reductionism

---

> The whole system is greater than the sum of its parts

##### Holism

---

#### Current State + Action = New State

Every action advances the state forward

---

# Predictable

---

<image src="http://danielgrant.co/redux-fel-talk/images/pure-calc-4x2.png" />

---

```js
function reducer(state = [], action) {
  if (action.type === 'ADD') {
    return [...state, action.value];
  }
  return state;
}
```

---

That was pure

---

```js
function updateDOMDeDOM() {
  var value = DOM.find('#element').value; // COULD BE ANYTHING!
  var newValue = value * 'dave';
  DOM.find('#anotherElement').value(newValue); // SIDE EFFECT :0
}
```

---

That wasn't pure

---

<image src="http://danielgrant.co/redux-fel-talk/images/jquery-architecture-hand-color.jpg" />

---

<image src="http://danielgrant.co/redux-fel-talk/images/redux-architecture-hand-color.jpg" />

---

<image src="http://danielgrant.co/redux-fel-talk/images/redux-architecture.jpg" />

---

## Thinking in Redux

---

```
Filters         TRACKS
[-- HOUSE --]   [--- CRAVE  YOU ---]
[-- PROGR --]   [--- FIVE HOURS ---]
[-- TRANC --]   [-- TALKING BODY --]
```

---

```js
var FilterList = React.createClass({
  propType: {
    filters: PropTypes.array
  },
  render: function () {
    return (
      this.props.filters.map(filter => (
        <Filter value={filter}
      ))
    );
  }
})
```

---

```js
{
  entities: {
    filters: ['house', 'progressive', 'trance']
    tracks: { 34346: {}, 96986: {} }
  },
  activeFilter: 'house'
  currentTrack: 96986
}
```

---

```js
function reducer(state = {}, action) {
  if (action.type = CHANGE_FILTER) { ... }
  if (action.type = PLAY_TRACK) { ... }
  if (action.type = FETCH_TRACKS) { ... }
  return state;
}
```

---

```js
function filterReducer(state = '', action) {
  if (action.type = CHANGE_FILTER) {
    return action.value
  }
  return state;
}
```

---

```js
var reducers = combineReducers({
  entities: entitiyReducer,
  activeFilter: filterReducer,
  currentTrack: trackReducer
});
```

---

```js
var entities = combineReducers({
  filters,
  tracks
});
```

---

```js
var Filter = React.createClass({
  propType: {
    value: PropTypes.string,
    onClick: PropTypes.func
  },
  render: function () {
    return (
      <div onClick={store.dispatch(changeFilter(value))}>{filter}</div>
    );
  }
})
```

---

## Connecting to React

---

```js
<Provider>

connect()
````

---

```js
ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

---

```js
connect(mapStateToProps, mapDispatchToProps)(Component);
````

---

```js
var mapStateToProps = state => ({
  filters: state.entities.filters
});

connect(mapStateToProps)(FilterList);
```

---

```js

var mapDispatchToProps = dispatch => ({
  onClick: value => dispatch(changeFilter(value))
});

connect(null, mapDispatchToProps)(Filter);
```

---

## Resources

- Redux docs - [http://redux.js.org](http://redux.js.org)
- Redux creator - [https://twitter.com/dan_abramov](https://twitter.com/dan_abramov)
- Eggheads screencasts - [https://egghead.io/series/getting-started-with-redux](https://egghead.io/series/getting-started-with-redux)
- These slides - [https://github.com/djgrant/redux-fel-talk](https://github.com/djgrant/redux-fel-talk)
- Redux examples - [https://github.com/reactjs/redux](https://github.com/reactjs/redux)

---

## Be my friend
#### @danieljohngrant
