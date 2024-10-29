
# Module 2: Advanced Front-end
## Week 4: Day 4 - State Management in React

### Outline
1. **Introduction to State in React**
2. **Using Local Component State**
3. **Lifting State Up**
4. **Using Context API for Global State Management**
5. **Introduction to Redux**
6. **Setting Up Redux in a React Application**
7. **Creating Actions and Reducers**
8. **Using Redux with React**
9. **Best Practices for State Management**
10. **Q&A and Wrap-up**

### Course Content

#### 1. Introduction to State in React
- **Understanding State:**
  - Explain what state is in React and its role in managing data that can change over time within a component.

#### 2. Using Local Component State
- **Managing Local State:**
  - Discuss the use of the `useState` hook to manage local state in functional components.

  ```javascript
  const [count, setCount] = useState(0);

  const increment = () => setCount(count + 1);
  ```

- **Effect of State Changes:**
  - Explain how state changes trigger re-renders of components and the implications for performance.

#### 3. Lifting State Up
- **When to Lift State Up:**
  - Discuss the scenarios where it’s beneficial to lift state up to a common ancestor component.

- **Example of Lifting State:**
  - Provide a code example that demonstrates how to lift state up.

  ```javascript
  const ParentComponent = () => {
      const [data, setData] = useState('');

      return <ChildComponent data={data} setData={setData} />;
  };
  ```

#### 4. Using Context API for Global State Management
- **Introduction to Context API:**
  - Explain the Context API and its usefulness for managing global state without prop drilling.

- **Creating a Context:**
  - Demonstrate how to create a context and provide it to components.

  ```javascript
  const MyContext = createContext();

  const App = () => (
      <MyContext.Provider value={{ /* some value */ }}>
          <MyComponent />
      </MyContext.Provider>
  );
  ```

- **Consuming Context:**
  - Show how to consume context in child components using the `useContext` hook.

  ```javascript
  const value = useContext(MyContext);
  ```

#### 5. Introduction to Redux
- **What is Redux?**
  - Provide an overview of Redux as a state management library, highlighting its core principles: Single Source of Truth, State is Read-Only, and Changes are Made with Pure Functions.

#### 6. Setting Up Redux in a React Application
- **Installing Redux:**
  - Show how to install Redux and React-Redux in a React application.

  ```bash
  npm install redux react-redux
  ```

- **Creating the Store:**
  - Explain how to create a Redux store and provide it to the application.

  ```javascript
  const store = createStore(rootReducer);

  const App = () => (
      <Provider store={store}>
          <MyComponent />
      </Provider>
  );
  ```

#### 7. Creating Actions and Reducers
- **Actions:**
  - Explain what actions are in Redux and how to create action creators.

  ```javascript
  const incrementAction = () => ({
      type: 'INCREMENT',
  });
  ```

- **Reducers:**
  - Discuss reducers and how they determine how the state changes in response to actions.

  ```javascript
  const counterReducer = (state = initialState, action) => {
      switch (action.type) {
          case 'INCREMENT':
              return { ...state, count: state.count + 1 };
          default:
              return state;
      }
  };
  ```

#### 8. Using Redux with React
- **Connecting Components:**
  - Explain how to connect React components to Redux state using the `connect` function or hooks like `useSelector` and `useDispatch`.

  ```javascript
  const count = useSelector((state) => state.count);
  const dispatch = useDispatch();

  const handleIncrement = () => {
      dispatch(incrementAction());
  };
  ```

#### 9. Best Practices for State Management
- **State Management Strategies:**
  - Discuss strategies for choosing when to use local state, context, or Redux based on the complexity and requirements of the application.

- **Code Organization:**
  - Highlight best practices for organizing state management code to enhance maintainability and readability.

#### 10. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions regarding state management in React applications.

- **Recap of Key Takeaways:**
  - Summarize the importance of effective state management in React and the various tools and techniques available.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with React components and hooks.

### Additional Resources
- **React Documentation on State:**
  - [React State](https://reactjs.org/docs/state-and-lifecycle.html)

- **Context API Documentation:**
  - [React Context API](https://reactjs.org/docs/context.html)

- **Redux Documentation:**
  - [Redux](https://redux.js.org/introduction/getting-started)

- **Video Tutorial on Redux:**
  - [Redux Crash Course](https://www.youtube.com/watch?v=9boLU4YXoxg)



