# Tasks

### Task 1: Applying Internal CSS

**Folder Structure:** `internal-css/`

In this task, you will apply internal CSS to your web page. Follow these steps:

1. Download the [index.html](https://github.com/CodeDroid999/SES-Web-Developer-Mentorship/blob/main/0x01_Module-1/0x01_Week-1/0x01_Day-3/index.html) file provided in this repository.

2. Create a new GitHub repository named "WebMentorship-Day3-InternalCSS."

3. Clone the new repository to your local machine using Git.

4. Inside the local repository directory, create three new folders: `folder-internal`, `folder-external`, and `folder-inline`.

5. Copy the downloaded `index.html` file and paste it into all three folders (`folder-internal`, `folder-external`, and `folder-inline`).

6. In the `index.html` file inside the `folder-internal`, apply internal CSS to style specific elements on your page. For example, you can change the font color, background color, or text size of your headings and paragraphs.

   ```html
   <style>
     h1, h2, p {
       color: #333333;
     }

     .section-background {
       background-color: #f0f0f0;
     }

     .cat-description {
       font-size: 16px;
       text-align: left;
     }
   </style>
   ```

7. Commit your changes with a meaningful message and push them to your GitHub repository.

### Task 2: Applying External CSS

**Folder Structure:** `external-css/`

In this task, you will apply external CSS to your web page. Follow these steps:

1. Create a new GitHub repository named "WebMentorship-Day3-ExternalCSS."

2. Clone the new repository to your local machine using Git.

3. Inside the local repository directory, create three new folders: `folder-internal`, `folder-external`, and `folder-inline`.

4. Copy the downloaded `index.html` file and paste it into all three folders (`folder-internal`, `folder-external`, and `folder-inline`).

5. In the `index.html` file inside the `folder-external`, create a new CSS file named `styles.css`. Define CSS rules to style your web page elements. You can target elements by their HTML tags, classes, or IDs.

   ```html
   <!-- Add this to index.html inside folder-external -->
   <link rel="stylesheet" href="styles.css">
   ```

   ```css
   /* styles.css */
   h1, h2, p {
     font-family: Arial, sans-serif;
     font-size: 24px;
     color: #333333;
   }

   a {
     color: #007acc;
   }

   .section-margin {
     margin: 20px;
   }

   .section-padding {
     padding: 10px;
   }
   ```

6. Commit your changes with a meaningful message and push them to your GitHub repository.

### Task 3: Applying In-line CSS

**Folder Structure:** `inline-css/`

In this task, you will apply in-line CSS to your web page. Follow these steps:

1. Create a new GitHub repository named "WebMentorship-Day3-InlineCSS."

2. Clone the new repository to your local machine using Git.

3. Inside the local repository directory, create three new folders: `folder-internal`, `folder-external`, and `folder-inline`.

4. Copy the downloaded `index.html` file and paste it into all three folders (`folder-internal`, `folder-external`, and `folder-inline`).

5. In the `index.html` file inside the `folder-inline`, choose a specific element (e.g., an image or a paragraph) on your web page to style.

6. Within that element's HTML tag, use the `style` attribute to apply in-line CSS styles directly. Experiment with different CSS properties and values to change the appearance of the chosen element.

   ```html
   <!-- Example for in-line CSS -->
   <img src="cat.jpg" alt="A cute cat" style="background-color: #ffcc00;">

   <p style="color: #990000; font-size: 18px;">This cat breed is known for its playful nature.</p>

   <div style="border: 1px solid #999999; padding: 15px;">
     <!-- Content here -->
   </div>
   ```

7. Commit your changes with a meaningful message and push them to your GitHub repository.

### Submission

Once you've completed all three tasks, create a new pull request in the main repository, adding links to your three individual repositories (one for each task) in the `submission.md` file. This will showcase your work, and the pull request will serve as your submission.