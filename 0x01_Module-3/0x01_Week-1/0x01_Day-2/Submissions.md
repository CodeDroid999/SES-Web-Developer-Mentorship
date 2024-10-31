# **Module 3: Beyond Front-end**
## **Week 1, Day 2: Dynamic Routing and Data Fetching in Next.js**

---

### **Submissions**

#### **Task 1: Implement Dynamic Routing in Next.js**
   - **Description**: Create a dynamic route page under `pages/posts/[id].js` to display blog posts based on dynamic IDs.
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
   - **Screenshot**: Attach a screenshot of a sample post URL like `/posts/1`.

#### **Task 2: Static Data Fetching with `getStaticProps`**
   - **Description**: Fetch a list of blog posts on the `Blog` page statically.
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
   - **Screenshot**: Attach a screenshot of the `Blog` page displaying the posts.

#### **Task 3: Server-Side Data Fetching with `getServerSideProps`**
   - **Description**: Create a `Products` page that fetches product data server-side.
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
   - **Screenshot**: Attach a screenshot of the `Products` page with products listed.

#### **Task 4: Using Environment Variables in Next.js**
   - **Description**: Set up an environment variable and use it in the project.
   - **Instructions**:
      1. Create a `.env.local` file in the root directory with the following content:
         ```
         NEXT_PUBLIC_API_URL=https://api.example.com
         ```
      2. Create a `config.js` file to access the environment variable:
         ```javascript
         const apiUrl = process.env.NEXT_PUBLIC_API_URL;
         export default apiUrl;
         ```
      3. Import `apiUrl` in `Products.js` and log it to the console.
   - **Screenshot**: Attach a screenshot showing the console log of the API URL.

#### **Task 5: Dynamic Post Page with Data Fetching**
   - **Description**: Update the `posts/[id].js` page to use `getStaticProps` and `getStaticPaths` for pre-rendering based on paths.
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
   - **Screenshot**: Attach a screenshot of the dynamically generated post page.

#### **Resources Review**
   - **Resources**:
      - [Dynamic Routing in Next.js Documentation](https://nextjs.org/docs/routing/dynamic-routes)
      - [Data Fetching in Next.js Documentation](https://nextjs.org/docs/basic-features/data-fetching)
   - **Summary**: Provide a brief summary of what you learned from the resources.

---

### **End-of-Day Reflection**
   - **Questions**:
      - **What concepts were challenging today?**
      - **Topics to explore further?**
      - **Key takeaways from today’s tasks.**

