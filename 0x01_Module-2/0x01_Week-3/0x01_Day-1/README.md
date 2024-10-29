# Module 2: Advanced Front-end
## Week 3: Day 1 - React Routing with React Router

### Outline
1. **Review of Week 2**
2. **Introduction to React Router**
3. **Setting Up React Router**
4. **Basic Routing Concepts**
5. **Nested Routes**
6. **Dynamic Routing**
7. **Programmatic Navigation**
8. **Q&A and Wrap-up**

### Course Content

#### 1. Review of Week 2
- **Recap of Handling Side Effects in React with Hooks:**
  - Participants will share their experiences implementing side effects using the `useEffect` hook.
  - Discuss challenges and solutions encountered while managing side effects.

#### 2. Introduction to React Router
- **What is React Router?**
  - React Router is a standard library for routing in React applications, allowing navigation between different components without reloading the page.

- **Why Use React Router?**
  - It enables a single-page application (SPA) experience by maintaining the app's state and allowing for smooth transitions between different views.

#### 3. Setting Up React Router
- **Installation:**
  ```bash
  npm install react-router-dom
  ```

- **Basic Setup:**
  - Import necessary components from `react-router-dom` and wrap your application in a `BrowserRouter`.
  ```javascript
  import { BrowserRouter as Router } from 'react-router-dom';

  function App() {
    return (
      <Router>
        {/* Your routes will go here */}
      </Router>
    );
  }
  ```

#### 4. Basic Routing Concepts
- **Creating Routes:**
  - Use the `Route` component to define paths and associate them with components.
  ```javascript
  import { Route } from 'react-router-dom';

  <Route path="/" component={Home} />
  <Route path="/about" component={About} />
  ```

- **Switch Component:**
  - The `Switch` component renders the first child `<Route>` that matches the location.
  ```javascript
  import { Switch } from 'react-router-dom';

  <Switch>
    <Route path="/" component={Home} />
    <Route path="/about" component={About} />
  </Switch>
  ```

#### 5. Nested Routes
- **Creating Nested Routes:**
  - You can nest routes within other routes to create more complex navigation structures.
  ```javascript
  <Route path="/dashboard">
    <Dashboard />
    <Route path="/dashboard/profile" component={Profile} />
  </Route>
  ```

- **Example of Nested Routes:**
  ```javascript
  <Route path="/products">
    <Products />
    <Route path="/products/:productId" component={ProductDetail} />
  </Route>
  ```

#### 6. Dynamic Routing
- **Using URL Parameters:**
  - Define dynamic routes with parameters that can be accessed within the component.
  ```javascript
  <Route path="/user/:id" component={UserProfile} />
  ```

- **Accessing Parameters:**
  - Use the `useParams` hook to access route parameters.
  ```javascript
  import { useParams } from 'react-router-dom';

  function UserProfile() {
    const { id } = useParams();
    // Fetch user data based on the ID
  }
  ```

#### 7. Programmatic Navigation
- **Navigating Programmatically:**
  - Use the `useHistory` hook to navigate programmatically.
  ```javascript
  import { useHistory } from 'react-router-dom';

  function LoginButton() {
    const history = useHistory();

    const handleClick = () => {
      history.push('/dashboard');
    };

    return <button onClick={handleClick}>Login</button>;
  }
  ```

#### 8. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions about React Router and its implementation in their projects.

- **Recap of Key Takeaways:**
  - Summarize the importance of routing in React applications and the role of React Router in enhancing the user experience.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with Git for version control.

### Additional Resources
- **React Router Documentation:**
  - [React Router Docs](https://reactrouter.com/)

- **Getting Started with React Router:**
  - [React Router Tutorial](https://reactrouter.com/web/guides/quick-start)

- **Video Tutorial on React Router:**
  - [React Router Crash Course](https://www.youtube.com/watch?v=Law7wfdg_ls)


