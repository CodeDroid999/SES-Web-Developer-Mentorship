
---




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
