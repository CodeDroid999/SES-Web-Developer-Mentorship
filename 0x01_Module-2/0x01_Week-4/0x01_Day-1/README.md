# Module 2: Advanced Front-end
## Week 4: Day 1 - Managing Forms in React with Formik

### Outline
1. **Introduction to Form Handling in React**
2. **What is Formik?**
3. **Benefits of Using Formik**
4. **Setting Up Formik**
5. **Creating Forms with Formik**
6. **Validation with Formik**
7. **Handling Form Submission**
8. **Advanced Form Features**
9. **Q&A and Wrap-up**

### Course Content

#### 1. Introduction to Form Handling in React
- **Understanding Forms in React:**
  - Discuss the challenges of managing form state, validation, and submission in React applications. Highlight common issues like uncontrolled vs. controlled components.

#### 2. What is Formik?
- **Overview of Formik:**
  - Formik is a popular library for building forms in React. It simplifies form state management and validation, allowing developers to focus on form functionality rather than boilerplate code.

#### 3. Benefits of Using Formik
- **Advantages of Formik:**
  - **Simplicity:** Reduces boilerplate code needed for forms.
  - **Validation:** Built-in support for form validation and error messages.
  - **Controlled Components:** Automatically handles form field state, making it easier to manage controlled components.

#### 4. Setting Up Formik
- **Installation:**
  ```bash
  npm install formik
  ```

- **Basic Usage:**
  ```javascript
  import { Formik, Form, Field } from 'formik';

  const MyForm = () => (
    <Formik
      initialValues={{ name: '', email: '' }}
      onSubmit={(values) => {
        console.log(values);
      }}
    >
      {() => (
        <Form>
          <Field name="name" placeholder="Name" />
          <Field name="email" placeholder="Email" type="email" />
          <button type="submit">Submit</button>
        </Form>
      )}
    </Formik>
  );
  ```

#### 5. Creating Forms with Formik
- **Basic Form Structure:**
  - Show how to create a simple form using Formik’s `Form`, `Field`, and `Formik` components.

- **Accessing Field Values:**
  ```javascript
  <Field name="name" placeholder="Name" />
  ```

#### 6. Validation with Formik
- **Adding Validation:**
  - Demonstrate how to use Formik’s `validate` prop or Yup for schema-based validation.
  
  ```javascript
  import * as Yup from 'yup';

  const validationSchema = Yup.object({
    name: Yup.string().required('Required'),
    email: Yup.string().email('Invalid email address').required('Required'),
  });

  <Formik
    initialValues={{ name: '', email: '' }}
    validationSchema={validationSchema}
    onSubmit={(values) => {
      console.log(values);
    }}
  >
  ```

- **Displaying Validation Errors:**
  ```javascript
  <ErrorMessage name="name" component="div" />
  ```

#### 7. Handling Form Submission
- **Submitting the Form:**
  - Discuss the `onSubmit` handler and how to access form values when the form is submitted.

#### 8. Advanced Form Features
- **Handling Nested Fields:**
  - Explain how to manage complex forms with nested fields using Formik.

- **Field Arrays:**
  - Show how to manage arrays of fields for dynamic form structures.
  
  ```javascript
  import { FieldArray } from 'formik';

  <FieldArray name="friends">
    {({ insert, remove, push }) => (
      <div>
        {values.friends.length > 0 &&
          values.friends.map((friend, index) => (
            <div key={index}>
              <Field name={`friends.${index}`} placeholder="Friend's Name" />
              <button type="button" onClick={() => remove(index)}>Remove</button>
            </div>
          ))}
        <button type="button" onClick={() => push('')}>Add Friend</button>
      </div>
    )}
  </FieldArray>
  ```

#### 9. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions about using Formik and handling forms in React.

- **Recap of Key Takeaways:**
  - Summarize the advantages of using Formik for form handling and how it simplifies form management in React applications.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with React components and hooks.

### Additional Resources
- **Formik Documentation:**
  - [Formik](https://formik.org/docs/overview)

- **Getting Started with Formik:**
  - [Formik Quick Start](https://formik.org/docs/overview#quick-start)

- **Yup Documentation:**
  - [Yup](https://github.com/jquense/yup)

- **Video Tutorial on Formik:**
  - [Formik Crash Course](https://www.youtube.com/watch?v=K2eBOj7D6V0)



