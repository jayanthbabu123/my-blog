+++
title = 'How to make an API call in Angular: Complete Guide'
date = 2023-12-25T14:33:36+05:30
draft = false
tags = [
    "Angular",
    "Angular 13",
    "Angular 14",
    "Angular 15",
    "Angular 16",
    "Angular 17",
    "API",
    "Angular API",
    "API Call",
    "Angular API Call",
    "Angular API Tutorial",
    "Angular API Integration",
    "Angular API Integration Tutorial",
    "Angular API Integration with Angular",
    "Angular API Integration with Angular Tutorial",
    "Angular API Integration with Angular 13",
    "Angular API Integration with Angular 14",
    "Angular API Integration with Angular 15",
    "Angular API Integration with Angular 16",
    "Angular API Integration with Angular 17"
]
categories = ["Angular"]
favorite= true
image= "/images/angular-api-call.png"
+++

![Angular API Call](/images/angular-api-call.png)
### Introduction 🚀
In your Angular projects, you'll often find the need to retrieve data from external APIs or send data back to a server. Whether you're a beginner or a seasoned developer, understanding how to communicate with external APIs is crucial in the world of web development. It's a key aspect of web development that allows your applications to be dynamic and responsive, fetching and displaying data in real time.

As of the time of writing this article, the latest version of Angular is `Angular 17`. let's get started and unlock the power of APIs in Angular! 🌟

### What is an API? 🤔
Think of an API `(Application Programming Interface)` like a menu in a restaurant. The menu provides a list of dishes you can order, along with a description of each dish. When you specify which dish you want, the kitchen (the system) prepares the dish and serves it. In the same way, an API lists a bunch of operations that developers can use, along with a description of what they do. The developer then chooses which operations to use in their application.

## Setting Up Your Angular Environment ⚙️
First, ensure you have the latest version of Angular installed. If you're new to Angular, visit the Angular Getting Started Guide to set up your development environment.

### Step 1: Create a New Angular Service 🛠️
In Angular, services are used to handle business logic and data operations, such as communicating with APIs. A service is a class with a specific purpose and reusable code that can be injected into components or other services in the application.
Generate a new service named 'data'. This service will handle all the API interactions. Open your terminal, navigate to your Angular project directory, and run the following command.

```bash
ng generate service data
```

Executing this command creates a new file named `data.service.ts` in your project's directory. Your `data.service.ts` file will initially look something like this:

```typescript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class DataService {

  constructor() { }

}

```
`@Injectable({ providedIn: 'root' })`: This decorator marks the class as a service that can be injected. `providedIn: 'root'` means this service is available throughout the application.

### Step 2: Import HttpClientModule 🌐
Angular's `HttpClientModule` enables the application to communicate with backend services over HTTP. It provides the `HttpClient` service, which is essential for making HTTP requests.

Include `HttpClientModule` in your main Angular module.

```typescript
// In app.module.ts
import { HttpClientModule } from '@angular/common/http';

@NgModule({
  imports: [
    HttpClientModule
  ],
  // ... other metadata
})
export class AppModule { }

```

### Step 3: Inject HttpClient into Your Service 💉
`HttpClient` is Angular's mechanism for communicating with external APIs. By injecting it into your service, you enable the service to perform HTTP requests.

Open the `data.service.ts` file in your project and inject `HttpClient` into your newly created data service.

```typescript
// In data.service.ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';

@Injectable({
  providedIn: 'root'
})
export class DataService {
  constructor(private http: HttpClient) { }
}
```

`constructor(private http: HttpClient) { }`: Here, HttpClient is injected into the DataService class, enabling it to make HTTP requests.
### Step 4: Create a Method for GET Requests 📡
Add a `getData` method in the `DataService` class. This method will utilize `HttpClient` to make a GET request to an API.
To do this, open your `data.service.ts` file and add a new method called getData inside the DataService class. This method will use Angular's `HttpClient` to make the GET request and it will return an Observable, which is a key concept in Angular for handling asynchronous operations.

For demonstration purposes, this method will make a GET request to the `JSONPlaceholder` API, a free fake online REST API. Feel free to replace the URL with your own API endpoint in your projects.

Here is how your `data.service.ts` file will look after adding the getData method:

```typescript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class DataService {
  constructor(private http: HttpClient) { }

  getData(): Observable<any> {
    return this.http.get('https://jsonplaceholder.typicode.com/todos/1');
  }
}
```
With this setup, your service is now capable of fetching data from an external source.

### Step 5: Call the API from a Component 📞
In this step, you'll integrate the API call into an Angular component. Components in Angular manage the user interface and interactions, making them ideal for displaying the data fetched from the API.

**Inject DataService:** Begin by injecting DataService into your component's constructor. This makes the service available within the component.

**Initialize Data in ngOnInit:** Use Angular's ngOnInit lifecycle hook to initiate the API call. Inside ngOnInit, call the getData method from DataService and subscribe to its Observable. This setup allows you to handle the response asynchronously and store it in a component property.

Your App Component code looks like this after injecting data service

```typescript
import { Component, OnInit } from '@angular/core';
import { DataService } from './data.service';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {
  data: any;

  constructor(private dataService: DataService) {}

  ngOnInit() {
    this.dataService.getData().subscribe(response => {
      this.data = response;
      console.log(this.data);
    });
  }
}
```
With this implementation, your component is now capable of displaying data fetched from the API.

### Step 6: Display the Data in Your Component 🖥️
Now that you have fetched the data from the API, the final step is to display this data in your Angular component's template.
**Implementing Data Display:**
**Modify the HTML Template:** In the HTML file of your component `(e.g., app.component.html)`, use Angular's data binding to show the fetched data.

**Use Angular Directives:** Utilize the *ngIf directive for conditional rendering and the {{ }} syntax for data interpolation.

This is how your `app.component.html` looks like

```html
<!-- In app.component.html -->
<div *ngIf="data">
  <h2>Data from API:</h2>
  <pre>{{ data | json }}</pre>
</div>
```

This simple setup checks if data is available and then displays it in a formatted JSON structure. With this, your Angular application now successfully fetches and displays data from an API, bringing dynamic content to your users.

### Step 7: Check Out the Code Sandbox Demo 🧪
For your convenience, a practical demonstration has been set up. Please check out the demo here on CodeSandbox. This demo includes an implementation of the concepts covered in this guide, giving you a hands-on example to explore and learn from.


<iframe src="https://codesandbox.io/p/devbox/affectionate-leaf-tkry82?embed=1&file=%2Fsrc%2Fapp%2Fapp.component.ts" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" title="QR code in React"></iframe>

### Conclusion 🚀
You've now walked through the process of making API calls in Angular, from setting up your environment to displaying data in your components. This skill is a key part of building interactive and dynamic web applications. As you continue your development journey, keep exploring and applying these concepts to different scenarios.

The more you practice and experiment, the more comfortable you'll become with Angular's powerful features.
Happy Coding!!!