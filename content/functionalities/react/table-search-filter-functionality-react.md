+++
title = 'Table Search and Filter Functionality React JS'
date = 2024-04-15T15:43:11+05:30
draft = false
+++

## Introduction

In this tutorial, we will develop a feature-rich, dynamic table component using React. This component will not only display a list of places but also include interactive elements like a search box and a city filter dropdown. The functionality will allow users to filter and search through the table dynamically based on their input. This guide is designed to help developers integrate such a component into any React application, providing a hands-on approach to learning React's powerful capabilities for handling state and user inputs.

## Step 1: Create the Table Component

To begin, set up a basic React component that will serve as the foundation for displaying data in a table format. This component, called DataTable, will accept a prop named data, which contains the places we want to display. Here's how you can structure this component to render a table with headers for "Name," "City," and "Description."

```jsx
// src/components/DataTable.js
import React from "react";

function DataTable({ data }) {
  return (
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>City</th>
          <th>Description</th>
        </tr>
      </thead>
      <tbody>
        {data.map((place) => (
          <tr key={place.id}>
            <td>{place.name}</td>
            <td>{place.city}</td>
            <td>{place.description}</td>
          </tr>
        ))}
      </tbody>
    </table>
  );
}

export default DataTable;
```

In this code, DataTable is a functional React component that renders a table. The `<thead>` section defines the column headers, and the `<tbody>` section dynamically generates rows based on the data prop. Each item from the data array is used to populate one row of the table, ensuring that each place's name, city, and description are presented clearly. This component emphasizes a clean, efficient approach to rendering tabular data in React.

## Step 2: Declare 10 Places Data

Next, we need to establish a dataset that our DataTable component will consume. This data should be structured as an array of objects where each object represents a place with properties for name, city, and description. Here’s an example dataset containing 10 different locations. This array is essential as it forms the basis of what will be rendered in our table.

```jsx
const placesData = [
  {
    name: "Central Park",
    city: "New York",
    description: "A large public, urban park in the city center.",
  },
  {
    name: "Golden Gate Bridge",
    city: "San Francisco",
    description: "A suspension bridge spanning the Golden Gate.",
  },
  {
    name: "Statue of Liberty",
    city: "New York",
    description: "A colossal statue on Liberty Island.",
  },
  {
    name: "Disneyland",
    city: "Anaheim",
    description: "The happiest place on earth.",
  },
  {
    name: "Grand Canyon",
    city: "Arizona",
    description: "A steep-sided canyon carved by the Colorado River.",
  },
  {
    name: "Mount Rushmore",
    city: "South Dakota",
    description: "Sculpture carved into the granite face of Mount Rushmore.",
  },
  {
    name: "Alcatraz Island",
    city: "San Francisco",
    description: "Notorious former prison located on an island.",
  },
  {
    name: "Times Square",
    city: "New York",
    description: "Major commercial intersection and tourist destination.",
  },
  {
    name: "Las Vegas Strip",
    city: "Las Vegas",
    description:
      "Stretch of South Las Vegas Boulevard known for its concentration of resort hotels and casinos.",
  },
  {
    name: "White House",
    city: "Washington D.C.",
    description:
      "The official residence of the President of the United States.",
  },
];
```

This dataset represents a diverse set of famous locations across the United States. Each object is uniquely identified by its name, city, and a brief description, providing context that will be useful when displayed in the table.

## Step 3: Display the Data in Table

Now that we have our data and table component, let's integrate them into the main part of our application. This step involves utilizing the DataTable component within a parent component called App. Here, placesData is passed as a prop to DataTable, enabling it to render the data dynamically.

```jsx
// src/components/App.js
import React from "react";
import DataTable from "./DataTable";

function App() {
  return (
    <div>
      <DataTable data={placesData} />
    </div>
  );
}

export default App;
```

In this step, we create an App component that includes the `DataTable` component, which is passed the placesData. This approach demonstrates the power of React's component-based architecture, allowing us to pass data through props effectively. The ReactDOM.render method then mounts the App component onto the page, making our data table visible on the web page.

## Step 4: Add a Search Box

To enhance the usability of our data table, we'll incorporate a search box that enables users to quickly find places based on the name or description. This feature will significantly enhance user interaction by allowing real-time filtering of the table's contents.

```jsx
import React from "react";
import DataTable from "./DataTable"; // Ensure DataTable is properly imported

function App() {
  const [searchTerm, setSearchTerm] = React.useState(""); // State to hold the search term

  // Filter the data based on the search term entered by the user
  const filteredData = placesData.filter(
    (place) =>
      place.name.toLowerCase().includes(searchTerm.toLowerCase()) ||
      place.description.toLowerCase().includes(searchTerm.toLowerCase())
  );

  return (
    <>
      <input
        type="text"
        placeholder="Search by name or description..."
        value={searchTerm}
        onChange={(e) => setSearchTerm(e.target.value)} // Update the search term as the user types
        style={{ margin: "10px 0", padding: "8px", width: "300px" }} // Basic styling for better visibility
      />
      <DataTable data={filteredData} /> // Render the DataTable with the filtered
      data
    </>
  );
}

export default App;
```

In this step, we added an input element above the data table to serve as the search box. We maintain the search term in the component's state using React's `useState` hook. This state updates dynamically with every keystroke in the search box, thanks to the onChange event handler that modifies the `searchTerm` state.

The `filteredData` variable holds the result of filtering placesData based on the current `searchTerm`. The filtering logic checks whether the `name` or `description` of each place includes the text entered in the search box, applying the `toLowerCase()` method to ensure case-insensitive comparisons.

We then pass this `filteredData` to the `DataTable` component, which re-renders the table based on the search input. This makes our table dynamically respond to user inputs, enhancing the interactivity of our React application.

## Step 5: Add Select Dropdown
Adding a dropdown to filter by city allows users to narrow down the list of places according to where they are located. This step involves integrating a dropdown component into our existing application structure and linking it to the data rendering logic.

```jsx
import React from 'react';
import DataTable from './DataTable';  // Ensure DataTable is properly imported

function App() {
    const [searchTerm, setSearchTerm] = React.useState('');
    const [selectedCity, setSelectedCity] = React.useState('');  // State to hold the selected city

    // Extract a list of unique cities from the places data for the dropdown
    const cities = Array.from(new Set(placesData.map(place => place.city)));

    // Filter the data based on the search term and selected city
    const filteredData = placesData.filter(place =>
        (place.name.toLowerCase().includes(searchTerm.toLowerCase()) ||
        place.description.toLowerCase().includes(searchTerm.toLowerCase())) &&
        (selectedCity === '' || place.city === selectedCity)
    );

    return (
        <>
            <input
                type="text"
                placeholder="Search by name or description..."
                value={searchTerm}
                onChange={(e) => setSearchTerm(e.target.value)}
                style={{ margin: '10px 0', padding: '8px', width: '300px' }}
            />
            <select
                value={selectedCity}
                onChange={(e) => setSelectedCity(e.target.value)}
                style={{ margin: '10px 0', padding: '8px', width: '200px' }}
            >
                <option value="">All Cities</option>
                {cities.map((city, index) => (
                    <option key={index} value={city}>{city}</option>
                ))}
            </select>
            <DataTable data={filteredData} />
        </>
    );
}

export default App;

```

In this the App component, we introduce a new piece of state called selectedCity. This state holds the currently selected city from the dropdown, which influences the data filtering process.

**Extract Unique Cities:** We start by extracting a list of unique cities from placesData using map to gather all cities and Set to eliminate duplicates. This list populates the dropdown menu, ensuring each city is only listed once.

**Dropdown Component:** The dropdown is created with a select element, which has its value bound to `selectedCity`. As users change their selection, setSelectedCity updates the state. The dropdown initially presents an option to display all cities, which corresponds to an empty string ("") value.

**Data Filtering:** The `filteredData` is recalculated to include both text search and city filtering. The combined filter checks if each place's name or description contains the search term and also matches the selected city, if one is selected.

`Styling and Layout:` Basic styling is applied to the search input and dropdown for consistency and better user experience. They are both given margins, padding, and specified widths.

## Step 6: Apply Basic Styles to the Table Component
We will apply basic CSS styles to our table to improve its readability and aesthetic appeal. This will involve setting styles for the table header, rows, and cells, as well as general layout adjustments to ensure the table is visually attractive.

```css
/* index.css */
table {
    width: 100%;
    border-collapse: collapse; 
    margin-top: 20px;
    background-color: #f9f9f9; 
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

th, td {
    border: 1px solid #ccc; 
    text-align: left;
    padding: 8px;
}

th {
    background-color: #4CAF50; 
    color: white; 
}

tr:nth-child(even) {
    background-color: #f2f2f2; 
}

tr:hover {
    background-color: #ddd; 
}

/* Styling for the search input and dropdown */
input[type="text"], select {
    width: 100%; 
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box; 
}

/* Button styling if needed */
button {
    width: 100%;
    background-color: #4CAF50;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

```
By integrating these styles, your data table component will not only function effectively but also have a professional, clean look that improves the user experience.

## Conclusion

Throughout this tutorial, we've successfully developed a dynamic and interactive data table component in React. We introduced functionalities such as a search box and a city filter dropdown, enhancing user interaction and data accessibility. We also applied basic CSS styling to ensure the table is not only functional but visually appealing.

This guide highlights the effectiveness of React's component-based architecture and demonstrates essential techniques for data manipulation and presentation in web applications. The skills acquired here will be useful for building a wide range of data-driven interfaces, enriching your development capabilities.
