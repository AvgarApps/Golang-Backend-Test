
# Golang Backend Take-Home Test

## Overview
Create a simple Go REST API for a task management system. The API should allow users to create, retrieve, update, and delete tasks. Additionally, it should include an endpoint that performs a periodic background task using goroutines. The data should be stored in a  database.

### Instructions
- Please provide the source code in a GitHub repository, with instructions on how to run the application.
- Include a `README.md` file that explains your design choices and how to set up and test the application.

---

## Requirements
1. **Go Version**: Use Go 1.20 or above.
2. **Database**: PostgreSQL or MongoDB.
3. **HTTP Server**: Use `net/http`.
4. **Goroutines**: Implement a background process using goroutines that runs every 5 minutes to perform a specific task.

---

## Functional Specifications

### 1. Task Management API

- **GET /tasks**  
  Retrieve a list of all tasks.  
  **Response**:
  ```json
  [
    {
      "id": 1,
      "title": "Buy groceries",
      "description": "Milk, Bread, Eggs",
      "completed": false,
      "created_at": "2024-11-08T10:00:00Z"
    }
  ]
  ```

- **GET /tasks/{id}**  
  Retrieve a task by ID.  
  **Response**:
  ```json
  {
    "id": 1,
    "title": "Buy groceries",
    "description": "Milk, Bread, Eggs",
    "completed": false,
    "created_at": "2024-11-08T10:00:00Z"
  }
  ```

- **POST /tasks**  
  Create a new task.  
  **Request Body**:
  ```json
  {
    "title": "Finish homework",
    "description": "Math and Science assignments"
  }
  ```  
  **Response**:
  ```json
  {
    "id": 2,
    "title": "Finish homework",
    "description": "Math and Science assignments",
    "completed": false,
    "created_at": "2024-11-08T11:00:00Z"
  }
  ```

- **PUT /tasks/{id}**  
  Update an existing task (title, description, completed status).  
  **Request Body**:
  ```json
  {
    "title": "Finish homework",
    "description": "Math and Science assignments",
    "completed": true
  }
  ```

- **DELETE /tasks/{id}**  
  Delete a task by ID.  
  **Response**:  
  ```json
  {
    "message": "Task deleted successfully"
  }
  ```

### 2. Background Task (Goroutines)
- Implement a background goroutine that runs every **5 minutes** to check for tasks marked as completed for over **7 days** and delete them from the database.
- Log the results of each run to a file.


