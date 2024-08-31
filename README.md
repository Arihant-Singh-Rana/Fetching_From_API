# React Product Display By Fetching From an API

## Objective
---
The goal of this React application is to fetch and display product information from the [Dummy JSON Products API](https://dummyjson.com/products). The app uses modern React features, such as hooks (`useState` and `useEffect`), and makes asynchronous API requests using Axios.

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/your-repo.git
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Run the application:**

   ```bash
   npm start
   ```

4. **Open your browser and navigate to `http://localhost:3000` to view the app.**

## Fetching Data from API

To fetch data from the [Dummy JSON Products API](https://dummyjson.com/products), the application uses the `axios` library and React hooks. Here's a breakdown of the relevant code:

### Explanation:

- The `useEffect` hook is used to handle side effects in functional components. In this case, it's fetching data from the API.
- Inside the `useEffect`, an asynchronous function `fetchData` is defined to make the API call using `axios.get`.
- Upon a successful response, the `setData` function is used to update the state with the fetched product data.
- Error handling is implemented using a `try...catch` block to log any errors that might occur during the API request.
- The `fetchData` function is invoked within the `useEffect`, ensuring that the data is fetched when the component mounts.

### Code Snippet:

```jsx
import React, { useState, useEffect } from "react";
import axios from "axios";
import "./App.css";

export default function App() {
  // State to hold the fetched data
  const [data, setData] = useState([]);

  // useEffect hook to perform the data fetching
  useEffect(() => {
    // Async function to fetch data
    async function fetchData() {
      try {
        // Make a GET request to the API endpoint
        const response = await axios.get("https://dummyjson.com/products");
        
        // Update the state with the fetched data
        setData(response.data.products);
      } catch (error) {
        // Handle errors if any
        console.error("Error fetching data:", error);
      }
    }

    // Invoke the fetchData function
    fetchData();
  }, []); // Empty dependency array ensures the effect runs only once, equivalent to componentDidMount

  // Code to render the fetched data in a card layout (not shown in this snippet)
  let show = data.slice(0, 15).map((res, index) => (
    // ... (your card component)
  ));

  // Return the JSX rendering
  return <div className="parent">{show}</div>;
}
```

Feel free to customize this template based on your project's specifics. Add any additional sections or details that you think would be helpful for users exploring or contributing to your project.
