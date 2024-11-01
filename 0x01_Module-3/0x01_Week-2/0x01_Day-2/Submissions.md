

# **Module 3: Beyond Front-end**
## **Week 1, Day 5: Advanced Authentication and SSR with Next.js**

---

### **Submissions**

#### **1. JWT Authentication Setup**

- **Description**: Implemented JSON Web Token (JWT) for user authentication. Created a token generation route to handle user login.
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
- **Test**: Verified with both correct and incorrect credentials for response validation.
- **Screenshot**: Captured API response with JWT on successful login.

---

#### **2. JWT Verification Middleware**

- **Description**: Developed middleware to verify the JWT token for authorized access control on API routes.
- **Code**:
   ```javascript
   // middleware/auth.js
   import jwt from 'jsonwebtoken';

   export default function auth(req, res, next) {
     const token = req.headers.authorization?.split(' ')[1];
     if (token) {
       jwt.verify(token, process.env.JWT_SECRET, (err, decoded) => {
         if (err) {
           return res.status(403).json({ message: 'Invalid token' });
         }
         req.user = decoded;
         next();
       });
     } else {
       res.status(403).json({ message: 'Authorization token missing' });
     }
   }
   ```
- **Usage**: Applied to restricted routes requiring valid authentication tokens.
- **Screenshot**: Displays allowed access with valid token and error for invalid/missing tokens.

---

#### **3. Server-Side Rendering (SSR) with Authentication**

- **Description**: Configured SSR on a protected profile page, verifying the token server-side before rendering.
- **Code**:
   ```javascript
   // pages/profile.js
   import jwt from 'jsonwebtoken';

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
- **Screenshot**: Shows profile page access for authenticated users, with redirection for unauthenticated users.

---

#### **4. Logout Implementation and Token Expiry**

- **Description**: Created a logout route to clear the token from cookies, ensuring session termination.
- **Code**:
   ```javascript
   // pages/api/logout.js
   export default function logout(req, res) {
     res.setHeader('Set-Cookie', 'token=; HttpOnly; Max-Age=0; Path=/');
     res.status(200).json({ message: 'Logged out successfully' });
   }
   ```
- **Screenshot**: Demonstrates logout action, with user redirected upon token clearance.

---

#### **5. Client-Side Route Protection**

- **Description**: Developed a ProtectedRoute component for client-side route protection, redirecting unauthenticated users.
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
- **Usage**: Wrapped protected pages with `ProtectedRoute`.
- **Screenshot**: Shows redirect to login when accessing protected pages without authentication.

---

### **Resources**
- **Consulted**:
   - [Next.js Authentication](https://nextjs.org/docs/authentication)
   - [JWT.io - JSON Web Tokens](https://jwt.io/introduction/)
   - [React Context API for User Authentication](https://reactjs.org/docs/context.html)
- **Summary**:
   - JWT-based secure authentication implemented
   - SSR integrated with server-side token validation
   - Both client-side and server-side route protection achieved

---

### **Reflection**
- **Challenges**: Ensuring smooth integration of SSR with token verification required meticulous cookie management and session handling.
- **Learning Outcome**: Securing pages with SSR and authentication boosts app reliability and user-specific data handling.

