# Module 2: Advanced Front-end
## Week 2: Day 4 - State Management in React with Context API

### Outline
1. **Review of Day 3 Activities**
2. **Understanding State Management**
3. **Introduction to Context API**
4. **Creating a Context**
5. **Using Context in Functional Components**
6. **Updating Context State**
7. **Context vs. Redux**
8. **Q&A and Wrap-up**

### Course Content

#### 1. Review of Day 3 Activities
- **Recap of React Router and Navigation:**
  - Participants will share their experiences with implementing React Router, including dynamic routing and handling 404 pages.
  - Discuss any challenges faced while managing nested routes.

#### 2. Understanding State Management
- **What is State Management?**
  - State management refers to the handling of state in an application. In React, state can be local (within components) or global (shared across components).

- **Why is State Management Important?**
  - As applications grow, managing state efficiently becomes crucial to ensure consistent UI updates and manage data flow.

#### 3. Introduction to Context API
- **What is Context API?**
  - The Context API is a built-in feature in React that allows for sharing data between components without having to pass props down manually at every level.

- **Key Features:**
  - It helps avoid prop drilling (passing data through many layers of components).
  - It allows for a more straightforward way to manage global state in small to medium-sized applications.

#### 4. Creating a Context
- **Defining a Context:**
  - Create a context using the `createContext` method from React.
  ```javascript
  import React, { createContext } from 'react';

  const MyContext = createContext();
  ```

- **Creating a Context Provider:**
  - The provider component allows you to set the value that can be accessed by any child components.
  ```javascript
  const MyProvider = ({ children }) => {
    const [state, setState] = React.useState(initialState);

    return (
      <MyContext.Provider value={{ state, setState }}>
        {children}
      </MyContext.Provider>
    );
  };
  ```

#### 5. Using Context in Functional Components
- **Consuming Context:**
  - Use the `useContext` hook to access context data within functional components.
  ```javascript
  import { useContext } from 'react';

  const MyComponent = () => {
    const { state, setState } = useContext(MyContext);

    return <div>{state.someValue}</div>;
  };
  ```

- **Updating Context State:**
  - You can update the context state by calling the `setState` function within the component.
  ```javascript
  const updateValue = () => {
    setState({ ...state, someValue: 'New Value' });
  };
  ```

#### 6. Context vs. Redux
- **When to Use Context API:**
  - Ideal for applications that do not require complex state management.
  - Suitable for simple data sharing between components.

- **When to Use Redux:**
  - Recommended for larger applications with complex state logic and actions.
  - Better suited for global state management with middleware support for handling asynchronous actions.

#### 7. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions about the material covered, particularly regarding using Context API in their applications.

- **Recap of Key Takeaways:**
  - Summarize the importance of state management in React and how the Context API can simplify sharing state across components.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with Git for version control.

### Additional Resources
- **React Context Documentation:**
  - [React Context Docs](https://reactjs.org/docs/context.html)
  
- **Using the Context API:**
  - [Context API Tutorial](https://reactjs.org/docs/context.html#api)

- **Context API vs. Redux:**
  - [When to Use Context API or Redux](https://www.freecodecamp.org/news/context-api-vs-redux-what-should-you-use/)



