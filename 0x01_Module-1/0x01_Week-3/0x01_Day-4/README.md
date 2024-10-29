# Week 3, Day 4: Advanced Interactivity with JavaScript

## Introduction

Welcome to **Week 3, Day 4**! Today, we will dive deeper into making your web pages more interactive by utilizing **JavaScript**. You will learn how to create dynamic content that responds to user actions and enhances the overall user experience.

### Objectives

By the end of this session, you will:

- Understand the fundamentals of JavaScript and its role in web interactivity.
- Learn to manipulate the DOM (Document Object Model) to change web content dynamically.
- Create an interactive mini-project that utilizes advanced JavaScript concepts.

## Key Topics

### 1. Introduction to JavaScript

- **What is JavaScript?**: A scripting language that enables you to create dynamic content on web pages.
- **How JavaScript Works**: Understanding how scripts run in the browser and interact with HTML/CSS.

### 2. DOM Manipulation

- **What is the DOM?**: A representation of the structure of a document that can be manipulated with JavaScript.
- **Common DOM Manipulation Methods**:
  - `getElementById()`, `querySelector()`, `createElement()`, `appendChild()`, `innerHTML`, etc.

### 3. Event Handling

- **What are Events?**: Actions that occur in the browser, such as clicks, key presses, or mouse movements.
- **Adding Event Listeners**: How to listen for events and respond accordingly.

### 4. Hands-On Exercise: Create an Interactive Web App

#### Task 1: Build a To-Do List Application

1. **Create a new HTML file** named `todo-list.html`.
2. **Set up the basic structure** for a to-do list, including an input field, a button to add tasks, and a list to display tasks.
3. **Use JavaScript to handle task addition**: When the button is clicked, the task from the input field should be added to the list.

#### Task 2: Add Task Removal Functionality

1. **Implement a way to remove tasks**: Each task in the list should have a delete button next to it. When clicked, the task should be removed from the list.

### Example Code Snippet

Here’s a sample structure to help you get started:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        li {
            margin: 5px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        button {
            background-color: red;
            color: white;
            border: none;
            padding: 5px 10px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>To-Do List</h1>
    <input type="text" id="taskInput" placeholder="Add a new task...">
    <button id="addTaskButton">Add Task</button>
    
    <ul id="taskList"></ul>

    <script>
        const addTaskButton = document.getElementById('addTaskButton');
        const taskInput = document.getElementById('taskInput');
        const taskList = document.getElementById('taskList');

        addTaskButton.addEventListener('click', function() {
            const taskText = taskInput.value;
            if (taskText) {
                const listItem = document.createElement('li');
                listItem.textContent = taskText;

                const deleteButton = document.createElement('button');
                deleteButton.textContent = 'Delete';
                deleteButton.onclick = function() {
                    taskList.removeChild(listItem);
                };

                listItem.appendChild(deleteButton);
                taskList.appendChild(listItem);
                taskInput.value = ''; // Clear the input field
            }
        });
    </script>
</body>
</html>
```

### 5. Review and Q&A

After completing your tasks, we will hold a review session where you can share your to-do list applications and ask any questions regarding JavaScript or DOM manipulation.

## Resources

Here are some helpful resources to reinforce today’s learning:

- **JavaScript Fundamentals**:
  - [MDN Web Docs - JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
  
- **DOM Manipulation**:
  - [MDN Web Docs - Working with Objects](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
  
- **Event Handling**:
  - [MDN Web Docs - Introduction to Events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)

## Conclusion

Congratulations on taking another step toward mastering interactivity in web development! Understanding how to use JavaScript for DOM manipulation will allow you to create dynamic, user-friendly applications. Keep experimenting with these concepts, and don't hesitate to push your creativity!
