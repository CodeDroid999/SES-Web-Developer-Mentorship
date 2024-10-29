# Module 2: Advanced Front-end
## Week 3: Day 3 - State Management in React with Context API and Redux

### Outline
1. **Review of Day 2: React Router**
2. **Understanding State Management**
3. **Using Context API for State Management**
4. **Introduction to Redux**
5. **Setting Up Redux**
6. **Redux Concepts: Actions, Reducers, and Store**
7. **Connecting React with Redux**
8. **Q&A and Wrap-up**

### Course Content

#### 1. Review of Day 2: React Router
- **Recap of Key Concepts:**
  - Participants will share their experiences using React Router, including challenges and how they implemented nested and dynamic routing.

#### 2. Understanding State Management
- **What is State Management?**
  - State management is the way we handle the state of an application. It allows us to manage data across components and ensure a seamless user experience.

- **Why is State Management Important?**
  - Effective state management helps in maintaining consistency across UI components, improves performance, and facilitates data sharing among components.

#### 3. Using Context API for State Management
- **What is Context API?**
  - Context API is a built-in feature in React that allows for state management without the need for additional libraries. It provides a way to pass data through the component tree without having to pass props down manually at every level.

- **Setting Up Context API:**
  ```javascript
  import React, { createContext, useState } from 'react';

  const MyContext = createContext();

  const MyProvider = ({ children }) => {
    const [state, setState] = useState(initialState);
    
    return (
      <MyContext.Provider value={{ state, setState }}>
        {children}
      </MyContext.Provider>
    );
  };

  export { MyContext, MyProvider };
  ```

- **Using Context in Components:**
  ```javascript
  import React, { useContext } from 'react';
  import { MyContext } from './MyProvider';

  const MyComponent = () => {
    const { state, setState } = useContext(MyContext);
    // Use state and setState here
  };
  ```

#### 4. Introduction to Redux
- **What is Redux?**
  - Redux is a predictable state container for JavaScript apps, commonly used with React to manage application state.

- **Why Use Redux?**
  - Redux provides a centralized store, enabling a predictable state flow, making it easier to manage state across large applications.

#### 5. Setting Up Redux
- **Installation:**
  ```bash
  npm install redux react-redux
  ```

- **Creating a Redux Store:**
  ```javascript
  import { createStore } from 'redux';

  const store = createStore(reducer);
  ```

- **Providing the Store:**
  ```javascript
  import { Provider } from 'react-redux';

  function App() {
    return (
      <Provider store={store}>
        {/* Your app components go here */}
      </Provider>
    );
  }
  ```

#### 6. Redux Concepts: Actions, Reducers, and Store
- **Actions:**
  - Actions are plain JavaScript objects that describe what happened in the application.
  ```javascript
  const increment = () => ({ type: 'INCREMENT' });
  ```

- **Reducers:**
  - Reducers specify how the application state changes in response to actions.
  ```javascript
  const initialState = { count: 0 };

  const counterReducer = (state = initialState, action) => {
    switch (action.type) {
      case 'INCREMENT':
        return { ...state, count: state.count + 1 };
      default:
        return state;
    }
  };
  ```

- **Store:**
  - The store holds the complete state tree of the application.
  ```javascript
  import { createStore } from 'redux';

  const store = createStore(counterReducer);
  ```

#### 7. Connecting React with Redux
- **Using `connect` to Access State:**
  ```javascript
  import { connect } from 'react-redux';

  const mapStateToProps = (state) => ({
    count: state.count,
  });

  const MyComponent = ({ count }) => {
    return <div>{count}</div>;
  };

  export default connect(mapStateToProps)(MyComponent);
  ```

- **Dispatching Actions:**
  ```javascript
  const mapDispatchToProps = (dispatch) => ({
    increment: () => dispatch(increment()),
  });

  const MyComponent = ({ increment }) => {
    return <button onClick={increment}>Increment</button>;
  };

  export default connect(null, mapDispatchToProps)(MyComponent);
  ```

#### 8. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions about Context API and Redux and share any challenges they have faced.

- **Recap of Key Takeaways:**
  - Summarize the importance of state management in React applications, highlighting when to use Context API vs. Redux.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with Git for version control.

### Additional Resources
- **React Context API Documentation:**
  - [React Context API](https://reactjs.org/docs/context.html)

- **Redux Documentation:**
  - [Redux Docs](https://redux.js.org/introduction/getting-started)

- **Video Tutorial on Redux:**
  - [Redux Crash Course](https://www.youtube.com/watch?v=93pn8vLq93o)

- **Understanding React Context vs Redux:**
  - [React Context vs Redux](https://www.smashingmagazine.com/2020/06/react-context-api-vs-redux/)




