+++
title = 'Understanding the Flow in a Project Created with Next.js - Lession 4'
date = 2024-04-20T23:26:57+05:30
draft = false
weight = 4

+++

Given that Create React App is officially deprecated, developers are encouraged to explore other methodologies for initiating new React projects. Next.js stands out as a recommended approach, as suggested by the latest React documentation. This framework not only simplifies setup but also enriches the development experience with robust features such as built-in routing and server-side rendering.

**Setting Up a Next.js Project**

To start a new Next.js project, which is now a favored alternative to Create React App, you can use the following commands:

```bash
npx create-next-app my-next-app
cd my-next-app
npm run dev

```

These steps create and launch a new Next.js application:

- `npx create-next-app my-next-app:` Generates a new project in the my-next-app directory, configuring all necessary dependencies and initial files.
- `cd my-next-app:` Moves into your new project directory.
- `npm run dev:` Fires up the development server at `http://localhost:3000`, where you can instantly start seeing your application come to life.

**Project Directory Structure**

Here’s a breakdown of what each directory and key file in a Next.js project is used for:

- `pages/`: Each JavaScript or JSX file here automatically corresponds to a route. The file name determines the route's path.
- `public/`: This directory holds static files like images and fonts, accessible from the root URL.
- `styles/`: Contains CSS files for styling your application.
- `components/ (optional)`: Commonly used for reusable components across different pages.
- `node_modules/`: Includes all npm packages required by the project.
- `package.json`: Manages dependencies, scripts, and project metadata.

**Code Flow and Component Creation**

## 1. pages/index.js:

This file serves as the home page for your Next.js application. The framework's routing is based on the presence of files within the pages directory.

```js
import Head from "next/head";
import Link from "next/link";

export default function Home() {
  return (
    <div>
      <Head>
        <title>Home Page</title>
        <meta name="description" content="Welcome to our homepage" />
      </Head>
      <h1>Welcome to Next.js</h1>
      <p>This is the homepage of your Next.js application.</p>
      <Link href="/about">
        <a>About Us</a>
      </Link>
    </div>
  );
}
```

## 2. pages/about.js:

Adding a new file like about.js in the pages directory sets up an automatic route at /about.

```js
import Head from "next/head";

export default function About() {
  return (
    <div>
      <Head>
        <title>About Us</title>
      </Head>
      <h1>About Us</h1>
      <p>This page provides information about our team and mission.</p>
    </div>
  );
}
```

**Built-in Routing:**

Next.js utilizes file-based routing, where each file in the pages directory automatically becomes accessible as a route, making setup and scaling straightforward without additional routing configuration.

**Creating Components**

For reusable components, such as navigation bars or buttons, create a components directory:

`components/Navbar.js:`

```js
export default function Navbar() {
  return (
    <nav>
      <ul>
        <li>Home</li>
        <li>About</li>
        <li>Contact</li>
      </ul>
    </nav>
  );
}
```

These components can be imported and used in any of your page files, promoting reusability and maintaining a clean codebase.

## Conclusion

Next.js is a powerful, efficient alternative for developing React applications, especially with the deprecation of Create React App. It provides advanced features like automatic routing and server-side rendering out-of-the-box, which are essential for modern web applications. This guide offers a comprehensive overview of setting up and navigating a Next.js project, showcasing how its built-in features can significantly streamline the development process.
