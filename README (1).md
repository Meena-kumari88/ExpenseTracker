# Expense Tracker Backend

## Overview
This repository contains the backend code for a RESTful API that powers an Expense Tracker application. The application allows users to sign up, log in, and manage their expenses by adding, viewing, updating, and deleting expense records. 

## Technology Stack

Here's a breakdown of the technologies used in this project:

**Core Technologies**

- **Node.js:** The JavaScript runtime environment for building fast and scalable server-side applications. [https://nodejs.org/](https://nodejs.org/)
- **Express.js:**  A minimalist web framework for Node.js that simplifies routing, middleware, and handling HTTP requests. [https://expressjs.com/](https://expressjs.com/)
- **MongoDB:** A NoSQL document-oriented database that stores data in a JSON-like format (BSON). [https://www.mongodb.com/](https://www.mongodb.com/)
- **MongoDB Atlas:** A cloud-based database-as-a-service offering from MongoDB, providing scalability and high availability. [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)

**Key Libraries and Tools**

- **Mongoose:**  An Object Data Modeling (ODM) library for MongoDB and Node.js that makes it easier to interact with MongoDB databases using JavaScript schemas.
[https://mongoosejs.com/](https://mongoosejs.com/)
- **CORS (cors):** Enables Cross-Origin Resource Sharing, allowing requests from your frontend (e.g., React, Angular, Vue) to interact with this backend API. [https://www.npmjs.com/package/cors](https://www.npmjs.com/package/cors)
- **dotenv:**  Loads environment variables from a `.env` file for managing sensitive data (API keys, database credentials). [https://www.npmjs.com/package/dotenv](https://www.npmjs.com/package/dotenv)
- **bcryptjs:** A library for securely hashing passwords before storing them in the database.
[https://www.npmjs.com/package/bcryptjs](https://www.npmjs.com/package/bcryptjs)
- **jsonwebtoken:** A library used for creating and verifying JSON Web Tokens (JWT) to handle user authentication and authorization. 
[https://www.npmjs.com/package/jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken)

## Project Structure

```
expense-tracker-backend/
├── models/
│   ├── Expense.js     // Expense data model (Mongoose schema)
│   └── User.js        // User data model (Mongoose schema)
├── routes/
│   ├── expenses.js   // Routes for handling expense data
│   └── auth.js       // Routes for user authentication (signup/login)
└── server.js          // Main server file (Express.js setup, routes, database connection)
```

## Functionality

### 1. User Authentication

- **`/api/auth/signup` (POST):** Registers a new user. It takes a username, email and password. The password will be hashed using `bcryptjs` before saving it to the database.
- **`/api/auth/login` (POST):** Logs in an existing user. It verifies the provided email and password against the stored hashed password using `bcryptjs`'s `compare` method.  If the credentials are valid, it generates a JWT (JSON Web Token) using `jsonwebtoken` for authentication. 

### 2. Expense Management

- **`/api/expenses` (GET):**  Retrieves a list of all expenses.
- **`/api/expenses` (POST):**  Creates a new expense record.
- **`/api/expenses/:id` (PUT):** Updates an existing expense by its ID. 
- **`/api/expenses/:id` (DELETE):**  Deletes an expense by its ID.

## Getting Started

1.  **Prerequisites:** Install Node.js and MongoDB on your local machine or have a MongoDB Atlas cluster set up. 
2.  **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/expense-tracker-backend.git
    ```
3.  **Install Dependencies:**
    ```bash
    cd expense-tracker-backend
    npm install 
    ```
4.  **Environment Variables:**
   Create a file named  `.env`  in the root directory to store your environment variables. Add the following with your actual credentials:

    ```
    MONGO_URI=your_mongodb_connection_string
    JWT_SECRET=your_jwt_secret_key
    ```
    
5.  **Start the Server:**
    ```bash
    npm start
    ```

The backend API should now be running, usually on `http://localhost:5000`  (or a different port specified in your `.env` file). You'll need to create a frontend application (React, Angular, Vue.js, or any other) to interact with this backend API.
