

# Day 1: Introduction to Static Site Generators (SSGs)

---

## Outline

1. **What Are Static Site Generators (SSGs)?**
2. **Key Benefits of SSGs**
3. **Popular SSG Tools**
4. **Working With Next.js as an SSG**
5. **Building a Blog Using Next.js**
6. **Deploying Static Sites**

---

## 1. What Are Static Site Generators (SSGs)?

### Definition
Static Site Generators are tools that generate pre-rendered HTML files from templates or components, eliminating the need for server-side rendering on every request.

### How They Work:
1. During the build process, SSGs fetch data and generate static HTML pages.
2. These pages are then served directly to users.

---

## 2. Key Benefits of SSGs

1. **Performance**: Pre-rendered pages load faster.
2. **Security**: No database or server-side code means reduced attack surfaces.
3. **Scalability**: Serve the same static assets across multiple requests.
4. **SEO-Friendly**: Fully rendered HTML is optimal for search engines.

---

## 3. Popular SSG Tools

- **Next.js**: A React-based framework for server-side rendering and static generation.
- **Gatsby**: Focuses on speed and SEO, ideal for data-driven sites.
- **Hugo**: Written in Go, it's one of the fastest SSGs.
- **Jekyll**: A Ruby-based SSG commonly used with GitHub Pages.

---

## 4. Working With Next.js as an SSG

### Why Use Next.js?
Next.js allows developers to create both server-rendered and statically generated websites with ease.

### Static Generation in Next.js:
- Use `getStaticProps()` to fetch data at build time.
- Use `getStaticPaths()` to generate dynamic routes.

### Example:
```javascript
import fs from 'fs';
import path from 'path';

export async function getStaticProps() {
  const postsDirectory = path.join(process.cwd(), 'posts');
  const filenames = fs.readdirSync(postsDirectory);

  const posts = filenames.map((filename) => {
    const filePath = path.join(postsDirectory, filename);
    const fileContents = fs.readFileSync(filePath, 'utf8');
    return { filename, content: fileContents };
  });

  return {
    props: {
      posts,
    },
  };
}

export default function Blog({ posts }) {
  return (
    <div>
      <h1>My Blog</h1>
      {posts.map((post) => (
        <article key={post.filename}>
          <h2>{post.filename}</h2>
          <p>{post.content}</p>
        </article>
      ))}
    </div>
  );
}
```

---

## 5. Building a Blog Using Next.js

1. **Set Up the Project**:
   - Initialize a Next.js app.
   - Create a `pages` directory for static pages.
   - Use Markdown files or an API to store blog data.

2. **Generate Static Pages**:
   - Use `getStaticProps()` for blog data fetching.
   - Use `getStaticPaths()` for dynamic blog routes.

---

## 6. Deploying Static Sites

### Platforms for Deployment:
1. **Vercel**: The official hosting platform for Next.js.
2. **Netlify**: A powerful platform for static sites and serverless functions.
3. **GitHub Pages**: Free hosting for static sites.

### Steps to Deploy on Vercel:
1. Install the Vercel CLI:
   ```bash
   npm install -g vercel
   ```
2. Deploy your app:
   ```bash
   vercel
   ```

---

## Resources
- [Next.js Documentation](https://nextjs.org/docs)
- [Vercel Deployment Guide](https://vercel.com/docs/concepts/deployments)
- [Understanding Static Site Generators](https://www.smashingmagazine.com/2020/02/introduction-static-site-generators/)
```

---
