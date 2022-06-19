# Redux principles
###### Redux is a library for managing global application state
  - Redux is typically used with the React-Redux library for integrating Redux and React together
  - Redux Toolkit is the recommended way to write Redux logic
###### Redux uses a "one-way data flow" app structure
  - State describes the condition of the app at a point in time, and UI renders based on that state
  - When something happens in the app:
    - The UI dispatches an action
    - The store runs the reducers, and the state is updated based on what occurred
    - The store notifies the UI that the state has changed
  - The UI re-renders based on the new state
###### Redux uses several types of code
  - Actions are plain objects with a `type` field, and describe "what happened" in the app
  - Reducers are functions that calculate a new state value based on previous state + an action
  - A Redux store runs the root reducer whenever an action is dispatched

###### We can create a Redux store using the Redux Toolkit configureStore API
  - `configureStore` accepts a `reducer` function as a named argument
  - `configureStore` automatically sets up the store with good default settings
###### Redux logic is typically organized into files called "slices"
  - A "slice" contains the reducer logic and actions related to a specific feature / section of the Redux state
  - Redux Toolkit's `createSlice` API generates action creators and action types for each individual reducer function you provide
###### Redux reducers must follow specific rules
  - Should only calculate a new state value based on the `state` and `action` arguments
  - Must make immutable updates by copying the existing state
  - Cannot contain any asynchronous logic or other "side effects"
  - Redux Toolkit's `createSlice` API uses Immer to allow "mutating" immutable updates
###### Async logic is typically written in special functions called "thunks"
  - Thunks receive `dispatch` and `getState` as arguments
  - Redux Toolkit enables the `redux-thunk` middleware by default
###### React-Redux allows React components to interact with a Redux store
  - Wrapping the app with `<Provider store={store}>` enables all components to use the store
  - Global state should go in the Redux store, local state should stay in React components