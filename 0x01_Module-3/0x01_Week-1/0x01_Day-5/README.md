# **Module 3: Beyond Front-end**
## **Week 1, Day 5: Advanced Authentication and SSR with Next.js**

---

### **Submissions**

#### **Task 1: Implementing JWT Authentication in Next.js**
   - **Description**: Created JWT-based authentication for secure login, generating a token upon user login.
   - **Code**:
      ```javascript
      // pages/api/login.js
      import jwt from 'jsonwebtoken';

      export default function login(req, res) {
        const { username, password } = req.body;
        if (username === 'admin' && password === 'password') {
          const token = jwt.sign({ username }, process.env.JWT_SECRET, { expiresIn: '1h' });
          res.status(200).json({ token });
        } else {
          res.status(401).json({ message: 'Invalid credentials' });
        }
      }
      ```
   - **Usage**: Tested token generation using valid and invalid credentials.
   - **Screenshot**: Attached screenshots of API responses showing generated JWT for successful login.

#### **Task 2: Setting Up Token Verification Middleware**
   - **Description**: Created middleware to verify JWT tokens and protect routes from unauthorized access.
   - **Code**:
      ```javascript
      // middleware/auth.js
      import jwt from 'jsonwebtoken';

      export default function auth(req, res, next) {
        const token = req.headers.authorization?.split(' ')[1];
        if (token) {
          jwt.verify(token, process.env.JWT_SECRET, (err, decoded) => {
            if (err) {
              return res.status(403).json({ message: 'Token is invalid' });
            }
            req.user = decoded;
            next();
          });
        } else {
          res.status(403).json({ message: 'Authorization token missing' });
        }
      }
      ```
   - **Usage**: Applied `auth` middleware to protect sensitive API routes.
   - **Screenshot**: Attached screenshots showing a successful access when token is valid and 403 error when it is missing or invalid.

#### **Task 3: Integrating Authentication with Server-Side Rendering (SSR)**
   - **Description**: Set up SSR for a profile page, checking the user’s authentication token on the server.
   - **Code**:
      ```javascript
      // pages/profile.js
      import auth from '../middleware/auth';

      export async function getServerSideProps(context) {
        const token = context.req.cookies.token || '';
        let user = null;
        
        try {
          user = jwt.verify(token, process.env.JWT_SECRET);
        } catch (error) {
          return { redirect: { destination: '/login', permanent: false } };
        }
        
        return {
          props: { user },
        };
      }

      export default function Profile({ user }) {
        return <div>Welcome, {user?.username}!</div>;
      }
      ```
   - **Screenshot**: Attached screenshots showing the profile page accessible only when a valid token is available.

#### **Task 4: Setting Up Logout and Token Expiry**
   - **Description**: Created a logout route to clear the authentication token and redirect the user to the login page.
   - **Code**:
      ```javascript
      // pages/api/logout.js
      export default function logout(req, res) {
        res.setHeader('Set-Cookie', 'token=; HttpOnly; Max-Age=0; Path=/');
        res.status(200).json({ message: 'Logged out successfully' });
      }
      ```
   - **Screenshot**: Attached screenshot showing successful token removal and redirection on logout.

#### **Task 5: Protecting Client-Side Routes Using Next.js Router**
   - **Description**: Added client-side route protection for certain pages, redirecting unauthenticated users to the login page.
   - **Code**:
      ```javascript
      // components/ProtectedRoute.js
      import { useRouter } from 'next/router';
      import { useEffect } from 'react';
      import { useAuth } from '../context/AuthContext';

      export default function ProtectedRoute({ children }) {
        const router = useRouter();
        const { user } = useAuth();

        useEffect(() => {
          if (!user) {
            router.push('/login');
          }
        }, [user]);

        return user ? children : null;
      }
      ```
   - **Usage**: Wrapped protected pages with `ProtectedRoute` to restrict access.
   - **Screenshot**: Attached screenshot showing redirection to the login page when accessing protected pages without authentication.

---

### **Resources Review**
   - **Resources Consulted**:
      - [Next.js Server-Side Rendering (SSR)](https://nextjs.org/docs/basic-features/pages#server-side-rendering)
      - [JSON Web Token (JWT) Authentication in Next.js](https://jwt.io/introduction/)
   - **Summary**:
      - **JWT Authentication**: Set up JWT for secure, stateless authentication.
      - **SSR with Authentication**: Integrated authentication with SSR for secure server-rendered pages.
      - **Route Protection**: Established both client-side and server-side route protection for improved security.

---

### **End-of-Day Reflection**
   - **Challenges**: Implementing token-based authentication with SSR required precise setup of token handling.
   - **Key Takeaways**: SSR with JWT authentication provides flexibility in rendering secure pages, allowing protected resources to be accessed only by authorized users.

