# Module 2: Advanced Front-end
## Week 3: Day 4 - Advanced State Management with Redux Thunk and Middleware

### Outline
1. **Review of Day 3: State Management in React with Context API and Redux**
2. **Introduction to Middleware in Redux**
3. **What is Redux Thunk?**
4. **Setting Up Redux Thunk**
5. **Async Actions with Redux Thunk**
6. **Error Handling in Async Actions**
7. **Combining Multiple Middleware**
8. **Q&A and Wrap-up**

### Course Content

#### 1. Review of Day 3: State Management in React with Context API and Redux
- **Recap of Key Concepts:**
  - Participants will share their implementations from Day 3, discussing how they used Context API and Redux in their projects.

#### 2. Introduction to Middleware in Redux
- **What is Middleware?**
  - Middleware is a way to extend Redux's capabilities. It is a higher-order function that wraps the store's dispatch function to intercept actions dispatched to the store.

- **Why Use Middleware?**
  - Middleware allows for logging, handling asynchronous actions, and more, enabling a more structured approach to side effects in Redux applications.

#### 3. What is Redux Thunk?
- **Understanding Redux Thunk:**
  - Redux Thunk is a middleware that allows action creators to return a function instead of an action object. This function can perform asynchronous operations before dispatching an action.

- **Why Use Redux Thunk?**
  - It simplifies the process of handling async actions, such as API calls, by allowing you to write action creators that return functions.

#### 4. Setting Up Redux Thunk
- **Installation:**
  ```bash
  npm install redux-thunk
  ```

- **Applying Middleware:**
  ```javascript
  import { createStore, applyMiddleware } from 'redux';
  import thunk from 'redux-thunk';

  const store = createStore(reducer, applyMiddleware(thunk));
  ```

#### 5. Async Actions with Redux Thunk
- **Creating Async Action Creators:**
  ```javascript
  const fetchData = () => {
    return async (dispatch) => {
      dispatch({ type: 'FETCH_DATA_REQUEST' });

      try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        dispatch({ type: 'FETCH_DATA_SUCCESS', payload: data });
      } catch (error) {
        dispatch({ type: 'FETCH_DATA_FAILURE', error });
      }
    };
  };
  ```

- **Dispatching Async Actions:**
  ```javascript
  const MyComponent = () => {
    const dispatch = useDispatch();
    
    const handleFetchData = () => {
      dispatch(fetchData());
    };

    return <button onClick={handleFetchData}>Fetch Data</button>;
  };
  ```

#### 6. Error Handling in Async Actions
- **Managing Errors:**
  - It’s essential to handle errors in your async actions to provide a better user experience.
  ```javascript
  const fetchData = () => {
    return async (dispatch) => {
      dispatch({ type: 'FETCH_DATA_REQUEST' });

      try {
        const response = await fetch('https://api.example.com/data');
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const data = await response.json();
        dispatch({ type: 'FETCH_DATA_SUCCESS', payload: data });
      } catch (error) {
        dispatch({ type: 'FETCH_DATA_FAILURE', error: error.message });
      }
    };
  };
  ```

#### 7. Combining Multiple Middleware
- **Using Multiple Middleware:**
  - You can combine multiple middleware in your Redux store for enhanced functionality.
  ```javascript
  import { createStore, applyMiddleware } from 'redux';
  import thunk from 'redux-thunk';
  import logger from 'redux-logger'; // Another middleware for logging actions

  const store = createStore(reducer, applyMiddleware(thunk, logger));
  ```

#### 8. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions about Redux Thunk, middleware, and their implementations from Day 4 activities.

- **Recap of Key Takeaways:**
  - Summarize the importance of middleware and how Redux Thunk simplifies async action handling in Redux applications.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with Git for version control.

### Additional Resources
- **Redux Thunk Documentation:**
  - [Redux Thunk](https://github.com/reduxjs/redux-thunk)

- **Understanding Middleware in Redux:**
  - [Middleware in Redux](https://redux.js.org/advanced/middleware)

- **Video Tutorial on Redux Thunk:**
  - [Redux Thunk Tutorial](https://www.youtube.com/watch?v=4uHya1O3vQo)

- **Error Handling in Redux:**
  - [Error Handling in Redux Thunk](https://medium.com/@parshakova/error-handling-with-redux-thunk-735baf749e91)

