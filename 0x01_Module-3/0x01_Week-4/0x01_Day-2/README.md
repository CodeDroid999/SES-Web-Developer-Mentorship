### **Week 4 - Day 2: Advanced Static Site Generation (SSG) and Incremental Static Regeneration (ISR)**

---

#### **Course Content:**

### **Introduction to Static Site Generation (SSG)**
Static Site Generation (SSG) is the process of pre-rendering pages at build time. Unlike Server-Side Rendering (SSR), which generates pages on each request, SSG generates HTML at build time and serves it for each request. This results in faster loading times, as the content is already generated and cached. **Next.js** provides an excellent way to implement SSG with the `getStaticProps` method.

#### **Topics Covered:**
1. **SSG with Next.js**:
   - Understand how SSG works by generating static pages at build time.
   - Learn how to use `getStaticProps` to fetch data during build time for static pages.
   - Use the `getStaticPaths` function to generate dynamic static pages when dealing with dynamic routes (e.g., blog post pages).

2. **Incremental Static Regeneration (ISR)**:
   - Explore ISR, a Next.js feature that allows you to update static pages without needing to rebuild the entire site.
   - Learn how to use the `revalidate` property in `getStaticProps` to control the frequency of regeneration for static pages.
   - Understand how ISR works in the background while serving the old static page until the new one is generated.

3. **Benefits of SSG and ISR**:
   - Fast performance due to pre-rendering.
   - Ability to serve fresh data without full rebuilds (via ISR).
   - Optimized for SEO since pages are pre-rendered with all content available to crawlers.
   
4. **When to Use SSG vs. SSR**:
   - Understand the trade-offs between SSR and SSG and know when to use each one.
   - Use SSR for dynamic content that requires real-time updates.
   - Use SSG for content that doesn't change often and can be cached.

#### **Practical Implementation**:

##### **1. Creating Static Pages Using `getStaticProps`**:
   - Build a simple blog page that fetches posts at build time.
   - Implement the `getStaticProps` method to fetch data from an external API and pass it to the page as props.
   - Learn how to use `getStaticPaths` to handle dynamic routes, such as individual blog posts.

##### **2. Implementing ISR with `revalidate`**:
   - Modify the `getStaticProps` method to enable ISR by setting a `revalidate` property.
   - Learn how to configure the `revalidate` period to ensure that content is updated at regular intervals.
   - Test your page by modifying the content and observing the regeneration process.

##### **3. Build a Blog with ISR**:
   - Create a blog page where the list of posts is pre-rendered at build time using SSG.
   - Use ISR to regenerate individual blog post pages when new content is added or updated.

---

### **Hands-On Assignment for Day 2:**

#### **Tasks:**

1. **Create a Static Blog Page Using `getStaticProps`:**
   - Build a simple Next.js blog using `getStaticProps` to fetch blog posts from a mock API (e.g., JSONPlaceholder API).
   - Display the list of posts (title and excerpt) in a grid or list format.

2. **Implement Dynamic Routing for Blog Posts:**
   - Use `getStaticPaths` to generate static pages for individual blog posts.
   - Fetch and display the full content of each blog post on the individual post page.

3. **Enable Incremental Static Regeneration (ISR):**
   - In `getStaticProps`, enable ISR by adding the `revalidate` property with a suitable value (e.g., 60 seconds).
   - Test that changes to the data are reflected on the page after the revalidation period has passed.

4. **Deploy Your Application:**
   - Deploy your Next.js application to **Vercel** or another platform that supports Next.js.
   - Ensure that the blog pages are served as static pages with incremental regeneration for individual posts.

---
