+++
title = 'Understanding the Flow of a Vue.js Project Created with Vue CLI - Lesson-2'
date = 2024-04-25T12:56:29+05:30
draft = false
weight = 2
+++

## Introduction

Vue.js is a progressive framework used for building user interfaces. It differs from other frameworks and libraries in its simplicity and flexibility, particularly how it integrates into projects where you might only need Vue for a part of the front-end. In this lesson, we'll explore the typical flow of a Vue.js project that has been set up using Vue CLI, covering how the application starts, initializes, and renders its main components.

**Initial Setup and Project Structure**

When you set up a new project with Vue CLI, the tool scaffolds a structured project directory that includes configuration files, source files, and directories that follow best practices for Vue development. Here’s what the typical structure looks like:

```js
my-vue-app/
├── node_modules/
├── public/
│   ├── favicon.ico
│   └── index.html
├── src/
│   ├── assets/
│   ├── components/
│   ├── App.vue
│   ├── main.js
├── .gitignore
├── package.json
├── README.md
└── vue.config.js

```

- **node_modules/**: Contains all npm packages and dependencies.
- **public/**: Static files like the favicon and index.html, the entry point for the application.
- **src/**: The core of your application's source code.
- **assets/**: Static assets such as images and stylesheets.
- **components/**: Individual Vue components.
- **App.vue**: The main component that acts as the root of your Vue application.
- **main.js**: The JavaScript entry point that creates and mounts the Vue app.

1. **Entry Point: index.html**

Every Vue.js application starts with a simple HTML file located in the public folder. This file serves as the scaffold for your app:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1.0" />
    <title>my-vue-app</title>
  </head>
  <body>
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
</html>
```

The `<div id="app"></div>` is crucial as it provides the mounting point for the Vue application.

2. **Bootstrapping Vue: main.js**

The main.js file in the src directory is where the Vue app is instantiated and mounted to the DOM. It imports Vue, the root component (App.vue), and potentially other plugins like Vue Router or Vuex. Here's how a basic main.js looks with Vue 3:

```js
import { createApp } from "vue";
import App from "./App.vue";

createApp(App).mount("#app");
```

- **Vue Application Creation:** `createApp(App)` creates a new Vue application instance using App as the root component.
- **Mounting:** `.mount('#app')` tells Vue to attach the app instance to the DOM element with the ID app, effectively integrating the Vue-managed content within the existing HTML.

3. **Rendering Components: App.vue**
   The App.vue file is typically the root component in a Vue project, serving as the central hub where other components are integrated. Here’s what a simple App.vue might look like:

```vue
<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```

**How It Works**

- **Template:**The template includes an `<img>` tag that displays an image, which is the Vue logo. This image uses the src attribute to link to the logo file stored in the ./assets directory, demonstrating how static assets are managed in Vue.js. The `HelloWorld` component is imported and used in this template. It receives a prop msg with the value "Welcome to Your Vue.js App". This component is responsible for displaying a greeting message, showcasing how parent components pass data to child components via props.

- **Script:** The `<script>` section contains the JavaScript logic for the component. This is where you define the component's properties, data, methods, and other options using Vue’s options API. In the example, the component is named App. Inside the export default block, the component is registered under the name `HelloWorld`. This allows it to be used within this file’s template. The name property of 'App' is also declared here, which is useful for debugging purposes and certain Vue.js plugins.

**Style:** The `<style>` section defines the CSS that applies to this component. Styles can be scoped to the component, meaning they will not affect other parts of the application. However, in the example above, the styles are global.

The `App.vue` component is structured to handle both static assets and components seamlessly. It demonstrates fundamental concepts of `Vue.js`, such as component usage, prop handling, asset management, and styling. This setup ensures that as your application scales, the main app container `(App.vue)` can effectively manage and organize multiple components and styles, maintaining a clean and modular architecture.

## Conclusion

In this lesson, we've learned about the how vue js application works and flow of the code.
