
---



```markdown
# Day 4: Server-Side Rendering, Apollo, and GraphQL Fundamentals

---

## Outline
1. **Server-Side Rendering (SSR) in Next.js**
2. **Introduction to GraphQL**
3. **Setting Up Apollo Client with Next.js**
4. **Writing Queries and Mutations in GraphQL**
5. **Integrating Apollo and GraphQL with SSR**

---

## 1. Server-Side Rendering (SSR) in Next.js

### Overview
Server-side rendering (SSR) allows pages to be pre-rendered on the server and delivered as fully populated HTML to the client.  
**Benefits of SSR**:
- Enhanced SEO for search engines.
- Faster perceived performance for end users.

### Key API: `getServerSideProps`
`getServerSideProps` is a Next.js API used to fetch data server-side before rendering.

### Example:
```javascript
export async function getServerSideProps() {
  const res = await fetch('https://api.example.com/data');
  const data = await res.json();

  return { props: { data } };
}
```

---

## 2. Introduction to GraphQL

### What is GraphQL?
GraphQL is a query language for APIs and a runtime for fulfilling those queries using a type system.  
- **Queries**: Fetch data.
- **Mutations**: Update data.
- **Schema/Types**: Define structure.

### Example Query:
```graphql
query {
  user(id: "1") {
    name
    email
  }
}
```

### Key Benefits:
- **Reduced Over-fetching**: Request only the data needed.
- **Single Endpoint**: A `/graphql` endpoint replaces multiple REST endpoints.

---

## 3. Setting Up Apollo Client in Next.js

### Steps:
1. Install Apollo Client:
   ```bash
   npm install @apollo/client graphql
   ```
2. Configure Apollo Client:
   ```javascript
   import { ApolloClient, InMemoryCache } from '@apollo/client';

   const client = new ApolloClient({
     uri: 'https://api.example.com/graphql',
     cache: new InMemoryCache(),
   });

   export default client;
   ```

3. Wrap the app with `ApolloProvider`:
   ```javascript
   import { ApolloProvider } from '@apollo/client';
   import client from './lib/apolloClient';

   function MyApp({ Component, pageProps }) {
     return (
       <ApolloProvider client={client}>
         <Component {...pageProps} />
       </ApolloProvider>
     );
   }

   export default MyApp;
   ```

---

## 4. Writing Queries and Mutations in GraphQL

### Queries
GraphQL queries are used to fetch data from a server.

#### Example Query:
```graphql
query GetUser {
  user(id: "1") {
    name
    email
  }
}
```

### Mutations
GraphQL mutations are used to modify or create new data.

#### Example Mutation:
```graphql
mutation UpdateUser($id: ID!, $name: String!) {
  updateUser(id: $id, name: $name) {
    id
    name
  }
}
```

---

## 5. Integrating Apollo with SSR

Use Apollo and `getServerSideProps` to fetch data server-side.

### Example:
```javascript
import { gql } from '@apollo/client';
import client from '../lib/apolloClient';

export async function getServerSideProps() {
  const { data } = await client.query({
    query: gql`
      query GetProducts {
        products {
          id
          name
          price
        }
      }
    `,
  });

  return { props: { products: data.products } };
}

export default function ProductsPage({ products }) {
  return (
    <div>
      <h1>Products</h1>
      <ul>
        {products.map((product) => (
          <li key={product.id}>{product.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

---

## Resources
- [Apollo Client Documentation](https://www.apollographql.com/docs/react/)
- [GraphQL Basics](https://graphql.org/learn/)
- [Next.js `getServerSideProps`](https://nextjs.org/docs/basic-features/data-fetching#getserversideprops)
```

---

### **2. tasks.md**

```markdown
# Day 4 Tasks: Server-Side Rendering, Apollo, and GraphQL

---

## Task 1: Implement SSR in Next.js
1. Create a new Next.js page that uses `getServerSideProps`.
2. Fetch data from a public API (e.g., https://jsonplaceholder.typicode.com/posts).
3. Render the data server-side and display it on the page.

---

## Task 2: Configure Apollo Client
1. Set up Apollo Client in your project.
2. Connect to a sample GraphQL API (e.g., https://countries.trevorblades.com/).
3. Write a GraphQL query to fetch a list of countries and their codes.

---

## Task 3: Write and Test a GraphQL Mutation
1. Create a mutation to add or update data using a GraphQL API.
2. Test the mutation in an Apollo Sandbox or client app.

---

## Task 4: Integrate Apollo with SSR
1. Use Apollo Client and `getServerSideProps` to fetch GraphQL data server-side.
2. Render the data in a Next.js component.
```

---

