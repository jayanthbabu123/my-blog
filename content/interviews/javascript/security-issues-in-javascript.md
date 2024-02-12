+++
title = 'Security Issues in Javascript'
date = 2024-02-10T11:42:45+05:30
draft = false
+++

When developing web applications, especially with frameworks like React, it's crucial to be aware of security vulnerabilities like XSS and CSRF. Let me break down each and explain how to mitigate them, including what measures React itself takes.

### XSS

This is a security problem where attackers put harmful code into websites that other people use. The main defense against this in React is that it automatically makes sure any text from users cannot run as code. This means if someone tries to submit a script through a website form, React will treat it just as text, not something that can run.

Mitigation in React:

Automatic Escaping: React helps prevent XSS out of the box by automatically escaping strings in JSX. This means if an attacker tries to inject a script through user input, React will treat it as a string rather than executable code.

```jsx
function App() {
  const userInput = "<script>maliciousCode()</script>";
  // React will escape this, preventing the script from executing
  return <div>{userInput}</div>;
}
```

**dangerouslySetInnerHTML:** This property allows us to insert raw HTML into our component. Since this can be risky, React named it `dangerouslySetInnerHTML` to signal the need for caution. It's our responsibility to sanitize this HTML before rendering it, to prevent XSS. A common approach is using a library like `DOMPurify`.

```jsx
import DOMPurify from "dompurify";

function App() {
  const unsafeHtml = "<script>maliciousCode()</script>";
  const sanitizedHtml = DOMPurify.sanitize(unsafeHtml);

  return <div dangerouslySetInnerHTML={{ __html: sanitizedHtml }} />;
}
```

### Cross-Site Request Forgery (CSRF)

CSRF attacks trick the user into executing unwanted actions on a web application where they’re authenticated, potentially leading to unauthorized actions.

**Prevention:**

**SameSite Cookies:** Setting the SameSite attribute on cookies to Strict or Lax can prevent the browser from sending these cookies along with cross-site requests.

```javascript
Set-Cookie: sessionId=a3fWa; SameSite=Strict;
```

**CSRF Tokens:** Using CSRF tokens in your forms that are verified on the server side can prevent CSRF attacks by ensuring that the requests originate from your own application.

```html
// Including CSRF token in a form
<input type="hidden" name="csrf_token" value="{csrfToken}" />
```

## Implementing Content Security Policy (CSP)

CSP can be implemented through HTTP headers set on the web server or through a `<meta>` tag in the HTML document's `<head>` section. This policy helps in specifying the sources from which the application can load resources, effectively mitigating XSS attacks.

Via HTTP Header:

```javascript
Content-Security-Policy: default-src 'self'; script-src 'self' https://trusted-source.com;
```

Via `<meta>` tag:

```html
<meta
  http-equiv="Content-Security-Policy"
  content="default-src 'self'; script-src 'self' https://trusted-source.com"
/>
```

When you set a Content Security Policy (CSP) in your HTML document using a `<meta>` tag as shown, it instructs the browser to only allow web page resources (like scripts, styles, images, etc.) from specified sources. Specifically, this policy restricts all content sources to the same origin as the document itself (default-src 'self'), but allows scripts to be loaded from the document's origin and also from a trusted external source (`script-src 'self' https://trusted-source.com`). This setup significantly enhances security by preventing the execution of malicious scripts from untrusted sources, effectively mitigating the risk of Cross-Site Scripting (XSS) attacks. However, it also means that any resources not explicitly allowed by the policy will be blocked, which could potentially break functionalities that rely on external scripts or other resources not listed in the policy.
