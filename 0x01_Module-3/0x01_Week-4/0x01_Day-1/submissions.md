
## **Submissions: Week 4, Day 1 – Advanced SSR, SSG, and Rendering Performance**

### **Task Overview**
In this assignment, you will be optimizing a Next.js SSR page. You will implement SSR with API routes, apply performance optimizations, and analyze the performance using Lighthouse. Finally, you'll improve your SSR page by addressing the identified performance bottlenecks.

### **Submission Tasks:**
1. **Create a Next.js SSR Blog Page:**
   - Build a page in Next.js that fetches blog data from an external API using SSR (Server-Side Rendering).
   - Use the `getServerSideProps` method to fetch data and render it on the server before sending the page to the browser.
   - Display a list of blog posts with titles and descriptions.

2. **Implement API Routes:**
   - Create an API route to fetch the blog data. The API route should be located in `pages/api/posts.js`.
   - This API route should fetch data from a mock blog API (you can use a service like [JSONPlaceholder](https://jsonplaceholder.typicode.com/) or any other API).

3. **Performance Optimizations:**
   - Apply performance optimizations, such as caching the blog data, using **Incremental Static Regeneration (ISR)** or **Edge Rendering** (if applicable).
   - Implement **code splitting** to optimize the loading performance of the page.
   - Use **Suspense** and **Concurrent Mode** (if relevant) to handle large components efficiently.

4. **Use Lighthouse to Measure Performance:**
   - Run a performance audit on your SSR page using **Lighthouse**.
   - Focus on **Time to First Byte (TTFB)**, **Largest Contentful Paint (LCP)**, and **Cumulative Layout Shift (CLS)** as key performance metrics.
   - After analyzing the audit, make performance improvements based on the Lighthouse recommendations.

5. **Document the Following:**
   - Describe the steps you followed to build and optimize the SSR page.
   - Include the URL of the live application or a GitHub repository link for your code.
   - Provide a summary of your **Lighthouse** performance results and any improvements you made.

---

### **Submission Guidelines:**

- **Code Submission**: Please submit your project repository link (GitHub, GitLab, etc.).
- **URL**: If your project is deployed, provide the live link.
- **Performance Audit**: Share a screenshot or PDF of the **Lighthouse performance report** showing the key metrics such as **TTFB**, **LCP**, and **CLS**.
- **Description**: In your submission message, provide a summary of the optimizations you implemented, any challenges faced, and how you improved the page's performance.

---

### **Evaluation Criteria:**
1. **Correct Implementation of SSR**: Ensuring the page fetches data and renders it on the server using `getServerSideProps`.
2. **Effective Use of API Routes**: Implementing and using API routes correctly in Next.js.
3. **Performance Optimizations**: Implementing performance best practices such as caching, code-splitting, and using ISR.
4. **Lighthouse Performance Improvements**: Analyzing and improving page performance based on Lighthouse reports.
5. **Documentation and Explanation**: Clear explanation of the steps taken and performance improvements.

---

### **Resources to Help You**:
- [Next.js SSR Documentation](https://nextjs.org/docs/basic-features/pages#server-side-rendering)
- [Lighthouse Performance Audits](https://developers.google.com/web/tools/lighthouse)
- [JSONPlaceholder API](https://jsonplaceholder.typicode.com/)
- [Next.js API Routes Documentation](https://nextjs.org/docs/api-routes/introduction)

---
