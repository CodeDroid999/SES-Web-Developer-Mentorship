# Module 2: Advanced Front-end
## Week 1: Day 4 - Implementing Advanced Features

### Outline
1. **Review of Day 3 Activities**
2. **Introduction to Routing in React**
3. **Implementing Nested Routes**
4. **Integrating Form Handling with Formik**
5. **Managing Side Effects with useEffect**
6. **Q&A and Wrap-up**

### Course Content

#### 1. Review of Day 3 Activities
- Recap the application enhancements made on Day 3, including state management and custom hooks.
- Discuss the importance of advanced features in improving user experience.

#### 2. Introduction to Routing in React
- **Understanding React Router:**
  - Overview of client-side routing and its importance in single-page applications.
  - Introduction to React Router and its core components (BrowserRouter, Route, Link).

- **Setting Up React Router:**
  - Install React Router in your existing project.

  ```bash
  npm install react-router-dom
  ```

- **Basic Routing Example:**

  ```jsx
  import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

  function App() {
    return (
      <Router>
        <nav>
          <Link to="/">Home</Link>
          <Link to="/about">About</Link>
        </nav>
        <Route path="/" exact component={Home} />
        <Route path="/about" component={About} />
      </Router>
    );
  }
  ```

#### 3. Implementing Nested Routes
- **Creating Nested Routes:**
  - Understanding the concept of nested routing for better organization of components.

  ```jsx
  <Route path="/users" component={Users}>
    <Route path="/:id" component={UserDetail} />
  </Route>
  ```

- **Dynamic Routing:**
  - Implement dynamic routes to display user details based on the user ID.

#### 4. Integrating Form Handling with Formik
- **Introduction to Formik:**
  - Overview of Formik for managing forms in React applications.

- **Setting Up Formik:**
  - Install Formik.

  ```bash
  npm install formik
  ```

- **Basic Form Example:**

  ```jsx
  import { Formik, Form, Field } from 'formik';

  function MyForm() {
    return (
      <Formik
        initialValues={{ name: '' }}
        onSubmit={(values) => {
          console.log(values);
        }}
      >
        <Form>
          <Field name="name" placeholder="Enter your name" />
          <button type="submit">Submit</button>
        </Form>
      </Formik>
    );
  }
  ```

#### 5. Managing Side Effects with useEffect
- **Understanding useEffect:**
  - Explanation of how to manage side effects in functional components using the `useEffect` hook.

- **Examples of useEffect Usage:**
  - Fetching data on component mount.
  - Subscribing to events or timers.

  ```jsx
  useEffect(() => {
    // Fetch data or set up subscriptions here
    return () => {
      // Cleanup code here
    };
  }, []);
  ```

#### 6. Q&A and Wrap-up
- Open floor for questions regarding routing, forms, and side effects.
- Recap of key takeaways from the day and how they integrate with previous topics.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with Git for version control.

### Additional Resources
- [React Router Documentation](https://reactrouter.com/)
- [Formik Documentation](https://formik.org/docs/overview)
- [Using useEffect](https://reactjs.org/docs/hooks-effect.html)



