+++
title = 'Components in Vuejs Lesson 3'
date = 2024-04-25T14:34:52+05:30
draft = false
weight = 3
+++

In Vue 3, the process of creating and using components has been streamlined, making it even easier to develop modular, maintainable applications. In this section, we'll explore how to write and use three basic components: **Home**, **Dashboard**, and **Profile**. Each component will be designed for a specific purpose, and we'll demonstrate how to integrate these components into a Vue 3 application.

Let's define three components: Home, Dashboard, and Profile. Each component will have its basic template and a simple script setup if necessary.

## Home Component

The Home component will serve as the landing page of the application.

**Home.vue:**

```vue
<template>
  <div class="home">
    <h1>Welcome to the Home Page</h1>
    <p>This is the starting point of our Vue application.</p>
  </div>
</template>

<script>
export default {
  name: "Home",
};
</script>

<style scoped>
.home h1 {
  color: #42b983;
}
.home p {
  color: #35495e;
}
</style>
```

## Dashboard Component

The Dashboard component could be where users interact with the main features of your application.

**Dashboard.vue:**

```vue
<template>
  <div class="dashboard">
    <h1>Welcome to the Dashboard</h1>
    <p>This is the dashboard of our Vue application.</p>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
};
</script>

<style scoped>
.dashboard h1 {
  color: #42b983;
}
.dashboard p {
  color: #35495e;
}
</style>
```

## Profile Component

The Profile component is for user-specific information.

**Profile.vue:**

```vue
<template>
  <div class="profile">
    <h1>Your Profile</h1>
    <p>Manage your personal information here.</p>
  </div>
</template>

<script>
export default {
  name: "Profile",
};
</script>

<style scoped>
.profile {
  background-color: #fff3e0;
  padding: 20px;
}
.profile h1 {
  color: #ff9800;
}
</style>
```

## 2. Using Components in the Main Application

Once you've created these components, the next step is to integrate them into a main application component. Let's assume you have a root component where these are used, such as App.vue.

App.vue:

```vue
<template>
  <div id="app">
    <Home />
    <Dashboard />
    <Profile />
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import Dashboard from "./components/Dashboard.vue";
import Profile from "./components/Profile.vue";

export default {
  name: "App",
  components: {
    Home,
    Dashboard,
    Profile,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
```

**Explanation**

- **Component Registration:** In App.vue, we import the Home, Dashboard, and Profile components and register them locally. This makes them available for use within the App.vue template.

- **Using Components:** The components are then used within the template of App.vue as custom elements. This demonstrates how components can be nested and utilized to build complex UI structures in Vue 3.

- **Scoped Styles:** Each component has its own scoped CSS, ensuring that styles do not leak into other parts of the application unintentionally.

## Conclusion

Creating and using components in Vue 3 helps in structuring your application into manageable, reusable pieces. By defining components like Home, Dashboard, and Profile, and integrating them into a main application component (App.vue), you can effectively organize and scale your Vue 3 projects. This approach promotes a clean architecture and allows each component to operate independently, improving maintainability and scalability.
