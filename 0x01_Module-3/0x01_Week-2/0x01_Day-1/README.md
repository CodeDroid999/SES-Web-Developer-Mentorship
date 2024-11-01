# **Module 3: Beyond Front-end**
## **Week 2, Day 1: Advanced Server-Side Rendering (SSR) and Dynamic Routing**

---

### **Course Content**

#### **1. Introduction to Advanced SSR Techniques**
   - **Objective**: Deep dive into advanced server-side rendering techniques in Next.js, focusing on dynamic and nested routing, API integration, and efficient data fetching.
   - **Topics**:
     - SSR with parameterized routing
     - Integrating external data into SSR routes
     - Error handling in SSR
     - Conditional redirects based on fetched data

#### **2. Dynamic Routing in Next.js**
   - **Objective**: Create dynamic routes in Next.js and fetch corresponding data on the server side.
   - **Explanation**:
     - Dynamic routes in Next.js allow rendering pages based on parameters (e.g., `/product/[id]`).
     - SSR with dynamic routes ensures data is pre-fetched on the server, improving performance and SEO.
   - **Example**:
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
   - **Test**: Verified that accessing `/product/[id]` dynamically displays product data.

#### **3. Conditional Redirects and Error Handling**
   - **Objective**: Implement conditional redirects in SSR based on fetched data status, ensuring a seamless user experience.
   - **Explanation**:
     - Using conditional redirects based on the data status or user authentication.
     - Error handling and redirecting unauthenticated users to login.
   - **Example**:
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
   - **Test**: Confirmed redirect to the 404 page when data is missing or error occurs.

---

### **Submissions**

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
- **Test**: Accessed multiple `/product/[id]` URLs, each returning the correct product details.
- **Screenshot**: Shows a product page with data fetched from the server.

#### **2. Error Handling with Conditional Redirects**
- **Description**: Added conditional redirects based on data retrieval errors.
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
- **Test**: Simulated data retrieval errors to confirm redirect to the 404 page.
- **Screenshot**: Shows 404 page for invalid data requests.

#### **3. Authentication Redirect on Protected Route**
- **Description**: Implemented server-side check for authentication; redirects unauthenticated users to login.
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
- **Screenshot**: Displays login redirect when accessing a protected route without authentication.

---

### **Resources**
- **Consulted**:
   - [Next.js Dynamic Routing](https://nextjs.org/docs/routing/dynamic-routes)
   - [Server-side Data Fetching with Next.js](https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props)
   - [Error Handling in API Requests](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)

---

### **Reflection**
- **Challenges**: Ensuring redirects work seamlessly with SSR required experimenting with error handling and token management.
- **Outcome**: Solidified understanding of dynamic routes, server-side data handling, and SSR best practices.

