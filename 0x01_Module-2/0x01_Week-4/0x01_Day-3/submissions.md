# Module 2: Advanced Front-end
## Week 4: Day 3 - Form Management in React

### Outline
1. **Introduction to Forms in React**
2. **Controlled vs. Uncontrolled Components**
3. **Handling Form Inputs**
4. **Managing Form State**
5. **Validation of Form Inputs**
6. **Submitting Forms**
7. **Using Form Libraries (Formik & React Hook Form)**
8. **Creating a Complete Form Example**
9. **Q&A and Wrap-up**

### Course Content

#### 1. Introduction to Forms in React
- **Understanding Forms:**
  - Discuss the role of forms in web applications and how they are used to collect user input. Highlight the importance of effective form management for user experience.

#### 2. Controlled vs. Uncontrolled Components
- **Controlled Components:**
  - Explain that in controlled components, form data is handled by the React component's state, making it easy to control the input value.

  ```javascript
  const [inputValue, setInputValue] = useState('');

  const handleChange = (event) => {
      setInputValue(event.target.value);
  };

  return <input value={inputValue} onChange={handleChange} />;
  ```

- **Uncontrolled Components:**
  - Discuss uncontrolled components, which manage their own state internally. These can be accessed using refs.

  ```javascript
  const inputRef = useRef(null);

  const handleSubmit = () => {
      alert(inputRef.current.value);
  };

  return <input ref={inputRef} />;
  ```

#### 3. Handling Form Inputs
- **Event Handling:**
  - Explain how to handle input changes using event handlers to update the component state based on user input.

- **Multiple Inputs:**
  - Show how to manage multiple form inputs using a single state object.

  ```javascript
  const [formData, setFormData] = useState({ name: '', email: '' });

  const handleChange = (event) => {
      const { name, value } = event.target;
      setFormData({ ...formData, [name]: value });
  };
  ```

#### 4. Managing Form State
- **State Management Techniques:**
  - Discuss strategies for managing form state, including local component state, lifting state up, and using context API for larger forms.

#### 5. Validation of Form Inputs
- **Basic Validation:**
  - Explain how to perform basic validation on form inputs (e.g., required fields, email format).

  ```javascript
  const validateEmail = (email) => {
      const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return re.test(String(email).toLowerCase());
  };
  ```

- **Error Messages:**
  - Show how to display error messages to inform users of validation issues.

#### 6. Submitting Forms
- **Handling Form Submission:**
  - Describe how to prevent default form submission behavior and handle the submission with custom logic.

  ```javascript
  const handleSubmit = (event) => {
      event.preventDefault();
      // Process form data
  };
  ```

#### 7. Using Form Libraries (Formik & React Hook Form)
- **Introduction to Form Libraries:**
  - Explain the benefits of using form libraries to simplify form management in React applications.

- **Formik Example:**
  - Show how to set up Formik for managing forms.

  ```javascript
  import { Formik, Form, Field, ErrorMessage } from 'formik';

  const MyForm = () => (
      <Formik
          initialValues={{ name: '', email: '' }}
          onSubmit={(values) => {
              console.log(values);
          }}
      >
          <Form>
              <Field name="name" />
              <ErrorMessage name="name" component="div" />
              <Field name="email" type="email" />
              <ErrorMessage name="email" component="div" />
              <button type="submit">Submit</button>
          </Form>
      </Formik>
  );
  ```

- **React Hook Form Example:**
  - Introduce React Hook Form for managing form state with hooks.

  ```javascript
  import { useForm } from 'react-hook-form';

  const MyForm = () => {
      const { register, handleSubmit } = useForm();

      const onSubmit = (data) => {
          console.log(data);
      };

      return (
          <form onSubmit={handleSubmit(onSubmit)}>
              <input {...register('name')} />
              <input {...register('email')} />
              <button type="submit">Submit</button>
          </form>
      );
  };
  ```

#### 8. Creating a Complete Form Example
- **Building a Registration Form:**
  - Create a complete example of a registration form using either Formik or React Hook Form. Include validation and error messages.

#### 9. Q&A and Wrap-up
- **Open Floor for Questions:**
  - Encourage participants to ask questions about managing forms in React applications.

- **Recap of Key Takeaways:**
  - Summarize the importance of form management, the differences between controlled and uncontrolled components, and the benefits of using form libraries.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with React components and hooks.

### Additional Resources
- **React Documentation on Forms:**
  - [React Forms](https://reactjs.org/docs/forms.html)

- **Formik Documentation:**
  - [Formik](https://formik.org/docs/overview)

- **React Hook Form Documentation:**
  - [React Hook Form](https://react-hook-form.com/get-started)

- **Video Tutorial on Form Management in React:**
  - [React Forms Tutorial](https://www.youtube.com/watch?v=7Zr27IDBr40)


