
# Module 2: Advanced Front-end
## Week 4: Day 5 - Handling Side Effects in React with `useEffect`

### Outline
1. **Introduction to Side Effects**
2. **Understanding `useEffect` Hook**
3. **Common Use Cases for `useEffect`**
   - Data Fetching
   - Subscriptions
   - Timers
4. **Dependency Array**
5. **Cleanup Function**
6. **Handling Multiple Effects**
7. **Best Practices for `useEffect`**
8. **Q&A and Wrap-up**

### Course Content

#### 1. Introduction to Side Effects
- **What are Side Effects?**
  - Explain the concept of side effects in programming, particularly in React. Discuss how side effects can include data fetching, subscriptions, or manually manipulating the DOM.

#### 2. Understanding `useEffect` Hook
- **What is `useEffect`?**
  - Introduce the `useEffect` hook, explaining its purpose in managing side effects in functional components.
  
  ```javascript
  useEffect(() => {
      // Side effect logic here
  }, [dependencies]);
  ```

- **How it Works:**
  - Discuss how `useEffect` runs after the render phase and how it can be used to perform operations that affect other components or the outside world.

#### 3. Common Use Cases for `useEffect`
- **Data Fetching:**
  - Demonstrate how to fetch data using `useEffect` and `fetch` API, including handling loading states.

  ```javascript
  useEffect(() => {
      const fetchData = async () => {
          const response = await fetch('https://api.example.com/data');
          const data = await response.json();
          setData(data);
      };
      fetchData();
  }, []);
  ```

- **Subscriptions:**
  - Explain how to set up subscriptions (e.g., WebSocket, EventListeners) and the importance of cleanup.

  ```javascript
  useEffect(() => {
      const handleResize = () => {
          console.log(window.innerWidth);
      };
      window.addEventListener('resize', handleResize);
      return () => {
          window.removeEventListener('resize', handleResize);
      };
  }, []);
  ```

- **Timers:**
  - Show how to use timers or intervals within `useEffect`.

  ```javascript
  useEffect(() => {
      const timer = setInterval(() => {
          console.log('Tick');
      }, 1000);
      return () => clearInterval(timer);
  }, []);
  ```

#### 4. Dependency Array
- **Understanding Dependencies:**
  - Explain the role of the dependency array in `useEffect`, detailing how to control when the effect runs based on changes in dependencies.

  ```javascript
  useEffect(() => {
      // Effect logic
  }, [dependency1, dependency2]);
  ```

- **Behavior with Different Dependencies:**
  - Discuss the behavior of effects with no dependencies, an empty array, and with specific dependencies.

#### 5. Cleanup Function
- **Importance of Cleanup:**
  - Discuss the importance of cleanup functions in `useEffect` to avoid memory leaks and unintended side effects.

  ```javascript
  useEffect(() => {
      // Side effect logic
      return () => {
          // Cleanup logic here
      };
  }, []);
  ```

#### 6. Handling Multiple Effects
- **Organizing Effects:**
  - Discuss how to structure multiple `useEffect` calls within a single component to handle different side effects separately.

  ```javascript
  useEffect(() => {
      // Effect 1 logic
  }, [dependency1]);

  useEffect(() => {
      // Effect 2 logic
  }, [dependency2]);
  ```

#### 7. Best Practices for `useEffect`
- **Optimizing Performance:**
  - Share best practices for using `useEffect`, such as keeping effects simple, avoiding unnecessary dependencies, and correctly cleaning up.

- **Debugging `useEffect`:**
  - Provide tips for debugging common issues related to `useEffect`, such as infinite loops and missed updates.

#### 8. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions regarding the `useEffect` hook and side effects in React applications.

- **Recap of Key Takeaways:**
  - Summarize the importance of handling side effects in React and the effective use of the `useEffect` hook.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with React components and hooks.

### Additional Resources
- **React Documentation on `useEffect`:**
  - [React useEffect](https://reactjs.org/docs/hooks-effect.html)

- **Video Tutorial on `useEffect`:**
  - [React useEffect Hook Explained](https://www.youtube.com/watch?v=Z3M1q8OQ9pY)

- **Article on Best Practices:**
  - [Best Practices for useEffect](https://kentcdodds.com/blog/how-to-use-react-effect-hook)



