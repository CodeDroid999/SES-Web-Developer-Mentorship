#### **1. Dynamic Product Page Implementation**
- **Description**: Created a dynamic route for product pages that fetches product details based on the URL parameter.
- **Code**:
   ```javascript
   // pages/product/[id].js
   import { useRouter } from 'next/router';

   export async function getServerSideProps(context) {
     const { id } = context.params;
     const res = await fetch(`https://api.example.com/products/${id}`);
     const product = await res.json();

     if (!product) {
       return { notFound: true };
     }

     return { props: { product } };
   }

   export default function ProductPage({ product }) {
     return (
       <div>
         <h1>{product.name}</h1>
         <p>{product.description}</p>
       </div>
     );
   }
   ```
- **Testing**:
   - Accessed multiple `/product/[id]` URLs; each returned the correct product details.
   - Verified that pages with invalid IDs rendered a 404.
- **Screenshots**: Included screenshots of valid product pages and the 404 page for non-existing products.

---

#### **2. Error Handling with Conditional Redirects**
- **Description**: Added error handling for data retrieval in SSR with conditional redirects to 404.
- **Code**:
   ```javascript
   export async function getServerSideProps(context) {
     const res = await fetch(`https://api.example.com/data`);
     const data = await res.json();

     if (!data || data.error) {
       return { redirect: { destination: '/404', permanent: false } };
     }

     return { props: { data } };
   }
   ```
- **Testing**:
   - Simulated data errors by manipulating the API response to confirm that the app redirects to 404.
   - Validated correct navigation back to the homepage when accessed from the 404 page.
- **Screenshot**: Displays 404 page redirection after a simulated data retrieval error.

---

#### **3. Authentication Redirect on Protected Route**
- **Description**: Implemented SSR check for user authentication, redirecting unauthenticated users to the login page.
- **Code**:
   ```javascript
   export async function getServerSideProps(context) {
     const token = context.req.cookies.token || '';

     try {
       const user = jwt.verify(token, process.env.JWT_SECRET);
       return { props: { user } };
     } catch (error) {
       return { redirect: { destination: '/login', permanent: false } };
     }
   }
   ```
- **Testing**:
   - Accessed the protected route without a token, confirming that it redirected to the login page.
   - Added a valid token in cookies and verified successful access to the protected content.
- **Screenshot**: Shows redirect to the login page when accessing a protected route without authentication.

---

### **Resources**
- **Reference Links**:
   - [Next.js Dynamic Routing](https://nextjs.org/docs/routing/dynamic-routes)
   - [Server-Side Rendering in Next.js](https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props)
   - [Error Handling with Conditional Redirects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)

---

### **Reflection**
- **Challenges**: Implementing and testing SSR error handling and redirects required careful testing, particularly for authentication.
- **Outcome**: Gained a stronger understanding of SSR, dynamic routing, and handling secure data flows for improved user experience.
