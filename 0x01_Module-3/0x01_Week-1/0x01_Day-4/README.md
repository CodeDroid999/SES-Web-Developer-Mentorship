# **Module 3: Beyond Front-end**
## **Week 1, Day 4: Advanced Next.js - API Routes, Middleware, and Authentication**

---

### **Submissions**

#### **Task 1: Setting Up API Routes in Next.js**
   - **Description**: Created custom API endpoints in the `pages/api` directory to handle CRUD operations for a sample resource (e.g., users).
   - **Code**:
      ```javascript
      // pages/api/users.js
      export default function handler(req, res) {
        if (req.method === 'GET') {
          res.status(200).json({ message: 'Fetched users successfully' });
        } else if (req.method === 'POST') {
          res.status(201).json({ message: 'User created successfully' });
        } else {
          res.setHeader('Allow', ['GET', 'POST']);
          res.status(405).end(`Method ${req.method} Not Allowed`);
        }
      }
      ```
   - **Screenshot**: Attached screenshot showing successful GET and POST requests using Postman or similar API testing tools.

#### **Task 2: Implementing Middleware for Logging Requests**
   - **Description**: Created middleware to log request details and applied it to the API routes.
   - **Code**:
      ```javascript
      // middleware/logger.js
      export default function logger(req, res, next) {
        console.log(`Received ${req.method} request on ${req.url}`);
        next();
      }
      ```
   - **Usage**: Imported and used `logger` middleware in the `pages/api/users.js` route.
   - **Screenshot**: Attached screenshot of the console output showing logs of incoming requests.

#### **Task 3: Implementing Basic Authentication**
   - **Description**: Set up a basic authentication check on API routes, verifying a sample token in headers.
   - **Code**:
      ```javascript
      // middleware/auth.js
      export default function auth(req, res, next) {
        const token = req.headers['authorization'];
        if (token === 'Bearer sample_token') {
          next();
        } else {
          res.status(403).json({ message: 'Forbidden: Invalid token' });
        }
      }
      ```
   - **Usage**: Applied `auth` middleware to protect specific API routes.
   - **Screenshot**: Attached screenshots demonstrating success with valid token and 403 response with invalid token.

#### **Task 4: Creating an Authentication API Route**
   - **Description**: Built an API route to handle user login, which verifies a sample user and returns a token.
   - **Code**:
      ```javascript
      // pages/api/login.js
      export default function login(req, res) {
        const { username, password } = req.body;
        if (username === 'admin' && password === 'password') {
          res.status(200).json({ token: 'sample_token' });
        } else {
          res.status(401).json({ message: 'Invalid credentials' });
        }
      }
      ```
   - **Screenshot**: Attached screenshot showing successful login response with a token and failed response for incorrect credentials.

#### **Task 5: Adding a Protected User Profile Route**
   - **Description**: Created a `/profile` API route to return user information, protected by the authentication middleware.
   - **Code**:
      ```javascript
      import auth from '../../middleware/auth';

      export default function handler(req, res) {
        auth(req, res, () => {
          res.status(200).json({ username: 'admin', email: 'admin@example.com' });
        });
      }
      ```
   - **Screenshot**: Attached screenshot showing successful access to profile route with token, and access denied without token.

---

### **Resources Review**
   - **Resources Consulted**:
      - [Next.js API Routes Documentation](https://nextjs.org/docs/api-routes/introduction)
      - [Next.js Middleware Examples](https://nextjs.org/docs/advanced-features/middleware)
   - **Summary**:
      - **API Routes**: Learned to create and protect custom API routes in Next.js.
      - **Middleware**: Implemented middleware functions to log requests and handle basic authentication.
      - **Authentication**: Practiced setting up a basic auth system with middleware to protect sensitive routes.

---

### **End-of-Day Reflection**
   - **Challenges**: Working with custom middleware in Next.js and managing different authentication states.
   - **Key Takeaways**: Middleware functions in Next.js enable flexible request handling and make it easier to manage protected routes.

