
# Module 2: Advanced Front-end
## Week 1: Day 2 - Exploring Advanced Front-end Frameworks

### Outline
1. **Introduction to Vue.js**
2. **Exploring Angular**
3. **Package Management with pnpm and Yarn**
4. **CSS Framework Integration**
5. **Q&A and Wrap-up**

### Course Content

#### 1. Introduction to Vue.js
**Overview of Vue.js**
- **What is Vue.js?**
  Vue.js is a progressive JavaScript framework used for building user interfaces and single-page applications. Its core library focuses on the view layer, making it easy to integrate with other libraries or existing projects.

- **Key Features and Advantages:**
  - **Reactive Data Binding:** Automatically updates the view when the model changes.
  - **Component-Based Architecture:** Encourages code reusability and separation of concerns.
  - **Virtual DOM:** Optimizes rendering for performance.

**Building a Simple Vue.js Application**
- **Setting Up a Vue.js Project:**
  - Use Vue CLI to scaffold a new project.
  - Navigate to the project directory and start the development server.

  ```bash
  npm install -g @vue/cli
  vue create my-project
  cd my-project
  npm run serve
  ```

- **Creating and Managing Components:**
  - Create a `HelloWorld.vue` component in the `src/components` directory.
  - Use the component in `App.vue`.

  ```html
  <template>
    <div>
      <HelloWorld msg="Welcome to Your Vue.js App!" />
    </div>
  </template>
  
  <script>
  import HelloWorld from './components/HelloWorld.vue';
  
  export default {
    components: {
      HelloWorld
    }
  }
  </script>
  ```

- **Utilizing Vue Router:**
  - Install Vue Router for navigation between components.
  
  ```bash
  vue add router
  ```

  - Set up routes and link navigation in the app.

**Activity:**
Participants will build a simple Vue.js application with at least two components and implement basic routing.

#### 2. Exploring Angular
**Overview of Angular**
- **What is Angular?**
  Angular is a platform and framework for building client applications in HTML and TypeScript. It provides a comprehensive set of tools for developing large-scale applications.

- **Key Features and Advantages:**
  - **Two-Way Data Binding:** Synchronizes data between the model and the view.
  - **Modular Development:** Organizes code into modules for better maintainability.
  - **Dependency Injection:** Simplifies the management of dependencies.

**Creating Angular Components**
- **Setting Up an Angular Project:**
  - Use Angular CLI to create a new project.
  
  ```bash
  npm install -g @angular/cli
  ng new my-angular-app
  cd my-angular-app
  ng serve
  ```

- **Creating and Managing Components:**
  - Generate a new component using Angular CLI.
  
  ```bash
  ng generate component my-component
  ```

  - Implement the component logic and template.

- **Introduction to Angular Services:**
  - Create a service to manage data and share it between components.
  
  ```bash
  ng generate service my-data
  ```

**Activity:**
Participants will develop a custom Angular component and implement it in a basic application.

#### 3. Package Management with pnpm and Yarn
**Introduction to Package Managers**
- **What are Package Managers?**
  Package managers automate the process of installing, upgrading, configuring, and removing software packages, ensuring project dependencies are managed effectively.

**Comparing pnpm and Yarn**
- **Key Differences and Advantages:**
  - **pnpm**: Uses a content-addressable filesystem to save disk space and speed up installations.
  - **Yarn**: Offers offline capabilities and a lock file for consistent installs across machines.

**Demonstrating Usage:**
- **Using pnpm:**
  
  ```bash
  pnpm init
  pnpm add vue
  ```

- **Using Yarn:**
  
  ```bash
  yarn init
  yarn add vue
  ```

**Activity:**
Participants will create a small project using pnpm or Yarn and document their experience.

#### 4. CSS Framework Integration
**Overview of CSS Frameworks**
- **Introduction to Popular CSS Frameworks:**
  CSS frameworks provide pre-designed styles and components to accelerate UI development. Popular frameworks include Bootstrap, Tailwind CSS, and Bulma.

**Integrating a CSS Framework into Your Project**
- **Steps to Integrate a CSS Framework:**
  - Choose a CSS framework that suits your project needs.
  - Install the framework via npm or include it through a CDN in the project.

**Activity:**
Participants will integrate a CSS framework into their Vue.js or Angular application and apply styling to their components.

#### 5. Q&A and Wrap-up
- Open floor for questions and clarifications on the topics covered.
- Recap of key takeaways from the day.
- Overview of the tasks to be completed by the next session.

### Required Materials
- Access to a computer with a code editor (e.g., VSCode) installed.
- Node.js and npm installed on your system.
- Familiarity with Git for version control.

### Additional Resources
- [Vue.js Official Documentation](https://vuejs.org/v2/guide/)
- [Angular Official Documentation](https://angular.io/docs)
- [pnpm Documentation](https://pnpm.js.org/)
- [Yarn Documentation](https://classic.yarnpkg.com/en/docs/)
- [Bootstrap Documentation](https://getbootstrap.com/docs/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)

