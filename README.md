# cloud973 21BCP351 Rachit Vaidya 
# Building a 3-Tier Application with JavaScript, Node.js, React, and Database Connectivity

In the realm of modern web development, creating robust applications often involves a multi-layered architecture to ensure scalability, maintainability, and performance. A 3-tier architecture, comprising a presentation layer, business logic layer, and data storage layer, is a common approach to achieve these goals. In this blog, we'll explore how to code a 3-tier application using JavaScript, Node.js, React, and a database connection.

## Understanding the 3-Tier Architecture

Before diving into coding, let's understand the three tiers of our application:

1. **Presentation Layer (Frontend):** This layer handles user interaction and displays the user interface. We'll use React, a popular JavaScript library for building dynamic UIs, to create our frontend components.

2. **Business Logic Layer (Backend):** This layer processes and manages data, implements business rules, and communicates with the frontend and data storage layer. We'll use Node.js, a server-side JavaScript runtime, to build our backend logic.

3. **Data Storage Layer (Database):** This layer stores and retrieves data. For our database, we'll use MongoDB, a NoSQL database that offers flexibility and scalability.

## Setting Up the Environment

To begin, ensure you have Node.js and MongoDB installed on your machine. You can install Node.js from [nodejs.org](https://nodejs.org/) and MongoDB from [mongodb.com](https://www.mongodb.com/). Additionally, have a code editor like Visual Studio Code or Sublime Text ready for coding.

## Coding the Backend (Node.js)

1. **Initialize the Backend Project:**
   Create a new directory for your backend project and initialize it with npm.
   ```bash
   mkdir backend && cd backend
   npm init -y
   ```

2. **Install Dependencies:**
   Install required dependencies such as Express (for building APIs) and Mongoose (for MongoDB connectivity).
   ```bash
   npm install express mongoose
   ```

3. **Create Server and Routes:**
   Set up an Express server in `server.js` and define routes for handling API requests.

   ```javascript
   // server.js
   const express = require('express');
   const app = express();
   const PORT = process.env.PORT || 5000;

   // Middleware
   app.use(express.json());

   // Routes
   app.get('/api/data', (req, res) => {
       // Logic to fetch data from MongoDB
       res.json({ message: 'Data from MongoDB' });
   });

   // Start the server
   app.listen(PORT, () => {
       console.log(`Server running on port ${PORT}`);
   });
   ```

4. **Connect to MongoDB:**
   Connect your backend to MongoDB using Mongoose in `db.js`.

   ```javascript
   // db.js
   const mongoose = require('mongoose');
   mongoose.connect('mongodb://localhost/mydatabase', {
       useNewUrlParser: true,
       useUnifiedTopology: true
   });
   ```

## Coding the Frontend (React)

1. **Initialize the Frontend Project:**
   Create a new directory for your frontend project and initialize it with Create React App.
   ```bash
   npx create-react-app frontend
   cd frontend
   ```

2. **Install Axios:**
   Axios is a popular library for making HTTP requests. Install it in your frontend project.
   ```bash
   npm install axios
   ```

3. **Create Components and API Integration:**
   Build React components in the `src/components` directory and integrate with your backend APIs using Axios.

   ```javascript
   // App.js
   import React, { useEffect, useState } from 'react';
   import axios from 'axios';

   const App = () => {
       const [data, setData] = useState('');

       useEffect(() => {
           axios.get('/api/data')
               .then(response => setData(response.data.message))
               .catch(error => console.error(error));
       }, []);

       return (
           <div>
               <h1>Data from Backend</h1>
               <p>{data}</p>
           </div>
       );
   };

   export default App;
   ```

4. **Start the Frontend Server:**
   Run the React development server to see your frontend in action.
   ```bash
   npm start
   ```

## Conclusion

Congratulations! You've successfully coded a 3-tier application using JavaScript, Node.js, React, and MongoDB. This setup allows for a scalable and efficient development process, separating concerns between frontend, backend, and data storage layers. You can further enhance this application by adding authentication, more API endpoints, and advanced frontend features. Happy coding!
