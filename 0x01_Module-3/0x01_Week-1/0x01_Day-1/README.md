### Module 3: Beyond Front-end
### Week 1, Day 1: Introduction to Next.js

---

#### **Goal**: 
To familiarize learners with Next.js, a powerful React framework used to build scalable, server-rendered applications. Learners will set up their first Next.js project, understand the core features, and create a basic page with routing and navigation.

---

### **Tasks**

#### **1. Introduction to Next.js and Key Features**
   - **Explanation**: Next.js is a React-based framework that provides key functionalities like Server-Side Rendering (SSR), Static Site Generation (SSG), and API routes. These features make it easy to build fast, SEO-friendly applications.
   - **Activities**:
      - Read the [Next.js Overview](https://nextjs.org/docs#what-is-nextjs) and take notes on the unique features.
      - Discuss the advantages of SSR, SSG, and Client-Side Rendering (CSR).
      - Identify when to use each rendering method and their impact on performance and SEO.

#### **2. Setting Up a Next.js Project**
   - **Explanation**: This step involves setting up the Next.js development environment and starting the project.
   - **Activities**:
      - Install Node.js if not already installed.
      - Open the terminal and create a new Next.js project by running:  
        ```bash
        npx create-next-app@latest my-nextjs-app
        ```
      - Start the development server by running:
        ```bash
        cd my-nextjs-app
        npm run dev
        ```
      - Open `http://localhost:3000` in a browser to see the project running.
   - **Outcome**: A basic Next.js project is set up and running locally.

#### **3. Understanding the Project Structure**
   - **Explanation**: Next.js projects follow a specific structure that includes folders like `pages`, `public`, and `styles`. Understanding the layout helps in organizing code effectively.
   - **Activities**:
      - Open the `my-nextjs-app` folder and explore its structure:
         - **`pages/`**: Holds files that represent each route in the application.
         - **`public/`**: Stores static assets.
         - **`styles/`**: Contains CSS files.
      - In the `pages` folder, open `index.js`, the default home page, and inspect the code.
   - **Outcome**: Learners understand where to place different parts of their code.

#### **4. Creating Pages and Routing in Next.js**
   - **Explanation**: In Next.js, each file in the `pages` folder represents a route. This built-in routing system simplifies navigation.
   - **Activities**:
      - Create a new file in `pages` named `about.js` and add the following code:
        ```javascript
        export default function About() {
          return <h1>About Page</h1>;
        }
        ```
      - Visit `http://localhost:3000/about` in the browser to view the new page.
      - Go back to `pages/index.js` and add a link to the About page using Next.js’s `Link` component:
        ```javascript
        import Link from 'next/link';

        export default function Home() {
          return (
            <div>
              <h1>Home Page</h1>
              <Link href="/about">Go to About Page</Link>
            </div>
          );
        }
        ```
      - Test the link to ensure navigation between pages.
   - **Outcome**: Learners create multiple pages and set up basic routing.

#### **5. Introduction to Server-Side Rendering (SSR) and Static Site Generation (SSG)**
   - **Explanation**: SSR and SSG are two key features in Next.js for pre-rendering pages. SSR renders the page on each request, while SSG generates HTML at build time.
   - **Activities**:
      - Learn the differences between SSR and SSG and their use cases.
      - Experiment by setting up a page using SSG:
         - Create a new file `blog.js` under `pages`:
           ```javascript
           export async function getStaticProps() {
             const posts = [
               { id: 1, title: 'First Post' },
               { id: 2, title: 'Second Post' }
             ];
             return { props: { posts } };
           }

           export default function Blog({ posts }) {
             return (
               <div>
                 <h1>Blog Posts</h1>
                 <ul>
                   {posts.map(post => (
                     <li key={post.id}>{post.title}</li>
                   ))}
                 </ul>
               </div>
             );
           }
           ```
      - Visit `http://localhost:3000/blog` to see the page with blog posts generated at build time.
   - **Outcome**: Learners understand SSR and SSG and can implement a basic SSG page.

#### **6. Hands-on Practice with Page Metadata and Head Management**
   - **Explanation**: Managing metadata (such as title and description) is essential for SEO. Next.js provides the `Head` component for adding metadata.
   - **Activities**:
      - In the `about.js` page, add metadata using the `Head` component:
        ```javascript
        import Head from 'next/head';

        export default function About() {
          return (
            <div>
              <Head>
                <title>About Page</title>
                <meta name="description" content="Learn more about us on this page." />
              </Head>
              <h1>About Page</h1>
            </div>
          );
        }
        ```
      - Verify that the metadata appears in the browser’s developer tools under `Elements > head`.
   - **Outcome**: Learners can add page-specific metadata for SEO and accessibility.

#### **7. Explore Resources for Continued Learning**
   - **Activities**:
      - Go through the following recommended resources to solidify today’s learning:
         - [Next.js Official Documentation](https://nextjs.org/docs)
         - [Learn Next.js Interactive Tutorial](https://nextjs.org/learn)
   - **Outcome**: Learners have resources to continue learning Next.js at their own pace.

---

### **Day Summary**:
By the end of Day 1, learners will have a functional understanding of the Next.js framework, including project setup, folder structure, basic routing, page creation, and an introduction to SSR and SSG. They’ll be able to add metadata for SEO purposes and have hands-on experience building a simple multi-page application in Next.js. 

