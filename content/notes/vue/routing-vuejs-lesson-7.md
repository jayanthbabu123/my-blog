+++
title = 'Routing Vuejs Lesson 7'
date = 2024-04-26T13:09:23+05:30
draft = false
weight = 7
+++

Routing is a crucial aspect of modern web applications, allowing users to navigate between different views or pages without reloading the page. Vue.js 3, with its Vue Router library, makes setting up routing straightforward and efficient. This guide will walk you through the process of setting up routing in a Vue.js 3 project, from installation to creating components and handling navigation.

## Step 1: Install Vue Router

First, you need to install Vue Router in your project. Open your terminal, navigate to your project directory, and run the following command:

```bash
npm install vue-router@next
```

## Step 3: Create Components

Next, create the components for Home, Dashboard, and Profile. In your **src/views** directory, create three files: `Home.vue`, `Dashboard.vue`, `Profile.vue` and `NotFound.vue` for your routes.

Here are the Components created in the **src/views** directory:

1. **Home Component**
   The Home component serves as the landing page of your application. It might include a welcome message and links to other sections of your app.

```js
<!-- src/views/Home.vue -->
<template>
 <div>
    <h1>Welcome to the Home Page</h1>
    <p>This is the main page of our application.</p>
    <router-link to="/dashboard">Go to Dashboard</router-link>
 </div>
</template>

<script>
export default {
 name: 'Home',
};
</script>

<style scoped>
h1 {
 color: #333;
}
</style>

```

2. **Dashboard Component**

The Dashboard component could display user-specific data or analytics. It might include a navigation link back to the Home page.

```js
<!-- src/views/Dashboard.vue -->
<!-- src/views/Dashboard.vue -->
<template>
 <div>
    <h1>Dashboard</h1>
    <p>This is the dashboard where you can see your data.</p>
    <router-link to="/">Back to Home</router-link>
 </div>
</template>

<script>
export default {
 name: 'Dashboard',
};
</script>

<style scoped>
h1 {
 color: #007bff;
}
</style>

```

## 3. Profile Component

The Profile component is where users can view and edit their personal information. It might include a form for updating the user's details.

```js
<!-- src/views/Profile.vue -->
<template>
 <div>
    <h1>Profile</h1>
    <p>This is your profile page.</p>

    <router-link to="/">Back to Home</router-link>
 </div>
</template>

<script>
export default {
 name: 'Profile',
 data() {
    return {
      user: {
        name: 'John Doe',
      },
    };
 },

};
</script>

<style scoped>
h1 {
 color: #28a745;
}
</style>

```

4. **NotFound Component**
   The NotFound component is displayed when the user navigates to a route that does not exist. It might include a message and a link back to the Home page.

```js
<!-- src/views/NotFound.vue -->
<template>
 <div>
    <h1>404 - Page Not Found</h1>
    <p>The page you are looking for does not exist.</p>
    <router-link to="/">Back to Home</router-link>
 </div>
</template>

<script>
export default {
 name: 'NotFound',
};
</script>

<style scoped>
h1 {
 color: #dc3545;
}
</style>

```

These components provide a basic structure for a Vue.js 3 application with routing. Each component includes a template, a script section for component logic, and a style section for scoped CSS. The router-link component is used for navigation between pages, and the router.push method can be used for programmatic navigation.

## Step 4: Create a Header Component

The Header component will now include a responsive design using Bootstrap classes for a better user experience on different devices. It will also demonstrate how to use Vue Router's Link component for navigation and how to handle active link styling.

First, ensure you have Bootstrap installed in your project. If not, you can add it via npm:

```bash
npm install bootstrap
```

Then, import Bootstrap in your `main.js` or `main.ts` file:

```js
// main.js or main.ts
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap";
```

Now, let's create the improved Header component:

```js
<!-- src/components/Header.vue -->
<template>
 <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">My App</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link class="nav-link" to="/" active-class="active">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/dashboard" active-class="active">Dashboard</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/profile" active-class="active">Profile</router-link>
          </li>
        </ul>
      </div>
    </div>
 </nav>
</template>

<script>
export default {
 name: 'Header',
};
</script>

<style scoped>
.active {
 color: #007bff; /* Bootstrap primary color */
}
</style>

```

This Header component uses Bootstrap classes for a responsive navigation bar. The router-link component is used for navigation, with the active-class attribute to apply a custom style to the active link. The active class in the `<style>` section changes the color of the active link to Bootstrap's primary color.

## Step 5: Integrating Vue Router and Components

After setting up your routes and creating your components, the next step is to integrate Vue Router with your Vue.js 3 application and ensure that all components are correctly registered and accessible. This step is crucial for enabling navigation between different views and ensuring that your application's structure is well-organized.

**Registering Components**

In Vue.js 3, components can be registered in two main ways: globally and locally. Global registration makes a component available throughout your entire application, while local registration restricts the component to a specific part of your application.

**Global Registration**

For components that are used frequently across your application, such as a Header or Footer component, global registration is often the best approach. This way, you don't need to import and register the component in every component where it's used.

To globally register a component, you can use the `app.component` method in your `main.js` file. For example, to globally register the Header component:

```js
// main.js
import { createApp } from "vue";
import App from "./App.vue";
import router from "./router";
import Header from "./components/Header.vue";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap";
const app = createApp(App);
app.use(router);
app.component("app-header", Header); // Registering Header globally
app.mount("#app");
```

With the Header component registered globally, you can now use it in any component without needing to import it again.

**Local Registration**

For components that are used only in specific parts of your application, local registration is more appropriate. This keeps your global namespace clean and ensures that components are only loaded when they are needed.

To locally register a component, you import it in the script section of the parent component and then register it in the components option:

```js
<!-- src/views/Dashboard.vue -->
<template>
 <div>
    <app-header></app-header>
    <!-- Dashboard content -->
 </div>
</template>

<script>
import Header from '../components/Header.vue';

export default {
 components: {
    'app-header': Header,
 },
};
</script>

```

**Handling the Header Component**

The Header component, being a common element across your application, is a good candidate for global registration. This way, you can easily include it in your App.vue or any other component without needing to import it each time.

```js
<!-- src/App.vue -->
<template>
 <div id="app">
    <app-header></app-header>
    <router-view></router-view>
 </div>
</template>

```

By following these guidelines, you ensure that your Vue.js 3 application is well-structured and that components are efficiently managed. Whether you choose global or local registration depends on the specific needs of your application and the frequency of component usage

## Step 6: Programmatic Navigation in Vue.js 3

Programmatic navigation in Vue.js 3 is a powerful feature that allows you to navigate between routes programmatically, enabling more dynamic and responsive user experiences. This method is not limited to components that are directly involved in routing but is available to all components within your Vue.js application, including those like the Header component that might not be directly associated with routing logic.

**Using this.$router.push for Navigation**

The primary method for programmatic navigation in Vue Router is the `this.$router.push` method. This method allows you to navigate to a different route by specifying the target route's path or name. It's important to note that `this.$router.push` is available to all components, regardless of their role in routing.

Here's a basic example of using `this.$router.push` to navigate to a different route when a button is clicked:

```js
<template>
 <button @click="navigateToDashboard">Go to Dashboard</button>
</template>

<script>
export default {
 methods: {
    navigateToDashboard() {
      this.$router.push({ name: 'Dashboard' });
    },
 },
};
</script>

```

In this example, clicking the button triggers the navigateToDashboard method, which uses `this.$router.push` to navigate to the route named 'Dashboard'. This method can be used in any component, including those not directly involved in routing, such as the Header component.

**Navigating with Parameters**

When navigating to routes that require parameters, you can pass these parameters as part of the this.$router.push method. This is particularly useful for dynamic routes.

```js
<template>
 <button @click="navigateToProfile">View Profile</button>
</template>

<script>
export default {
 methods: {
    navigateToProfile() {
      this.$router.push({ name: 'Profile', params: { userId: 123 } });
    },
 },
};
</script>

```

In this example, the navigateToProfile method navigates to the 'Profile' route and passes a userId parameter, which can be used in the target component to fetch and display the user's profile.

## Conclusion

Setting up routing in a Vue.js 3 project is a straightforward process, thanks to Vue Router. This guide covered the basics of installing Vue Router, setting up routes, creating components, and handling navigation. With these steps, you can efficiently manage navigation in your Vue.js 3 applications, enhancing the user experience and making your web applications more dynamic and responsive.


