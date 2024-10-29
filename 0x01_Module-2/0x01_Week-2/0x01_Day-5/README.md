# Module 2: Advanced Front-end
## Week 2: Day 5 - Handling Side Effects in React with Hooks

### Outline
1. **Review of Day 4 Activities**
2. **Understanding Side Effects**
3. **Introduction to the useEffect Hook**
4. **Common Use Cases for useEffect**
5. **Cleanup in useEffect**
6. **Fetching Data with useEffect**
7. **Using Multiple Effects**
8. **Q&A and Wrap-up**

### Course Content

#### 1. Review of Day 4 Activities
- **Recap of State Management with Context API:**
  - Participants will share their experiences implementing the Context API and managing state within their applications.
  - Discuss challenges and solutions encountered while using the Context API.

#### 2. Understanding Side Effects
- **What are Side Effects?**
  - Side effects are operations that can affect other components outside of the function being executed. Examples include data fetching, subscriptions, or manually changing the DOM.

- **Why Handle Side Effects?**
  - Proper management of side effects is crucial for maintaining the integrity and performance of applications, ensuring that components behave as expected without causing unwanted side effects.

#### 3. Introduction to the useEffect Hook
- **What is useEffect?**
  - The `useEffect` hook is a built-in React hook that allows you to perform side effects in function components. It runs after the component renders and can be triggered on specific changes to state or props.

- **Basic Syntax:**
  ```javascript
  useEffect(() => {
    // Side effect logic here
  }, [dependencies]);
  ```

#### 4. Common Use Cases for useEffect
- **Data Fetching:**
  - Fetching data from an API when the component mounts.
  - Example:
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
  - Setting up subscriptions to external data sources or WebSocket connections.

- **Manual DOM Manipulation:**
  - Interacting with third-party libraries that require direct DOM access.

#### 5. Cleanup in useEffect
- **Why Cleanup is Important:**
  - Cleanup helps prevent memory leaks and ensures that subscriptions or timers are removed when a component unmounts.

- **Cleanup Function:**
  - Return a function from `useEffect` that performs cleanup.
  ```javascript
  useEffect(() => {
    const subscription = someAPI.subscribe();

    return () => {
      subscription.unsubscribe();
    };
  }, []);
  ```

#### 6. Fetching Data with useEffect
- **Example of Data Fetching:**
  - Setting up an effect to fetch data and handle loading and error states.
  ```javascript
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch('https://api.example.com/data');
        const result = await response.json();
        setData(result);
      } catch (error) {
        setError(error);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, []);
  ```

#### 7. Using Multiple Effects
- **When to Use Multiple useEffect Hooks:**
  - You can have multiple `useEffect` hooks in a single component to manage different side effects independently.
  ```javascript
  useEffect(() => {
    // Effect for fetching user data
  }, []);

  useEffect(() => {
    // Effect for fetching posts
  }, []);
  ```

#### 8. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions about the material covered, especially regarding the use of the `useEffect` hook and managing side effects.

- **Recap of Key Takeaways:**
  - Summarize the importance of handling side effects correctly and the role of `useEffect` in managing component lifecycle events.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with Git for version control.

### Additional Resources
- **React useEffect Documentation:**
  - [React useEffect Docs](https://reactjs.org/docs/hooks-effect.html)

- **Understanding Side Effects in React:**
  - [Managing Side Effects](https://www.robinwieruch.de/react-side-effects/)

- **Fetching Data in React:**
  - [Data Fetching in React with Hooks](https://kentcdodds.com/blog/data-fetching-with-react-hooks)



