+++
title = 'What is the Improtance of Web Vitals in React Project'
date = 2024-02-22T13:02:53+05:30
draft = false
+++

Web Vitals is an initiative by Google to provide unified guidance for quality signals that are essential to delivering a great user experience on the web. It focuses on three main aspects of website performance: loading performance, interactivity, and visual stability. These core Web Vitals are:

**Largest Contentful Paint (LCP):** Measures loading performance. To provide a good user experience, LCP should occur within 2.5 seconds of when the page first starts loading.

**First Input Delay (FID):** Measures interactivity. For a good user experience, pages should have an FID of 100 milliseconds or less.

**Cumulative Layout Shift (CLS):** Measures visual stability. Pages should maintain a CLS of 0.1 or less to ensure a good user experience.

Web Vitals can be measured in several ways, including using `Google's Lighthouse tool`, `Chrome User Experience Report`, or `PageSpeed Insights`. Developers can also use the `Web Vitals` JavaScript library to measure these metrics directly in their web applications.

In React applications, especially those created with Create React App (CRA), you might notice a file named reportWebVitals.js. This file is part of the default setup provided by CRA to help developers easily measure and report these vital metrics. The purpose of including this setup by default is to encourage developers to consider performance from the start of their project and to integrate performance tracking into their development and deployment workflows.

How Web Vitals are Useful in React Applications:

**Improving User Experience:** By focusing on metrics that affect user experience, developers can make informed decisions to optimize performance. For example, reducing LCP times can make the page feel faster to the user, improving satisfaction and engagement.

**SEO Optimization:** Google uses page experience signals, which include Core Web Vitals, in its ranking algorithms. Optimizing these metrics can contribute to better search engine visibility.

**Performance Monitoring:** Integrating Web Vitals measurement allows developers to track the real-world performance of their applications, identify issues, and measure the impact of optimizations.

How to Use the Web Vitals Library in React:

`The reportWebVitals.js `file is a convenient place to add the code that measures these metrics. The Web Vitals library provides functions to measure each of the Core Web Vitals:

```js
import { reportWebVitals } from 'web-vitals';

// Measure Web Vitals
reportWebVitals((metric) => {
    console.log(metric);
});
```
You can replace console.log with any reporting mechanism you prefer, such as sending the metrics to a backend endpoint where they can be analyzed and monitored over time.

In practice, the reportWebVitals function can look something like this:

```js
export function reportWebVitals(onPerfEntry) {
  if (onPerfEntry && onPerfEntry instanceof Function) {
    import('web-vitals').then(({ getCLS, getFID, getLCP, getTTFB, getFCP }) => {
      getCLS(onPerfEntry);
      getFID(onPerfEntry);
      getLCP(onPerfEntry);
      getTTFB(onPerfEntry);
      getFCP(onPerfEntry);
    });
  }
}

```

This setup demonstrates how to dynamically import the web-vitals library and use it to measure the various metrics. Each metric is measured by calling its corresponding function (`getCLS`, `getFID`, etc.), and the `onPerfEntry` callback function is used to handle the reported metrics.

