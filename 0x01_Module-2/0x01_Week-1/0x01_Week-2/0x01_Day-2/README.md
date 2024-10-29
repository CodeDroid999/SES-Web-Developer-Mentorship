# Module 2: Advanced Front-end
## Week 2: Day 2 - Advanced Redux Concepts

### Outline
1. **Review of Day 1 Activities**
2. **Selectors in Redux**
3. **Redux Toolkit Introduction**
4. **Handling Side Effects with Redux-Saga**
5. **Testing Redux Logic**
6. **Q&A and Wrap-up**

### Course Content

#### 1. Review of Day 1 Activities
- **Recap the Implementation of Redux:**
  - Participants will share their experiences from the previous day, highlighting the Redux store setup, the creation of actions, and the integration of reducers.
  - Discuss any challenges or successes encountered while implementing Redux in their applications.

#### 2. Selectors in Redux
- **What are Selectors?**
  - Selectors are functions used to retrieve and derive data from the Redux store. They enable a clean separation of data-fetching logic from component logic. By using selectors, you can avoid duplicating logic across components, which enhances maintainability.

- **Creating and Using Selectors:**
  - **Basic Selector:**
    ```javascript
    const selectMyState = (state) => state.myState;
    ```
    - This function retrieves the `myState` slice from the Redux store.

  - **Memoized Selectors:**
    - Memoized selectors, created with the `reselect` library, optimize performance by recalculating derived data only when the input data changes.
    ```javascript
    import { createSelector } from 'reselect';

    const selectItems = (state) => state.items;

    const selectActiveItems = createSelector(
      [selectItems],
      (items) => items.filter(item => item.active)
    );
    ```
    - Here, `selectActiveItems` will only recompute the filtered list when the `items` array changes, making it efficient for performance-critical applications.

- **Benefits of Using Selectors:**
  - Selectors help to encapsulate the logic for selecting data, making your components cleaner and easier to test.
  - They improve performance by reducing unnecessary re-renders.

#### 3. Redux Toolkit Introduction
- **What is Redux Toolkit?**
  - Redux Toolkit is the official, recommended way to write Redux applications. It simplifies the store setup process and helps reduce boilerplate code, making it easier to manage Redux state.

- **Key Features:**
  - **Simplified Store Setup:** Automatically configures the Redux DevTools and integrates middleware.
  - **`createSlice`:** A function that generates action creators and action types, along with reducers based on your specified state shape.

- **Setting Up Redux Toolkit:**
  - Install Redux Toolkit in your application:
  ```bash
  npm install @reduxjs/toolkit
  ```

- **Creating a Slice:**
  - You can create a slice that represents a portion of the Redux state and its associated logic.
  ```javascript
  import { createSlice } from '@reduxjs/toolkit';

  const mySlice = createSlice({
    name: 'mySlice',
    initialState: { items: [] },
    reducers: {
      addItem: (state, action) => {
        state.items.push(action.payload);
      },
      removeItem: (state, action) => {
        state.items = state.items.filter(item => item.id !== action.payload.id);
      },
    },
  });

  export const { addItem, removeItem } = mySlice.actions;
  export default mySlice.reducer;
  ```
  - Here, `mySlice` automatically creates action creators (`addItem` and `removeItem`) and the corresponding reducers for modifying the state.

#### 4. Handling Side Effects with Redux-Saga
- **Introduction to Redux-Saga:**
  - Redux-Saga is a middleware library that helps to manage side effects in Redux applications, such as data fetching, by using generator functions. This makes it easier to handle asynchronous actions and complex logic.

- **Setting Up Redux-Saga:**
  - Install Redux-Saga in your application:
  ```bash
  npm install redux-saga
  ```

- **Creating Sagas:**
  - Sagas are implemented as generator functions that yield effects, which can be actions, delays, or API calls.
  ```javascript
  import { takeEvery, call, put } from 'redux-saga/effects';

  function* fetchDataSaga(action) {
    try {
      const data = yield call(fetchDataFromAPI, action.payload);
      yield put({ type: 'FETCH_SUCCESS', payload: data });
    } catch (error) {
      yield put({ type: 'FETCH_FAILURE', payload: error.message });
    }
  }

  function* watchFetchData() {
    yield takeEvery('FETCH_REQUEST', fetchDataSaga);
  }
  ```
  - In this example, `fetchDataSaga` handles the side effect of fetching data from an API. The `call` effect invokes the asynchronous function, and `put` dispatches an action to update the store.

- **Integrating Sagas with Redux:**
  - Integrate the saga middleware into your Redux store:
  ```javascript
  import createSagaMiddleware from 'redux-saga';
  const sagaMiddleware = createSagaMiddleware();
  const store = createStore(myReducer, applyMiddleware(sagaMiddleware));

  sagaMiddleware.run(watchFetchData);
  ```

#### 5. Testing Redux Logic
- **Importance of Testing Redux:**
  - Testing Redux logic is crucial for ensuring that your application behaves correctly, especially when managing complex state and side effects.

- **Testing Reducers and Actions:**
  - Write tests for your reducers and action creators using a testing framework like Jest.
  ```javascript
  test('myReducer handles MY_ACTION correctly', () => {
    const initialState = { items: [] };
    const action = { type: 'MY_ACTION', payload: { id: 1, name: 'Test Item' } };
    const newState = myReducer(initialState, action);
    expect(newState.items).toContainEqual(action.payload);
  });
  ```

- **Testing Sagas:**
  - You can use libraries like `redux-saga-test-plan` to test your sagas in isolation.
  ```javascript
  import { runSaga } from 'redux-saga';
  import { fetchDataSaga } from './sagas';

  test('fetchDataSaga works correctly', async () => {
    const dispatched = [];
    await runSaga({ dispatch: (action) => dispatched.push(action) }, fetchDataSaga, { payload: 'test' }).toPromise();
    expect(dispatched).toContainEqual({ type: 'FETCH_SUCCESS', payload: expectedData });
  });
  ```

#### 6. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions about the material covered, and provide clarifications as needed.

- **Recap of Key Takeaways:**
  - Summarize the importance of selectors, the benefits of using Redux Toolkit, how to handle side effects with Redux-Saga, and the necessity of testing Redux logic.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with Git for version control.

### Additional Resources
- **Selectors and Reselect:**
  - [Reselect Documentation](https://github.com/reduxjs/reselect)
  
- **Redux Toolkit:**
  - [Redux Toolkit Documentation](https://redux-toolkit.js.org/)
  
- **Redux-Saga:**
  - [Redux-Saga Documentation](https://redux-saga.js.org/)
  
- **Testing with Jest:**
  - [Jest Documentation](https://jestjs.io/docs/getting-started)
  
- **Testing Redux Applications:**
  - [Testing Redux Applications](https://redux.js.org/usage/writing-tests)


