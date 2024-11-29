# **Submission Instructions for Week 3: Day 5 – Advanced Techniques in State Management**

Welcome to **Week 3, Day 5** of your web development mentorship program! In this section, we will cover advanced state management techniques across various frameworks like React, Vue.js, and their associated state management libraries. 

To submit your tasks for today, please follow the instructions below:

---

## **1. Create a New Git Repository or Use Your Existing Repository**
- If you haven’t already, create a new repository on GitHub to store your project for this week.
- If you already have a repository, ensure that all files for this week's tasks are properly committed and pushed.

---

## **2. Build the Application Based on the Task**
For this day's task, you are required to build a small to-do application implementing advanced state management techniques. Here are the instructions for what you should include in your submission:

### **Features for the Application:**
- **React with Redux Thunk or Vue.js with Vuex/Pinia** (based on your choice).
- Add, remove, and update tasks.
- Tasks should be stored in the global state.
- Simulate saving tasks to an API (you can use `setTimeout` or `fake API`).
- Use either **Redux Thunk** or **Vuex/Pinia** for managing async actions, depending on the framework you're working with.

---

## **3. Code Structure**
Ensure your project is structured properly and follows the best practices for your chosen framework. The general structure should look like the following:

For **React with Redux Thunk**:
```plaintext
/src
  /actions
    - taskActions.js
  /components
    - TaskList.js
    - TaskItem.js
  /reducers
    - taskReducer.js
  /store
    - store.js
  /App.js
  /index.js
  /manifest.json
```

For **Vue.js with Vuex/Pinia**:
```plaintext
/src
  /store
    - store.js (Vuex) or counterStore.js (Pinia)
  /components
    - TaskList.vue
    - TaskItem.vue
  /App.vue
  /main.js
  /manifest.json
```

---

## **4. Requirements for the Submission**
- **State Management**: Implement global state management with React’s Context API/Redux (or Vuex/Pinia).
- **Async Logic**: Use Redux Thunk or Vuex/Pinia for handling async actions, such as fetching tasks or simulating saving tasks to an API.
- **Component Interaction**: Ensure proper interaction between components (e.g., TaskList and TaskItem).
- **UI/UX**: Build a simple, intuitive interface for adding, removing, and editing tasks.

---

## **5. Push Your Code to GitHub**
- After building the application, commit all your changes to your local repository.
- Push the code to your GitHub repository.

Example commit message:  
`Implemented state management and async actions for to-do app in React/Redux or Vue/Vuex`

---

## **6. Create a Pull Request (PR)**
- Once you’ve pushed the code to GitHub, create a pull request with the changes. Title the PR with **"Week 3 Day 5 – Advanced State Management"**.
- In the description of the PR, briefly explain what you have implemented and how it addresses the task requirements.

---

## **7. Submit the Pull Request**
Once you have created the pull request, submit the PR link to your instructor or mentor via the platform's designated submission method.

---

## **8. Optional (if applicable): Include Screenshots/Screen Recording**
- If you’ve built a UI, you can include screenshots or a screen recording of the application running. This will help the instructor verify that your app is working as expected.

---

## **Resources**
- [Redux Official Documentation](https://redux.js.org/)
- [Redux Thunk Documentation](https://github.com/reduxjs/redux-thunk)
- [Vuex Official Guide](https://vuex.vuejs.org/)
- [Pinia Official Guide](https://pinia.vuejs.org/)

---
