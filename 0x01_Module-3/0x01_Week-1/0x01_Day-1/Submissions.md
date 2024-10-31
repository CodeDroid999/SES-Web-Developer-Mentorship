# **Module 3: Beyond Front-end**
## **Week 1, Day 1: Introduction to Next.js**

---

### **Submissions**

#### **Task 1: Introduction to Next.js and Key Features**
   - **Summary**:  
      Describe in a few sentences what you learned about Next.js, including its main features and the difference between SSR, SSG, and CSR.
   - **Key Takeaways**:
      - Feature highlights of Next.js.
      - Scenarios where SSR, SSG, and CSR are applicable.
   - **Screenshot**: Attach a screenshot of notes or a summary document about Next.js features.

#### **Task 2: Setting Up a Next.js Project**
   - **Project Setup**:
      - **Command Used**:
        ```
        npx create-next-app@latest my-nextjs-app
        ```
      - **Screenshot**: Attach a screenshot of the `http://localhost:3000` page showing that the server is running.
   
#### **Task 3: Understanding the Project Structure**
   - **Folder Summary**: Write a brief summary of each folder (`pages`, `public`, `styles`).
   - **Screenshot**: Attach a screenshot of the folder structure in your code editor.

#### **Task 4: Creating Pages and Routing in Next.js**
   - **Pages Created**:
      - **About Page Code**:
        ```javascript
        export default function About() {
          return <h1>About Page</h1>;
        }
        ```
      - **Home Page Code** with `Link`:
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
   - **Screenshot**: Attach screenshots of the `Home` and `About` pages in the browser.

#### **Task 5: Introduction to Server-Side Rendering (SSR) and Static Site Generation (SSG)**
   - **Blog Page Code**:
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
   - **Screenshot**: Attach a screenshot of the `Blog` page with generated content visible in the browser.

#### **Task 6: Hands-on Practice with Page Metadata and Head Management**
   - **About Page Code with Metadata**:
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
   - **Screenshot**: Attach a screenshot of the metadata visible in the browser’s developer tools (`Elements > head`).

#### **Task 7: Explore Resources for Continued Learning**
   - **Resource Summary**:  
      Write a few lines summarizing your learnings from each of the following:
      - [Next.js Official Documentation](https://nextjs.org/docs)
      - [Learn Next.js Interactive Tutorial](https://nextjs.org/learn)

---

### **End-of-Day Reflection**
   - **What was most challenging today?**
   - **What did you enjoy the most?**
   - **Areas for further practice or improvement:**

