# Todo App Backend

A Node.js backend for a Todo application with MongoDB, featuring user authentication and task management.

## Features

- User registration and login with JWT authentication
- Task CRUD operations
- Search functionality
- Pagination
- Secure password hashing
- MongoDB integration

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or Atlas)

## Setup

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file in the root directory with the following variables:
   ```
   PORT=3000
   MONGODB_URI=mongodb://localhost:27017/todo-app
   JWT_SECRET=your_jwt_secret_key_here
   ```
4. Start the development server:
   ```bash
   npm run dev
   ```

## API Endpoints

### Authentication

- `POST /api/auth/register` - Register a new user
  - Body: `{ "name": "string", "email": "string", "password": "string" }`

- `POST /api/auth/login` - Login user
  - Body: `{ "email": "string", "password": "string" }`

### Tasks

- `POST /api/tasks` - Create a new task
  - Headers: `Authorization: Bearer <token>`
  - Body: `{ "title": "string", "description": "string" }`

- `GET /api/tasks` - Get tasks with search and pagination
  - Headers: `Authorization: Bearer <token>`
  - Query params: `page`, `limit`, `search`

- `PATCH /api/tasks/:id` - Update a task
  - Headers: `Authorization: Bearer <token>`
  - Body: `{ "title": "string", "description": "string", "completed": boolean }`

- `DELETE /api/tasks/:id` - Delete a task
  - Headers: `Authorization: Bearer <token>`

## Error Handling

The API returns appropriate HTTP status codes and error messages:

- 200: Success
- 201: Created
- 400: Bad Request
- 401: Unauthorized
- 404: Not Found
- 500: Server Error 