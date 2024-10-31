# **Module 3: Beyond Front-end**
## **Week 1, Day 2: Dynamic Routing and Data Fetching in Next.js**

---

### **Submissions**

#### **Task 1: Implement Dynamic Routing in Next.js**
   - **Description**: Created a dynamic route for posts using `[id].js` under the `pages/posts/` directory, allowing dynamic URL generation and routing.
   - **Code**:
      ```javascript
      import { useRouter } from 'next/router';

      export default function Post() {
        const router = useRouter();
        const { id } = router.query;

        return (
          <div>
            <h1>Post ID: {id}</h1>
            <p>This page dynamically displays the post based on its ID.</p>
          </div>
        );
      }
      ```
   - **Screenshot**: Attached screenshot showing a sample post URL, e.g., `/posts/1`.

#### **Task 2: Static Data Fetching with `getStaticProps`**
   - **Description**: Set up static data fetching on the `Blog` page to display a list of posts.
   - **Code**:
      ```javascript
      export async function getStaticProps() {
        const posts = [
          { id: 1, title: 'Introduction to Dynamic Routing' },
          { id: 2, title: 'Getting Started with Data Fetching' }
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
   - **Screenshot**: Attached screenshot of the `Blog` page displaying the static list of posts.

#### **Task 3: Server-Side Data Fetching with `getServerSideProps`**
   - **Description**: Implemented server-side data fetching on a `Products` page.
   - **Code**:
      ```javascript
      export async function getServerSideProps() {
        const products = [
          { id: 'a', name: 'Product Alpha' },
          { id: 'b', name: 'Product Beta' }
        ];
        return { props: { products } };
      }

      export default function Products({ products }) {
        return (
          <div>
            <h1>Products</h1>
            <ul>
              {products.map(product => (
                <li key={product.id}>{product.name}</li>
              ))}
            </ul>
          </div>
        );
      }
      ```
   - **Screenshot**: Attached screenshot of the `Products` page with server-side data displayed.

#### **Task 4: Using Environment Variables in Next.js**
   - **Description**: Configured an environment variable for the API URL and used it within a page component.
   - **Instructions**:
      1. Created `.env.local` in the root with the following content:
         ```
         NEXT_PUBLIC_API_URL=https://api.example.com
         ```
      2. Created `config.js` to access the environment variable:
         ```javascript
         const apiUrl = process.env.NEXT_PUBLIC_API_URL;
         export default apiUrl;
         ```
      3. Imported `apiUrl` in `Products.js` and logged it to the console.
   - **Screenshot**: Attached screenshot showing the console log of the API URL.

#### **Task 5: Dynamic Post Page with Data Fetching**
   - **Description**: Updated the `posts/[id].js` page to use `getStaticProps` and `getStaticPaths` to pre-render specific paths.
   - **Code**:
      ```javascript
      export async function getStaticPaths() {
        const paths = [
          { params: { id: '1' } },
          { params: { id: '2' } }
        ];
        return { paths, fallback: false };
      }

      export async function getStaticProps({ params }) {
        const post = { id: params.id, title: `Post ${params.id}`, content: 'This is the content for the post.' };
        return { props: { post } };
      }

      export default function Post({ post }) {
        return (
          <div>
            <h1>{post.title}</h1>
            <p>{post.content}</p>
          </div>
        );
      }
      ```
   - **Screenshot**: Attached screenshot of a dynamically generated post page.

---

### **Resources Review**
   - **Resources Consulted**:
      - [Next.js Dynamic Routing Documentation](https://nextjs.org/docs/routing/dynamic-routes)
      - [Next.js Data Fetching Documentation](https://nextjs.org/docs/basic-features/data-fetching)
   - **Summary**:
      - **Dynamic Routing**: Learned to set up dynamic routes with `[param]` structure for creating unique pages.
      - **Data Fetching**: Understood how to use `getStaticProps` for static generation and `getServerSideProps` for server-side rendering, along with environment variables.

---

### **End-of-Day Reflection**
   - **Challenges**: Managing data fetching types and understanding use cases for `getStaticProps` vs `getServerSideProps`.
   - **Key Takeaways**: The ability to control data fetching and pre-rendering in Next.js adds powerful flexibility and efficiency to web applications.
