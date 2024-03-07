+++
title = 'How to Extend Webpack Config React'
date = 2024-02-22T12:48:10+05:30
draft = false
+++

To extend the webpack configuration in a Create React App project without directly altering the built-in configuration, you would typically need to 'eject' by running npm run eject. This command exposes all the hidden configuration files and scripts, allowing you to customize them. However, ejecting is irreversible and can make your project configuration more complex and harder to manage.

Fortunately, there are third-party libraries available that provide a more manageable approach to customizing the webpack configuration without ejecting. Two popular choices are react-app-rewired and Craco (Create React App Configuration Override).

## Using react-app-rewired:

Install react-app-rewired:

```bash
npm install react-app-rewired --save-dev
```

In your project's root, create a `config-overrides.js` file where you'll specify your webpack customizations. For example:

```javascript
module.exports = function override(config, env) {
  // do stuff with the webpack config...
  return config;
};
```

Modify the scripts in your package.json to use react-app-rewired instead of react-scripts. For instance:

```json

"scripts": {
  "start": "react-app-rewired start",
  "build": "react-app-rewired build",
  "test": "react-app-rewired test"
}
```

## Using Craco:

Install Craco:

```bash
npm install craco --save-dev
```

In your project's root, create a `craco.config.js` file where you'll specify your webpack customizations. For example:

```javascript
module.exports = {
  webpack: {
    configure: (webpackConfig, { env, paths }) => {
      // do stuff with the webpack config...
      return webpackConfig;
    },
  },
};
```

Modify the scripts in your package.json to use Craco instead of react-scripts. For instance:

```json
"scripts": {
  "start": "craco start",
  "build": "craco build",
  "test": "craco test"
}
```

Both react-app-rewired and Craco allow you to extend and override the webpack configuration provided by Create React App without ejecting, maintaining the simplicity of CRA while adding your custom configurations.
