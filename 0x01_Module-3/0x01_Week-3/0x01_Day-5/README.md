#### **Week 3: Day 5 – Advanced Techniques in State Management**

---

### **Outline**  
1. **Overview of State Management in Modern Applications**  
2. **React State Management with Context API**  
3. **Advanced Redux Patterns and Middleware (Redux Thunk/Saga)**  
4. **State Management in Vue.js (Vuex and Pinia)**  
5. **Activity: Building a Small Application with Advanced State Management Techniques**  

---

### **Course Content**

#### **1. Overview of State Management in Modern Applications**  
- **Definition:**  
  State management is the process of managing the state of an application, ensuring predictable behavior and data flow.  
- **Why Use State Management?**  
  - Centralizes data for easier debugging and consistency.  
  - Simplifies complex data-sharing logic between components.  
  - Enables scalability in large applications.  
- **Approaches to State Management:**  
  - Local component state (useState/useReducer).  
  - Global state management libraries (Redux, Vuex, Pinia).  
  - Context-based approaches (React Context API).  

---

#### **2. React State Management with Context API**  
- **Introduction to React Context API:**  
  - Enables global state sharing without prop drilling.  
- **Steps to Implement:**  
  1. Create a `Context` object.  
  2. Wrap your component tree with a `Provider`.  
  3. Use the `useContext` hook to consume the context.  

  **Example:**  
  ```jsx
  import React, { createContext, useContext, useState } from 'react';

  const ThemeContext = createContext();

  const App = () => {
    const [theme, setTheme] = useState("light");

    return (
      <ThemeContext.Provider value={{ theme, setTheme }}>
        <Toolbar />
      </ThemeContext.Provider>
    );
  };

  const Toolbar = () => {
    const { theme, setTheme } = useContext(ThemeContext);
    return (
      <div>
        <p>Current Theme: {theme}</p>
        <button onClick={() => setTheme("dark")}>Change Theme</button>
      </div>
    );
  };
  ```

---

#### **3. Advanced Redux Patterns and Middleware (Redux Thunk/Saga)**  
- **Why Use Middleware?**  
  - To handle side effects like asynchronous actions (API calls).  
- **Redux Thunk:**  
  - Simplifies async logic with functions that dispatch actions.  
  **Example:**  
  ```javascript
  const fetchData = () => async (dispatch) => {
    dispatch({ type: "FETCH_START" });
    try {
      const data = await fetch("/api/data").then((res) => res.json());
      dispatch({ type: "FETCH_SUCCESS", payload: data });
    } catch (error) {
      dispatch({ type: "FETCH_ERROR", error });
    }
  };
  ```
- **Redux Saga:**  
  - Uses generator functions for handling async logic.  
  **Example:**  
  ```javascript
  function* fetchDataSaga() {
    try {
      const data = yield call(fetch, "/api/data");
      yield put({ type: "FETCH_SUCCESS", payload: data });
    } catch (error) {
      yield put({ type: "FETCH_ERROR", error });
    }
  }

  function* watchFetchData() {
    yield takeEvery("FETCH_START", fetchDataSaga);
  }
  ```

---

#### **4. State Management in Vue.js (Vuex and Pinia)**  
- **Vuex Overview:**  
  - Centralized state management for Vue apps.  
  - Follows the Flux pattern with **state**, **getters**, **mutations**, and **actions**.  

  **Basic Example:**  
  ```javascript
  const store = new Vuex.Store({
    state: {
      count: 0,
    },
    mutations: {
      increment(state) {
        state.count++;
      },
    },
    actions: {
      incrementAsync({ commit }) {
        setTimeout(() => {
          commit("increment");
        }, 1000);
      },
    },
  });
  ```

- **Pinia Overview:**  
  - Lightweight alternative to Vuex with a simpler API.  
  **Basic Example:**  
  ```javascript
  import { defineStore } from "pinia";

  const useCounterStore = defineStore("counter", {
    state: () => ({
      count: 0,
    }),
    actions: {
      increment() {
        this.count++;
      },
    },
  });
  ```

---

#### **5. Activity: Building a Small Application with Advanced State Management Techniques**  
**Task:**  
- Build a small to-do application with advanced state management:  
  - Use React and Redux Thunk for async actions, or Vue.js with Vuex/Pinia.  
  - Implement the following:  
    - Add, remove, and update tasks.  
    - Store tasks in the global state.  
    - Simulate saving data to an API.  

---

### **Resources**  
- [Redux Official Documentation](https://redux.js.org/)  
- [Redux Thunk Documentation](https://github.com/reduxjs/redux-thunk)  
- [Redux Saga Documentation](https://redux-saga.js.org/)  
- [Vuex Official Guide](https://vuex.vuejs.org/)  
- [Pinia Official Guide](https://pinia.vuejs.org/)  

--- 

