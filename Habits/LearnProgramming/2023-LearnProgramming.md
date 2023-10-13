## Learn Programming • 2023 💻

## January - May
- Worked on Redux and Sagas
- Developing Cart and Checkout flow
- Creating reusable and configurable components with atomic design pattern
- Implemented a complete Checkout Re-design with minimal and modern UI

**GitHub Contributions** ✅
![image](https://github.com/abhiramready/Habit-System/assets/40287643/99c23a37-d5ad-4057-bb42-6ee253da26d6)


## June
### Catching up with React 18
- [React 18 New Features](https://www.freecodecamp.org/news/react-18-new-features/) ⭐
- [10 React Hooks Explained](https://www.youtube.com/watch?v=TNhaISOUy6Q) - Video by Fireship ⭐
- [React Testing Library Tutorial](https://www.robinwieruch.de/react-testing-library/) ⭐
- [React useRef() Hook Explained in 3 Steps](https://dmitripavlutin.com/react-useref/)  - Dmitri Pavlutin
- [React's useReducer Hook vs Redux](https://www.robinwieruch.de/redux-vs-usereducer/) - Robin
- [Generator functions in JS](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) - MDN
- [Your Guide to React.useCallback()](https://dmitripavlutin.com/react-usecallback/) - Dmitri Pavlutin
- [JavaScript Callback Functions and How to Use Them](https://www.freecodecamp.org/news/javascript-callback-functions-what-are-callbacks-in-js-and-how-to-use-them/) - FreeCodeCamp

### Ref vs State
- Updating a reference doesn't trigger re-rendering, while updating the state makes the component re-render;
- The reference update is synchronous (the updated reference value is available right away), while the state update is asynchronous (the state variable is updated after re-rendering).
- From a higher point of view, references store infrastructure data of side effects, while the state stores information that is directly rendered on the screen.

### Work Done
- Published blog post, [How to fix ‘agentkeepalive’ npm update error](https://matrixread.com/cannot-find-module-agentkeepalive-npm-update/)
- Deployed first Next.js App, [Next.js Blog](https://nextjs-blog-abhiramready.vercel.app/)


### Learning [Next.js](https://nextjs.org/learn/foundations/about-nextjs)
Next.js has two forms of pre-rendering:  

Static Generation and Server-side Rendering. The difference is in when it generates the HTML for a page.
- SSG Static Generation is the pre-rendering method that generates the HTML at build time. The pre-rendered HTML is then reused on each request.
- SSR Server-side Rendering is the pre-rendering method that generates the HTML on each request.

#### Client-side Rendering in Next.js
- When the page loads, fetch external data from the client using JavaScript and populate the remaining parts.
- This approach works well for user dashboard pages, for example. Because a dashboard is a private, user-specific page, SEO is not relevant, and the page doesn’t need to be pre-rendered. The data is frequently updated, which requires request-time data fetching.

#### Server-side Rendering
```javascript
// context contains request-specific parameters.
export async function getServerSideProps(context) {
  return {
    props: {
      // props for your component
    },
  };
}
```
**Dynamic URLs:** Next.js allows you to statically generate pages with paths that depend on external data, where each page path depends on external data.

 <img src="https://github.com/abhiramready/Habit-System/assets/40287643/4f55fdca-4753-492c-a86a-28a2ddf1682f" width="400"> 

### Redux
- App state management library that acts as a Single source of truth
- Helps us implement top-to-bottom data flow for consistent behavior
- Persistent state across applications with Reducers helps transform the state
- As we cannot change the state directly in Redux and it can only be possible with actions, the state changes are predictable

```JavaScript
/**
 * This is a reducer - a function that takes a current state value and an
 * action object describing "what happened", and returns a new state value.
 * A reducer's function signature is: (intialState, action) => newState
 *
 * The Redux state should contain only plain JS objects, arrays, and primitives.
 * The root state value is usually an object. It's important that you should
 * not mutate the state object, but return a new object if the state changes.
 *
 * You can use any conditional logic you want in a reducer. In this example,
 * we use a switch statement, but it's not required.
 */
function counterReducer(state = { value: 0 }, action) {
  switch (action.type) {
    case 'counter/incremented':
      return { value: state.value + 1 }
    case 'counter/decremented':
      return { value: state.value - 1 }
    default:
      return state
  }
}
```

## Redux-Saga
An intuitive Redux side effect manager.

### Create a Saga

**Generator Functions**

The function* with * defines a generator function, which returns a Generator object. Generators functions can be exited and later re-entered. Their context (variable bindings) will be saved across re-entrances. 

**Yield**

Yield operator is used to pause and resume a generator function. The yield keyword pauses generator function execution and the value of the expression following the yield keyword is returned to the generator's caller.

Both call and put are effect-creator functions.

**Call**

 Call is used to create effect description, which instructs middleware to call the promise. call() is a blocking effect, which means that the saga will wait for the promise resolving before moving on to the next step.

**Put**

Put creates an effect, which instructs middleware to dispatch an action to the store. put(), on the other hand, is a non-blocking effect, which means that the saga can continue to the next step and action will be dispatched within the internal scheduler.

**takeEvery vs takeLatest**
- takeEvery allows multiple action instances to be started concurrently and their completion order can vary.
- takeLatest allows only one action/task to run at any moment, the previous one will be canceled

Creating the Redux Store and applying Middleware

```JavaScript
import { createStore, applyMiddleware } from 'redux'
import createSagaMiddleware from 'redux-saga'

import reducer from './reducers'
import mySaga from './sagas'

// Create the saga middleware
const sagaMiddleware = createSagaMiddleware()
// Mount it on the Store
const store = createStore(
  reducer,
  applyMiddleware(sagaMiddleware)
)

// Then run the saga
sagaMiddleware.run(mySaga)
```
Creating SAGA
```JavaScript
import { call, put, takeEvery, takeLatest } from 'redux-saga/effects'
import Api from '...'

// Worker saga will be fired on USER_FETCH_REQUESTED actions
function* fetchUser(action) {
   try {
      const user = yield call(Api.fetchUser, action.payload.userId);
      yield put({type: "USER_FETCH_SUCCEEDED", user: user});
   } catch (e) {
      yield put({type: "USER_FETCH_FAILED", message: e.message});
   }
}

function* mySaga() {
  yield takeLatest("USER_FETCH_REQUESTED", fetchUser);
}
```

Dispatch an Action
```JavaScript
class UserComponent extends React.Component {
  ...
  onSomeButtonClicked() {
    const { userId, dispatch } = this.props
    dispatch({type: 'USER_FETCH_REQUESTED', payload: {userId}})
  }
  ...
}
```

## July
## TypeScript Revision

- Strongly typed - the variables have fixed types in their life cycle
- Create custom types with interfaces
- [TypeScript Basics - Beginner's Guide](https://www.freecodecamp.org/news/learn-typescript-basics/)
- Interfaces help maintain consistency
- Custom Types, readonly, Array, Union Interfaces, Enum, Tuple, Generics, Type Narrowing
- Learn TypeScript – [Full Tutorial Video](https://www.youtube.com/watch?v=30LWjhZzg50) - FreeCodeCamp, Hitesh Chowdary
- Javascript is dynamically typed i.e. the type of your variable is unknown until it instantiates at run-time which leads to errors. Typescript adds static type support to Javascript which takes care of bugs that are caused by false assumptions of a variable type if you use it right.

## FreeCodeCamp Project
- working on Pomodoro Timer with React
- Timer Codepen - [https://codepen.io/abhiramready/full/oNeVJZW]
- Working on the timer function with useInterval and hooks

## August
- Published blog post - [Count Vowels in a String with JavaScript](https://matrixread.com/count-vowels-in-a-string-with-javascript/)
- Introduction to [Formik](https://www.freecodecamp.org/news/build-react-forms-with-formik-library/) - FreeCodeCamp

## September
- Published blog post - [Consecutive characters count in String with JavaScript](https://matrixread.com/consecutive-characters-count-in-string-with-javascript/)

## October
- Published blog post - [Simple and Pure CSS Spinner](https://matrixread.com/simple-and-pure-css-spinner/)
- useMemo() = cache result of expensive function calls, recompute when dependencies change
- useCallback() = a new function object is created for every re-render which can hog performance, useCallback() prevents unnecessary re-renders of the children as they'll be using the same function object.
- React 18 features: Concurrent Rendering, Automatic Batching, Transitions - startTransition, Suspense on the server
- A “higher-order function” is a function that accepts functions as parameters and/or returns a function.
