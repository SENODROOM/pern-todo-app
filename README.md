# PERN Stack Todo Application

![PERN Stack](https://www.freecodecamp.org/news/content/images/size/w2000/2020/03/PERN.png)

A full-stack Todo List application built with the PERN stack (PostgreSQL, Express.js, React, and Node.js). This project demonstrates how to create a complete CRUD (Create, Read, Update, Delete) application with a PostgreSQL database, Express REST API backend, and React frontend.

## 📺 Tutorial

This project is based on **The Stoic Programmers** PERN Stack Course, available on the [freeCodeCamp.org YouTube channel](https://www.youtube.com/watch?v=ldYcgPKEZC8).

## 🎯 Project Overview

This application showcases the integration of:
- **PostgreSQL** - Relational database for data persistence
- **Express.js** - Backend web framework for Node.js
- **React** - Frontend UI library
- **Node.js** - JavaScript runtime environment

The app allows users to manage their daily tasks with full CRUD functionality through a clean, intuitive interface.

## ✨ Features

- ➕ **Create** new todo items
- 📋 **Read/Display** all todos in a list
- ✏️ **Update/Edit** existing todos
- 🗑️ **Delete** completed or unwanted todos
- 🔄 **Real-time updates** between frontend and database
- 🎨 **Responsive UI** with Bootstrap styling

## 🏗️ Architecture

```
┌─────────────────┐
│   React Client  │  (Port 3000)
│   Frontend UI   │
└────────┬────────┘
         │ HTTP Requests
         │ (Fetch API)
         ▼
┌─────────────────┐
│  Express Server │  (Port 5000)
│   REST API      │
└────────┬────────┘
         │ SQL Queries
         │ (node-postgres)
         ▼
┌─────────────────┐
│   PostgreSQL    │
│    Database     │
└─────────────────┘
```

## 📁 Project Structure

```
pern-todo-app/
├── client/                 # React frontend
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/
│   │   │   ├── InputTodo.js      # Component for adding new todos
│   │   │   ├── ListTodos.js      # Component for displaying todos
│   │   │   └── EditTodo.js       # Component for editing todos
│   │   ├── App.js
│   │   └── index.js
│   └── package.json
│
├── server/                 # Express backend
│   ├── database.sql        # SQL schema for creating database table
│   ├── db.js              # Database connection configuration
│   ├── index.js           # Express server and API routes
│   └── package.json
│
└── README.md
```

## 🛠️ Technologies Used

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web application framework
- **node-postgres (pg)** - PostgreSQL client for Node.js
- **cors** - Enable Cross-Origin Resource Sharing

### Frontend
- **React** - UI library
- **React Hooks** (useState, useEffect) - State management
- **Bootstrap 5** - CSS framework for styling
- **Fetch API** - HTTP requests to backend

### Database
- **PostgreSQL** - Relational database management system

## 🚀 Getting Started

### Prerequisites

Before running this application, ensure you have the following installed:

- [Node.js](https://nodejs.org/) (v12 or higher)
- [PostgreSQL](https://www.postgresql.org/download/) (v12 or higher)
- npm or yarn package manager

### Database Setup

1. **Install and start PostgreSQL**

2. **Create the database**

   Open PostgreSQL command line (psql) and run:
   ```sql
   CREATE DATABASE perntodo;
   ```

3. **Connect to the database**
   ```sql
   \c perntodo
   ```

4. **Create the todo table**
   
   Use the schema provided in `server/database.sql`:
   ```sql
   CREATE TABLE todo(
     todo_id SERIAL PRIMARY KEY,
     description VARCHAR(255)
   );
   ```

### Server Setup

1. **Navigate to the server directory**
   ```bash
   cd server
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure database connection**
   
   In `server/db.js`, update the PostgreSQL connection settings if needed:
   ```javascript
   const Pool = require("pg").Pool;

   const pool = new Pool({
     user: "postgres",      // Your PostgreSQL username
     password: "password",  // Your PostgreSQL password
     host: "localhost",
     port: 5432,
     database: "perntodo"
   });
   ```

4. **Start the server**
   ```bash
   npm start
   # Or for development with nodemon:
   nodemon index
   ```

   The server will run on `http://localhost:5000`

### Client Setup

1. **Navigate to the client directory**
   ```bash
   cd client
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the React application**
   ```bash
   npm start
   ```

   The application will open in your browser at `http://localhost:3000`

## 🔌 API Endpoints

The Express server provides the following RESTful API endpoints:

| Method | Endpoint        | Description              | Request Body            |
|--------|----------------|--------------------------|-------------------------|
| POST   | `/todos`       | Create a new todo        | `{ description: "" }`   |
| GET    | `/todos`       | Get all todos            | -                       |
| GET    | `/todos/:id`   | Get a specific todo      | -                       |
| PUT    | `/todos/:id`   | Update a todo            | `{ description: "" }`   |
| DELETE | `/todos/:id`   | Delete a todo            | -                       |

### Example API Requests

**Create a Todo:**
```javascript
POST http://localhost:5000/todos
Content-Type: application/json

{
  "description": "Learn PERN stack"
}
```

**Update a Todo:**
```javascript
PUT http://localhost:5000/todos/1
Content-Type: application/json

{
  "description": "Master PERN stack"
}
```

**Delete a Todo:**
```javascript
DELETE http://localhost:5000/todos/1
```

## 📦 Dependencies

### Server Dependencies
```json
{
  "express": "^4.17.1",
  "cors": "^2.8.5",
  "pg": "^8.7.1"
}
```

### Client Dependencies
```json
{
  "react": "^17.0.2",
  "react-dom": "^17.0.2",
  "bootstrap": "^5.1.3"
}
```

## 🧩 Component Breakdown

### InputTodo Component
- Provides an input field for users to enter new todo descriptions
- Handles form submission
- Makes POST request to create new todos
- Refreshes the page after successful creation

### ListTodos Component
- Fetches all todos from the database on component mount
- Displays todos in a Bootstrap table
- Includes Edit and Delete buttons for each todo
- Manages the delete functionality with confirmation

### EditTodo Component
- Modal-based editing interface
- Pre-populates with current todo description
- Sends PUT request to update the todo
- Closes modal and refreshes list on successful update

## 🎓 Learning Outcomes

By building and studying this project, you will learn:

1. **Full-stack Development** - How to connect frontend, backend, and database
2. **RESTful API Design** - Creating and consuming REST APIs
3. **Database Operations** - CRUD operations with PostgreSQL
4. **React Hooks** - useState and useEffect for state management
5. **Asynchronous JavaScript** - Using async/await with Fetch API
6. **HTTP Methods** - Implementing GET, POST, PUT, DELETE requests
7. **CORS** - Handling Cross-Origin Resource Sharing
8. **Environment Configuration** - Managing different development environments

## 🔧 Development Tips

- Use **Postman** or **Thunder Client** (VS Code extension) to test API endpoints before building the frontend
- Install **nodemon** globally for automatic server restarts during development:
  ```bash
  npm install -g nodemon
  ```
- Use PostgreSQL command line tools to verify database changes:
  ```sql
  SELECT * FROM todo;  -- View all todos
  ```

## 🚢 Deployment Considerations

When deploying to production (e.g., Heroku):

1. Set up environment variables for database credentials
2. Configure production database connection
3. Update CORS settings for production domain
4. Build React app for production
5. Serve React static files from Express server

## 🤝 Contributing

This is an educational project based on The Stoic Programmers tutorial. Feel free to fork and expand upon it with additional features such as:

- User authentication
- Todo categories/tags
- Due dates and priorities
- Search and filter functionality
- Drag-and-drop reordering
- Dark mode toggle

## 📝 License

This project is open source and available for educational purposes.

## 🙏 Acknowledgments

- **The Stoic Programmers** - Original tutorial creators
- **freeCodeCamp.org** - Platform hosting the course
- **Henry Ly** - Course instructor

## 📚 Additional Resources

- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Express.js Guide](https://expressjs.com/en/guide/routing.html)
- [React Documentation](https://reactjs.org/docs/getting-started.html)
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [RESTful API Best Practices](https://restfulapi.net/)

## 💬 Support

If you encounter any issues or have questions:
1. Check the [original tutorial video](https://www.youtube.com/watch?v=ldYcgPKEZC8)
2. Review the freeCodeCamp article
3. Ensure all prerequisites are properly installed
4. Verify database connection settings

---

**Happy Coding! 🚀**
