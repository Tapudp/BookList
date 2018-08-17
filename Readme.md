# Book Library App
### Reducers
   - `redux` has this fanct words like reducers so gonna create a reducer file with function which returns an array of books

### Containers Connecting Redux to react
   - it is already generating a state for the component
   - created `book-list.js` component without any connection to state yet.
   - `containers` which are similar to components but just has the dumb component in which redux states can be added
   
### Container implementation
   - adding the `booklist` component in main app file 
   - adding `react-redux` library in the `book-list` because it is going to be the container for our applications
   - `connect` takes a function and a component and produces a Container
   - Provider will give you the store where we can call our reducers
   - and in the `book-list` which is a dumb component till now will have a function `mapStateToProps` which directly looks into the store for the `books` or any state props are defined there.

### Action and Action Creators
   - user clicks and creates an actions action
   - action creator returns an action
   - action automatically sent to all reducers
   - `activeBook` property on state set to the value returned from the `activeBook` reducer
   - All reducers processed the action and returns the new state.
      New State has been assembled.
      Notify containers of the changes to state
      - On notification containers will render with new props


### Binding Action creator
   - create a action function `selectbook` 
   - attatching `selectBook` action creator with the book-list container
   - `bindActionCreators` function from the redux library 
   - `mapDispatchToProps` uses `bindActionCreators` with `dispatch` function object as second argument and it is going to take all the actions and going to pass on to all the different reducers inside the application

### Creating an action
   - `onClick` event and the action just logs in for now
   - so now action creator should return an action
   - now changing the action creator which has two keywords `type` which can be a variable and a `payload` the book itself

### Consuming Actions in reducer
   - created a new reducer `activeBook reducer` 
   - 2 arguments to reducers `currentState` and `action`
      - state argument is not application state only the state a particular reducer is responsible for
      - redux doesn't take in `undefined` state so we will use ES6 syntax and say `state = null` the functional argument itself so that it says `if the state is undefined then set it to null`
      - never mutate the current to present the new state, always return a fresh object
      - and `active_reducer` need to be in the combined reducer state in that `index.js` 
   - any key that provide our `combineReducer` ends up as a key to our global state

   - only bookList component cares about the book reducers so only the book-detail will care about the active book is so created a new container `book-detail.js`
   - and connected the `mapStateToProps` with that function as well