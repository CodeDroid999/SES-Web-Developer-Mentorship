### **Module 3: Beyond Front-end**  
#### **Week 4: Day 1 – Advanced SSR, SSG, and Rendering Performance**

---

### **Outline**  
1. **Introduction to Advanced SSR**  
2. **Server-Side Rendering (SSR) vs. Static Site Generation (SSG)**  
3. **Optimizing SSR and SSG in Next.js**  
4. **Using SSR with API Routes**  
5. **Performance Metrics for SSR and SSG**  
6. **Activity: Optimizing a Next.js SSR Page**  

---

### **Course Content**

#### **1. Introduction to Advanced SSR**  
- **What is Advanced SSR?**  
  Server-Side Rendering (SSR) in its basic form is the process where the web page is generated on the server for each request. However, when scaling applications, this approach can lead to performance bottlenecks. Advanced SSR techniques address these concerns, aiming to enhance performance, reduce server load, and improve the overall user experience.
  
  Advanced techniques in SSR often involve:
  - **Caching**: Storing pre-rendered pages to minimize server load.
  - **Code-Splitting**: Breaking the app into smaller chunks to send only necessary code to the browser.
  - **Edge Rendering**: Moving SSR to the edge, using CDNs (Content Delivery Networks) to distribute rendering closer to the user.

---

#### **2. SSR vs. SSG**  
- **What’s the Difference?**  
  - **SSR (Server-Side Rendering)**: Pages are generated on the server per request. Suitable for dynamic content that changes frequently, such as user profiles, news articles, or data dashboards.
  - **SSG (Static Site Generation)**: Pages are pre-rendered at build time, meaning they are static. Best used for content that doesn’t change often, such as blogs, documentation, or landing pages.
  
  **When to Use Each Approach?**  
  - Use SSR for content that is dynamic and requires real-time fetching from APIs or databases.
  - Use SSG for content that can be generated once during the build and doesn’t need to change with every request.

---

#### **3. Optimizing SSR and SSG in Next.js**  
- **Optimizing SSR in Next.js:**  
  To optimize SSR in Next.js, we need to focus on reducing server load, improving data fetching efficiency, and reducing latency.
  - **Caching Data**: Cache API responses to reduce load times.
  - **Incremental Static Regeneration (ISR)**: With ISR, pages can be re-rendered on the server at a specified interval rather than on every request.
  - **Use of Suspense and Concurrent Mode**: These features can help with SSR performance by splitting the rendering of large components and keeping the UI responsive.

  - **Example with ISR:**
    ```javascript
    export async function getStaticProps() {
      const res = await fetch('https://api.example.com/posts');
      const posts = await res.json();

      return {
        props: { posts },
        revalidate: 60,  // Re-generate page every 60 seconds
      };
    }
    ```

- **Optimizing SSG in Next.js:**
  - **Pre-build and Static Export**: If your site doesn’t need real-time data, exporting it as a static HTML can drastically improve performance.
  - **Fallback Pages**: Use `getStaticPaths` and `fallback: 'blocking'` to ensure pages are built ahead of time, while still serving fresh content.

---

#### **4. Using SSR with API Routes**  
- **Combining SSR with API Routes**:  
  Next.js allows us to use API routes to fetch dynamic data for SSR pages. This enables fetching data from external APIs or databases before rendering the page.  
  - **Creating API Routes in Next.js**:  
    Example of an API route:
    ```javascript
    // pages/api/products.js
    export default async (req, res) => {
      const response = await fetch('https://api.example.com/products');
      const products = await response.json();
      res.status(200).json(products);
    };
    ```
  - **Fetching Data in SSR**:
    ```javascript
    // pages/products.js
    import { useEffect } from 'react';

    export async function getServerSideProps() {
      const res = await fetch('http://localhost:3000/api/products');
      const products = await res.json();

      return { props: { products } };
    }

    const Products = ({ products }) => {
      return (
        <div>
          {products.map(product => (
            <div key={product.id}>{product.name}</div>
          ))}
        </div>
      );
    };
    
    export default Products;
    ```

---

#### **5. Performance Metrics for SSR and SSG**  
- **Why Performance Metrics Matter**:  
  Whether using SSR or SSG, it’s essential to measure how well your pages load to ensure they meet performance standards. Tools like **Lighthouse** and **Web Vitals** help track performance.  
  - **Time to First Byte (TTFB)**: Measures the time it takes for the server to respond with the first byte of data.
  - **Largest Contentful Paint (LCP)**: Measures the loading performance of the largest content element on the page.
  - **First Contentful Paint (FCP)**: Measures how quickly the browser renders the first visible content.
  - **First Input Delay (FID)**: Measures the time it takes for the page to respond to the first user input.
  - **Cumulative Layout Shift (CLS)**: Measures the visual stability of the page as it loads.

  **Use Lighthouse for Performance Audits**:
  You can run Lighthouse audits within Chrome DevTools or via the command line to get performance insights and recommendations on how to improve your SSR and SSG setup.

---

#### **6. Activity: Optimizing a Next.js SSR Page**  
- **Task:**  
  - Build a simple blog application using **SSR** in Next.js.  
  - Implement caching and test it with the **Next.js caching API**.
  - Create an API route to fetch blog data and render it on the server side.
  - Use **Lighthouse** to analyze the performance of the SSR page and make optimizations such as reducing TTFB or improving LCP.

  **Steps:**
  1. Create a `pages/posts.js` file.
  2. Implement `getServerSideProps` to fetch blog posts from an external API.
  3. Test the performance of the page using **Lighthouse** and improve the metrics by implementing SSR optimizations.

---

### **Resources**  
- [Next.js Documentation on SSR](https://nextjs.org/docs/basic-features/pages#server-side-rendering)  
- [Lighthouse Performance Audits](https://developers.google.com/web/tools/lighthouse)  
- [Web Vitals Documentation](https://web.dev/vitals/)  
- [Next.js API Routes](https://nextjs.org/docs/api-routes/introduction)

---
