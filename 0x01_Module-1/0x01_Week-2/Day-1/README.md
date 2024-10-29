# Week 3, Day 1: Advanced HTML and Semantic Markup

## Introduction

Welcome to **Week 3, Day 1**! Today, we will dive deeper into **HTML** and the importance of **semantic markup**. Building on your foundational skills, this session aims to enhance your understanding of HTML elements, structures, and best practices for creating meaningful and accessible web content.

### Objectives

By the end of this session, you will:

- Understand the role and significance of **semantic HTML** in web development.
- Learn about various **HTML5 semantic elements** and their appropriate use cases.
- Gain hands-on experience in creating a well-structured HTML document.

## Key Topics

### 1. The Importance of Semantic HTML

- **Definition**: Semantic HTML uses HTML markup to reinforce the meaning of the content. Instead of using generic tags like `<div>` and `<span>`, semantic elements convey meaning about the content within them.
  
- **Benefits**:
  - **Accessibility**: Helps assistive technologies (like screen readers) better understand web content.
  - **SEO**: Search engines can better index pages, improving search rankings.
  - **Maintainability**: Easier for developers to read and understand the code.

### 2. Common Semantic HTML Elements

- **`<header>`**: Represents introductory content, typically a group of introductory or navigational aids.
- **`<nav>`**: Defines a set of navigation links.
- **`<main>`**: Represents the main content of the document, excluding headers, footers, and sidebars.
- **`<article>`**: Represents a self-contained piece of content that could be distributed and reused independently.
- **`<section>`**: Represents a thematic grouping of content, typically with a heading.
- **`<footer>`**: Contains information about the author, copyright, links to related documents, and other relevant details.
- **`<aside>`**: Represents content indirectly related to the main content, such as sidebars or pull quotes.

### 3. Writing Semantic HTML

- **Best Practices**:
  - Use semantic tags to improve accessibility and SEO.
  - Ensure that your HTML document has a clear structure (header, main, footer).
  - Avoid overusing `<div>` tags; instead, opt for semantic elements that convey meaning.

### 4. Hands-On Exercise: Creating a Semantic HTML Document

1. **Create a new HTML file** named `semantic.html`.
2. **Set up the basic structure** of an HTML document, including the `<!DOCTYPE html>` declaration and `<html>` element.
3. **Incorporate semantic elements** into your document:
   - Add a `<header>` with a site title and navigation links.
   - Use a `<main>` section for the primary content, including an `<article>` for a blog post and a `<section>` for related topics.
   - Include a `<footer>` with copyright information.

### Example Code Snippet

Here's a sample structure to help you get started:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Semantic HTML Example</title>
</head>
<body>
    <header>
        <h1>My Blog</h1>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <article>
            <h2>Understanding Semantic HTML</h2>
            <p>Semantic HTML helps improve accessibility and SEO...</p>
        </article>
        
        <section>
            <h2>Related Topics</h2>
            <p>Learn more about accessibility, SEO, and HTML best practices...</p>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 My Blog. All rights reserved.</p>
    </footer>
</body>
</html>
