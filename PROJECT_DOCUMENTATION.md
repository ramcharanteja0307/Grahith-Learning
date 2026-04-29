# Grahith Learning Project Documentation

## Introduction
This document provides an extensive overview of the Grahith Learning project's architecture, API calls, frontend-backend connections, and a compilation of common interview questions and answers.

## Project Architecture
### Overview
Grahith Learning is designed with a microservices architecture that ensures scalability and ease of maintenance.

### Components
1. **Frontend**: Developed in React, communicating with the backend via RESTful API.
2. **Backend**: Node.js with Express framework, handling requests, user authentication, and data processing.
3. **Database**: MongoDB for storing user data, course materials, etc.
4. **Authentication**: JWT (JSON Web Tokens) for secure session management.

## API Calls
### Authentication
- **POST /api/login**: Authenticates user and returns a token.
  - Request body: `{ "username": "string", "password": "string" }`
- **POST /api/register**: Registers a new user.
  - Request body: `{ "username": "string", "password": "string", "email": "string" }`

### Courses
- **GET /api/courses**: Retrieves all courses.
- **GET /api/courses/:id**: Retrieves details for a specific course.
- **POST /api/courses**: Creates a new course (admin only).
  - Request body: `{ "title": "string", "description": "string" }`

## Frontend-Backend Connections
### Communication
The frontend communicates with the backend using Axios for sending HTTP requests. Each request appends the user's JWT in the headers for authentication.

### Example
```javascript
import axios from 'axios';

const fetchCourses = async () => {
    const response = await axios.get('/api/courses', {
        headers: { Authorization: `Bearer ${localStorage.getItem('token')}` }
    });
    return response.data;
};
```

## Interview Q&A
### Common Questions
1. **What is JWT?**  
   JWT (JSON Web Token) is a compact, URL-safe means of representing claims to be transferred between two parties. It helps in securely transmitting information as a JSON object.

2. **How do you secure API endpoints?**  
   By implementing middleware that checks for a valid JWT before proceeding with the request processing.

3. **Explain Microservices architecture.**  
   This architecture pattern breaks down applications into smaller, independent services that communicate with each other using APIs, which improves flexibility and scalability.

## Conclusion
This documentation serves as a guideline for developers and stakeholders involved in the Grahith Learning project, outlining its structure, functionality, and operational details.