
#### **1. Implementing Server-Side Authentication Check with Role-Based Access Control (RBAC)**
- **Description**: Implemented a server-side authentication check that also verifies user roles, enabling RBAC for specific pages.
- **Code**:
   ```javascript
   export async function getServerSideProps(context) {
     const token = context.req.cookies.token || '';
     
     try {
       const user = jwt.verify(token, process.env.JWT_SECRET);
       if (user.role !== 'admin') {
         return { redirect: { destination: '/403', permanent: false } };
       }
       return { props: { user } };
     } catch (error) {
       return { redirect: { destination: '/login', permanent: false } };
     }
   }
   ```
- **Testing**:
   - Tested access by navigating to the protected page with different roles (admin, editor, guest).
   - Verified that users with non-admin roles were redirected to a 403 error page.
- **Screenshot**: Shows 403 page for users who lack permission.

---

#### **2. Custom 403 Error Page**
- **Description**: Designed a custom 403 error page to inform users when they lack permission to access certain pages.
- **Code**:
   ```javascript
   // pages/403.js
   export default function ForbiddenPage() {
     return (
       <div>
         <h1>403 - Forbidden</h1>
         <p>You do not have permission to view this page.</p>
         <a href="/">Return to Home</a>
       </div>
     );
   }
   ```
- **Testing**:
   - Accessed protected pages with non-authorized roles and confirmed redirection to the 403 page.
   - Verified links back to the home page worked as expected.
- **Screenshot**: Included screenshots showing the 403 error page layout and functionality.

---

#### **3. Adding Conditional Rendering for Role-Based Content**
- **Description**: Added conditional rendering within a component to display content based on the user role.
- **Code**:
   ```javascript
   function Dashboard({ user }) {
     return (
       <div>
         <h1>Welcome, {user.name}</h1>
         {user.role === 'admin' && (
           <div>
             <h2>Admin Panel</h2>
             <p>Only admins can see this content.</p>
           </div>
         )}
         {user.role === 'editor' && (
           <div>
             <h2>Editor Tools</h2>
             <p>Only editors can see this content.</p>
           </div>
         )}
       </div>
     );
   }
   ```
- **Testing**:
   - Logged in with different roles and confirmed that content displayed accurately based on the user's role.
- **Screenshot**: Shows conditional content appearing based on user role.

---

### **Resources**
- **Reference Links**:
   - [Next.js Authentication Patterns](https://nextjs.org/docs/authentication)
   - [Role-Based Access Control (RBAC) in Web Apps](https://auth0.com/docs/authorization/rbac)
   - [Custom Error Pages in Next.js](https://nextjs.org/docs/advanced-features/custom-error-page)

---

### **Reflection**
- **Challenges**: Managing role checks and dynamic redirection required testing various access scenarios to ensure consistent functionality.
- **Outcome**: Successfully implemented secure role-based access with responsive, user-friendly error handling.

