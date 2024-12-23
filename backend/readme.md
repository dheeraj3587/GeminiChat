
# Project Documentation

## Table of Contents
- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
  - [User Routes](#user-routes)
  - [Project Routes](#project-routes)
  - [AI Routes](#ai-routes)
- [Middleware](#middleware)
- [Models](#models)
- [Services](#services)
- [Controllers](#controllers)
- [Database Connection](#database-connection)

## Introduction
This project is a backend application built with Node.js, Express, and MongoDB. It includes user authentication, project management, and AI integration using Google Generative AI.

## Project Structure
```plaintext
├── app.js
├── controllers
│   ├── ai.controller.js
│   ├── project.controller.js
│   └── user.controller.js
├── db
│   └── db.js
├── middleware
│   └── auth.middleware.js
├── models
│   ├── project.model.js
│   └── user.model.js
├── readme.md
├── routes
│   ├── ai.routes.js
│   ├── project.routes.js
│   └── user.routes.js
├── server.js
└── services
    ├── ai.service.js
    ├── project.service.js
    ├── redis.service.js
    └── user.service.js

## Installation
1. Clone the repository.
2. Install dependencies:
   ```sh
   npm install
   ```

3. Create a `.env` file and add the following environment variables:
   ```sh
   PORT=3000
   MONGODB_URI=your_mongodb_uri
   JWT_SECRET=your_jwt_secret
   GOOGLE_AI_KEY=your_google_ai_key
   REDIS_HOST=your_redis_host
   REDIS_PORT=your_redis_port
   REDIS_PASSWORD=your_redis_password
   ```

## Usage
To start the server, run:
```sh
npm start
```

## API Endpoints

### User Routes
#### POST /users/register
Registers a new user.
- Body: `{ email: string, password: string }`
- Response: `{ user, token }`

#### POST /users/login
Logs in a user.
- Body: `{ email: string, password: string }`
- Response: `{ user, token }`

#### GET /users/profile
Gets the profile of the logged-in user.
- Response: `{ user }`

#### GET /users/logout
Logs out the user.
- Response: `{ message: 'Logged out successfully' }`

#### GET /users/all
Gets all users except the logged-in user.
- Response: `{ users }`

### Project Routes
#### POST /projects/create
Creates a new project.
- Body: `{ name: string }`
- Response: `{ project }`

#### GET /projects/all
Gets all projects of the logged-in user.
- Response: `{ projects }`

#### PUT /projects/add-user
Adds users to a project.
- Body: `{ projectId: string, users: string[] }`
- Response: `{ project }`

#### GET /projects/get-project/:projectId
Gets a project by ID.
- Response: `{ project }`

#### PUT /projects/update-file-tree
Updates the file tree of a project.
- Body: `{ projectId: string, fileTree: object }`
- Response: `{ project }`

### AI Routes
#### GET /ai/get-result
Gets AI-generated result based on a prompt.
- Query: `prompt=string`
- Response: `{ result }`

## Middleware
`auth.middleware.js`
- `authUser`: Middleware to authenticate users using JWT and Redis for token blacklisting.

## Models
### `user.model.js`
Mongoose schema for user with email and password fields.
- Methods: `hashPassword`, `isValidPassword`, `generateJWT`.

### `project.model.js`
Mongoose schema for project with name, users, and fileTree fields.

## Services
### `user.service.js`
- `createUser`: Creates a new user.
- `getAllUsers`: Gets all users except the specified user.

### `project.service.js`
- `createProject`: Creates a new project.
- `getAllProjectByUserId`: Gets all projects by user ID.
- `addUsersToProject`: Adds users to a project.
- `getProjectById`: Gets a project by ID.
- `updateFileTree`: Updates the file tree of a project.

### `ai.service.js`
- `generateResult`: Generates AI result based on a prompt using Google Generative AI.

### `redis.service.js`
Initializes and exports a Redis client.

## Controllers
### `user.controller.js`
- `createUserController`: Handles user registration.
- `loginController`: Handles user login.
- `profileController`: Gets the profile of the logged-in user.
- `logoutController`: Logs out the user.
- `getAllUsersController`: Gets all users except the logged-in user.

### `project.controller.js`
- `createProject`: Handles project creation.
- `getAllProject`: Gets all projects of the logged-in user.
- `addUserToProject`: Adds users to a project.
- `getProjectById`: Gets a project by ID.
- `updateFileTree`: Updates the file tree of a project.

### `ai.controller.js`
- `getResult`: Gets AI-generated result based on a prompt.

## Database Connection
### `db.js`
Connects to MongoDB using Mongoose.
```
