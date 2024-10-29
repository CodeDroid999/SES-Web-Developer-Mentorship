# Module 2: Advanced Front-end
## Week 2: Day 3 - React Router and Navigation

### Outline
1. **Review of Day 2 Activities**
2. **Introduction to React Router**
3. **Setting Up React Router**
4. **Dynamic Routing**
5. **Route Parameters and Query Strings**
6. **Nested Routes**
7. **Handling 404 Pages and Redirects**
8. **Q&A and Wrap-up**

### Course Content

#### 1. Review of Day 2 Activities
- **Recap of Advanced Redux Concepts:**
  - Participants will share their experiences implementing selectors, Redux Toolkit, and Redux-Saga in their applications.
  - Discuss any challenges faced during testing Redux logic and how they resolved them.

#### 2. Introduction to React Router
- **What is React Router?**
  - React Router is a standard library for routing in React applications. It enables dynamic routing, allowing you to build single-page applications (SPAs) with navigation capabilities without refreshing the page.

- **Key Features:**
  - Declarative routing for React applications.
  - Nested routing capabilities.
  - Support for dynamic routing, enabling you to display different content based on the URL.

#### 3. Setting Up React Router
- **Installation:**
  - To use React Router, you need to install it via npm:
  ```bash
  npm install react-router-dom
  ```

- **Basic Setup:**
  - Wrap your main application component with the `BrowserRouter` to enable routing:
  ```javascript
  import React from 'react';
  import { BrowserRouter as Router } from 'react-router-dom';
  import App from './App';

  const Root = () => (
    <Router>
      <App />
    </Router>
  );

  export default Root;
  ```

#### 4. Dynamic Routing
- **Defining Routes:**
  - Use the `Route` component to define different routes in your application. For example, to create a route for the home page and about page:
  ```javascript
  import { Route, Switch } from 'react-router-dom';

  const App = () => (
    <Switch>
      <Route path="/" exact component={HomePage} />
      <Route path="/about" component={AboutPage} />
    </Switch>
  );
  ```

- **Understanding `Switch`:**
  - The `Switch` component renders the first `Route` that matches the current URL. This ensures that only one route is rendered at a time.

#### 5. Route Parameters and Query Strings
- **Route Parameters:**
  - Dynamic segments in routes can be defined using a colon `:` followed by the parameter name.
  ```javascript
  <Route path="/user/:id" component={UserProfile} />
  ```
  - In the `UserProfile` component, access the route parameter using `props.match.params.id`.

- **Query Strings:**
  - Query strings can be accessed using the `useLocation` hook from React Router.
  ```javascript
  import { useLocation } from 'react-router-dom';

  const UserProfile = () => {
    const query = new URLSearchParams(useLocation().search);
    const name = query.get('name'); // e.g., /user?id=1&name=John
    return <div>User: {name}</div>;
  };
  ```

#### 6. Nested Routes
- **Creating Nested Routes:**
  - You can create nested routes by defining routes inside a component. This is useful for complex UIs where sub-routes are related to a parent route.
  ```javascript
  <Route path="/dashboard" component={Dashboard}>
    <Route path="/dashboard/profile" component={Profile} />
    <Route path="/dashboard/settings" component={Settings} />
  </Route>
  ```

- **Rendering Nested Routes:**
  - In the `Dashboard` component, render the nested routes using the `children` prop:
  ```javascript
  const Dashboard = ({ children }) => (
    <div>
      <h1>Dashboard</h1>
      {children}
    </div>
  );
  ```

#### 7. Handling 404 Pages and Redirects
- **404 Not Found Page:**
  - To handle undefined routes, create a 404 page and use it as a fallback route.
  ```javascript
  <Route component={NotFoundPage} />
  ```

- **Redirecting Routes:**
  - You can redirect users from one route to another using the `Redirect` component.
  ```javascript
  <Redirect from="/old-route" to="/new-route" />
  ```

#### 8. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions about the material covered, particularly regarding routing challenges they may have faced.

- **Recap of Key Takeaways:**
  - Summarize the importance of React Router in building SPAs, understanding route parameters, handling nested routes, and managing redirects.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with Git for version control.

### Additional Resources
- **React Router Documentation:**
  - [React Router Docs](https://reactrouter.com/)
  
- **Dynamic Routing with React Router:**
  - [Dynamic Routing Guide](https://reactrouter.com/en/main/start/overview)

- **Handling Nested Routes:**
  - [Nested Routing Guide](https://reactrouter.com/en/main/components/routes)

- **404 Not Found Page and Redirects:**
  - [Redirects Guide](https://reactrouter.com/en/main/components/redirect)



