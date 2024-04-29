---
title: "Vue JS"
description: "Explore VueJS Notes here"
logo: "/images/vue.png"
layout: "language"
---

## Introduction

Vue.js is a progressive JavaScript framework used to develop interactive web interfaces. It primarily focuses on the view layer, which makes it easy to integrate into projects and other JavaScript libraries. Vue.js is not just a library but a full-fledged framework for building rich single-page applications (SPAs). It was created by Evan You, an ex-Google engineer, who wanted to extract the parts he liked about Angular and build something lightweight without the extra concepts involved in Angular.

## Comparison with React and Angular

Vue.js is often compared to Angular and React, two of the most popular front-end frameworks:

- **Angular** is a full-blown framework which includes a wide range of features out-of-the-box, such as HTTP client and form handling, making it somewhat heavier. Angular uses TypeScript, which can be a steep learning curve for new developers.

- **React** is a library focused on building user interfaces and requires additional libraries to handle routing and state management (like React Router and Redux). React's use of JSX, a syntax extension that allows HTML with JavaScript, is one of its unique features.

Vue.js stands out by combining the best aspects of both frameworks. It is approachable like React, with a similar component structure but simpler syntax and model. Like Angular, it offers a robust set of features but is much lighter and faster. Vue's template syntax is straightforward and uses plain HTML, making it very easy to learn, especially for those new to web development.

## Key Features of Vue.js

Vue.js offers several powerful features that make it a compelling choice for web developers:

- **Reactive Data Binding:** Vue.js facilitates the creation of dynamic data bindings between HTML elements and JavaScript objects, ensuring that changes in data are automatically reflected in the UI.
- **Component-Based Architecture:** Vue.js uses components, reusable custom elements that you can use in your HTML.
- **Directives:** Vue.js provides built-in directives like **v-bind** and **v-model** that offer functionality to HTML applications, making it easier to handle events and perform other actions on the front end.
- **Transition System:** Vue has a built-in transition system that allows adding effects when items are added, updated, or removed from the DOM.
- **Virtual DOM:** Like React, Vue uses a virtual DOM, which makes it very efficient at updating the smallest parts of the view in response to state changes.

## Creating a New Vue.js Project

Starting a new project in Vue.js can be done through several approaches, each tailored to different project needs and developer preferences. Here’s a breakdown of the most common methods to help you choose the best one for your situation:

1. **Vue CLI (Command Line Interface)**
   Vue CLI is the standard tool for rapid Vue.js development, offering a complete project structure and build system out of the box. It is ideal for developing large-scale applications or when you need a fine-tuned setup with specific configurations. To get started with Vue CLI, you'll need to install it first:

```bash
npm install -g @vue/cli
```

After installation, you can create a new project by running:

```bash
vue create my-vue-project
```

This command will guide you through several configuration options, such as choosing features like Babel, Vuex, Vue Router, linters, and more.

2. **Vite**

Vite is a modern and fast build tool that significantly speeds up the development and build process. It's especially useful for projects where rapid feedback and iteration are critical. Vite uses native ES Modules and skips unnecessary bundling during development, which results in lightning-fast rebuilds. To create a new project with Vite, use the following commands:

```bash
npm create vite@latest my-vue-app --template vue
cd my-vue-app
npm install
npm run dev

```

This sets up a new Vue 3 project using Vite, which you can start developing immediately.

3. **Including Vue via CDN**

For those looking to quickly add Vue to a webpage without npm or any build step, using a CDN is the simplest option. This method is best suited for small projects, experiments, or learning purposes. Simply add the following script tag to your HTML file to start using Vue immediately:

```html
<script src="https://cdn.jsdelivr.net/npm/vue@3"></script>
```

This script tag imports Vue 3 directly into your webpage, allowing you to leverage the latest features and improvements of Vue without any complex setup. It's a great way to quickly get started with Vue, especially for adding interactivity to static pages or prototyping new ideas.
