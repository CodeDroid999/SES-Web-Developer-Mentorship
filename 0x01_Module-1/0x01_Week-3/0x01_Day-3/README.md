
```markdown
# Week 3, Day 3: Interactive HTML and CSS Tasks

## Introduction

Welcome to **Week 3, Day 3**! Today, we will focus on making your web projects interactive using **HTML** and **CSS**. This session is designed to help you understand how to create engaging user experiences through interactive elements.

### Objectives

By the end of this session, you will:

- Understand how to implement interactive HTML elements.
- Learn the basics of CSS animations and transitions.
- Create a mini-project with interactive components.

## Key Topics

### 1. Interactive HTML Elements

- **Forms**: Learn to create user-friendly forms with various input types.
- **Buttons**: Use buttons effectively to trigger actions.
- **Links**: Enhance navigation with styled links.

### 2. Introduction to CSS Animations and Transitions

- **CSS Transitions**: Smoothly change property values over a specified duration.
- **CSS Animations**: Create keyframe animations to animate HTML elements.

### 3. Hands-On Exercise: Create an Interactive Web Page

#### Task 1: Create a Simple Form

1. **Create a new HTML file** named `interactive-form.html`.
2. **Set up a basic form** with fields for name, email, and a submit button.
3. **Style the form** using CSS to make it visually appealing.

#### Task 2: Add Interactive Buttons

1. **Add a button** that displays an alert when clicked.
2. **Create another button** that changes the background color of the page using JavaScript.

#### Task 3: Implement CSS Transitions

1. **Add a div** element and apply CSS styles to it.
2. **Make the div change size and color** when hovered over using CSS transitions.

### Example Code Snippet

Here’s a sample to get you started:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Web Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .interactive-div {
            width: 200px;
            height: 100px;
            background-color: lightblue;
            transition: all 0.3s ease;
        }
        .interactive-div:hover {
            width: 300px;
            background-color: coral;
        }
    </style>
</head>
<body>
    <h1>Interactive HTML and CSS Tasks</h1>

    <form id="userForm">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
        <button type="submit">Submit</button>
    </form>

    <button onclick="showAlert()">Click Me!</button>
    
    <div class="interactive-div"></div>

    <script>
        function showAlert() {
            alert('Button was clicked!');
        }
    </script>
</body>
</html>
```

### 4. Review and Q&A

After completing your exercises, we will have a review session. You can share your interactive projects and ask any questions related to HTML, CSS, or JavaScript.

## Resources

Here are some helpful resources to reinforce today’s learning:

- **HTML Forms Documentation**:
  - [MDN Web Docs - Forms](https://developer.mozilla.org/en-US/docs/Learn/Forms)
  
- **CSS Transitions**:
  - [CSS Tricks - CSS Transitions](https://css-tricks.com/almanac/properties/t/transition/)
  
- **JavaScript Basics**:
  - [W3Schools - JavaScript Tutorial](https://www.w3schools.com/js/)

## Conclusion

Great job on exploring interactivity in web development! Understanding how to create engaging user experiences will significantly enhance your web projects. Keep practicing these concepts, and don't hesitate to experiment with more interactive elements!
```
