# **Module 3: Beyond Front-end**
## **Week 1, Day 2: Dynamic Routing and Data Fetching in Next.js**

---

### **Submissions**

#### **Task 1: Implement Dynamic Routing in Next.js**
   - **Dynamic Route Page**:
      - Create a dynamic route page under `pages/posts/[id].js` to handle different blog post URLs based on an `id`.
   - **Code for Dynamic Route**:
      ```javascript
      import { useRouter } from 'next/router';

      export default function Post() {
        const router = useRouter();
        const { id } = router.query;

        return (
          <div>
            <h1>Post ID: {id}</h1>
            <p>This page is dynamically generated based on the post ID in the URL.</p>
          </div>
        );
      }
      ```
   - **Screenshot**: Attach a screenshot of the page for a sample post ID like `/posts/1` in the browser.

#### **Task 2: Fetching Data in Next.js using `getStaticProps`**
   - **Creating a Static Blog List**:
      - Fetch a list of posts statically on the `Blog` page and display them.
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
   - **Screenshot**: Attach a screenshot of the `Blog` page with static posts listed in the browser.

#### **Task 3: Fetching Data in Next.js using `getServerSideProps`**
   - **Server-Side Rendering for a Product List**:
      - Use `getServerSideProps` to fetch data for a `Products` page, simulating an API fetch.
   - **Products Page Code**:
      ```javascript
      export async function getServerSideProps() {
        const products = [
          { id: 'a', name: 'Product A' },
          { id: 'b', name: 'Product B' }
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
   - **Screenshot**: Attach a screenshot of the `Products` page with products listed in the browser.

#### **Task 4: Using Environment Variables in Next.js**
   - **Creating Environment Variables**:
      - Create a `.env.local` file in the root of your project and add a variable:
        ```
        NEXT_PUBLIC_API_URL=https://api.example.com
        ```
      - Access this variable in a `config.js` file.
   - **config.js Code**:
      ```javascript
      const apiUrl = process.env.NEXT_PUBLIC_API_URL;

      export default apiUrl;
      ```
   - **Environment Variable Usage**:
      - Import `apiUrl` into the `Products` page and log it in the console.
      ```javascript
      import apiUrl from '../config';

      console.log("API URL:", apiUrl);
      ```
   - **Screenshot**: Attach a screenshot of the console log showing the API URL.

#### **Task 5: Hands-On Practice with Dynamic Routes and Data Fetching**
   - **Dynamic Post Page with Data**:
      - Update the `posts/[id].js` page to fetch the post data using `getStaticProps` and `getStaticPaths`.
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
        const post = { id: params.id, title: `Post ${params.id}`, content: 'This is the post content.' };
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

#### **Task 6: Review Resources**
   - **Resource Summary**:
      Write a summary of what you learned from these resources:
      - [Dynamic Routing in Next.js Documentation](https://nextjs.org/docs/routing/dynamic-routes)
      - [Data Fetching in Next.js Documentation](https://nextjs.org/docs/basic-features/data-fetching)

---

### **End-of-Day Reflection**
   - **What concepts did you find most challenging?**
   - **What topics are you interested in exploring further?**
   - **Key takeaways from today’s tasks.**

