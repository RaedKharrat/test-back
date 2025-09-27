# Blog Microservices Platform

A modern, scalable blog platform built with a microservices architecture using Node.js, Express, MongoDB, and Angular.

## 🏗️ Architecture Overview

This project follows a microservices pattern with the following components:

### Backend Services
- **API Gateway**: Single entry point for all client requests (Port: 3000)
- **User Service**: Handles authentication, authorization, and user management (Port: 3001)
- **Article Service**: Manages blog articles, comments, and content (Port: 3002)
- **Notification Service**: Real-time notifications using WebSockets (Port: 3003)

### Frontend
- **Angular Application**: Modern single-page application (Port: 4200)

## 📁 Project Structure
project/
├── microservices/ # Backend microservices
│ ├── api-gateway/ # API Gateway service
│ ├── user-service/ # Authentication & user management
│ ├── article-service/ # Articles and comments
│ ├── notification-service/ # Real-time notifications
│ └── package.json # Root package with scripts
└── frontend/ # Angular frontend application
├── src/
├── angular.json
├── package.json
└── README.md


## 🚀 Quick Start

### Prerequisites

- Node.js (v16 or higher)
- MongoDB
- npm or yarn
- Angular CLI (`npm install -g @angular/cli`)

### Installation & Setup

1. **Clone the repository**
```bash
git clone https://github.com/RaedKharrat/test-back.git
cd project
Backend Setup

bash
cd microservices

# Install dependencies for all services
npm run install:all

# Create environment file
echo "# Database
MONGO_URI=mongodb://localhost:27017/microservices_db

# Service Ports
USER_SERVICE_PORT=3001
ARTICLE_SERVICE_PORT=3002
NOTIFICATION_SERVICE_PORT=3003
GATEWAY_PORT=3000

# JWT
CLIENT_URL=http://localhost:4200

# Email (for password reset)
EMAIL_USER=noreplysteelisia@gmail.com
EMAIL_PASSWORD=kzizhlhdtndtdoey


" > .env
Frontend Setup
```
```bash

cd ../frontend
npm install
Running the Application
Start Backend Services
```
```bash
cd microservices
npm run dev:all
Start Frontend Development Server
```
```bash
cd frontend
ng serve
Access the Application
```
Frontend: http://localhost:4200

API Gateway: http://localhost:3000

Health Check: http://localhost:3000/health

🛠️ Services Details
Backend Microservices
API Gateway (Port: 3000)
Routes requests to appropriate microservices

Handles CORS and request logging

Provides health checks and service status

User Service (Port: 3001)
User registration and authentication

JWT token management

Password reset with OTP

Role-based access control (Admin, Editor, Writer, Reader)

Article Service (Port: 3002)
CRUD operations for articles

Comment system with nested replies

Article search and pagination

View counting

Notification Service (Port: 3003)
Real-time notifications via WebSocket

Comment notifications

Live updates for article interactions

Frontend Application
This project was generated using Angular CLI version 20.3.3.

Development Server
To start a local development server, run:

```bash
ng serve
```
Once the server is running, open your browser and navigate to http://localhost:4200/. The application will automatically reload whenever you modify any of the source files.

Code Scaffolding
Angular CLI includes powerful code scaffolding tools. To generate a new component, run:

```bash
ng generate component component-name
For a complete list of available schematics (such as components, directives, or pipes), run:
```
```bash
ng generate --help
```
Building
To build the project run:

```bash
ng build
```
This will compile your project and store the build artifacts in the dist/ directory. By default, the production build optimizes your application for performance and speed.



🔌 API Endpoints
Authentication
POST /api/users/signup - User registration

POST /api/users/login - User login

POST /api/users/refresh-token - Refresh access token

POST /api/users/forgot-password - Password reset request

POST /api/users/verify-otp - OTP verification

POST /api/users/reset-password - Password reset

Articles
GET /api/articles - Get all articles (paginated)

GET /api/articles/:id - Get specific article

POST /api/articles - Create article (authenticated)

PUT /api/articles/:id - Update article

DELETE /api/articles/:id - Delete article (admin only)

GET /api/articles/search?q=query - Search articles

Comments
GET /api/comments/article/:articleId - Get article comments

POST /api/comments - Add comment (authenticated)

PUT /api/comments/:id - Update comment

DELETE /api/comments/:id - Delete comment

👥 User Roles
Reader: Read articles and comments

Writer: Create and manage own articles

Editor: Edit any articles + writer permissions

Admin: Full system access + user management

🔒 Security Features
JWT-based authentication

Password hashing with bcrypt

Role-based authorization

CORS configuration

Input validation and sanitization

Rate limiting on authentication endpoints

📊 Database Models
User Model
javascript
{
  email: String,
  password: String (hashed),
  firstName: String,
  lastName: String,
  role: String, // ['Admin', 'Editor', 'Writer', 'Reader']
  refreshTokens: Array
}
Article Model
javascript
{
  title: String,
  slug: String,
  content: String,
  author: ObjectId,
  authorName: String,
  imageUrl: String,
  tags: [String],
  views: Number,
  likes: Number
}
Comment Model
javascript
{
  article: ObjectId,
  parent: ObjectId, // for nested comments
  author: ObjectId,
  authorName: String,
  content: String
}
🧪 Testing the Setup
Check backend services:

bash
curl http://localhost:3000/health
Test API endpoints:

bash
curl http://localhost:3000/api/users/test
curl http://localhost:3000/api/articles/health
Verify frontend: Navigate to http://localhost:4200

🚨 Troubleshooting
Common Issues
Port conflicts: Ensure ports 3000-3003 and 4200 are available

MongoDB connection: Verify MongoDB is running and MONGO_URI is correct

CORS issues: Check CLIENT_URL in environment variables matches frontend URL

Angular build errors: Ensure Angular CLI is installed globally

Development Tips
Backend services provide detailed console logs for debugging

Use Angular DevTools for frontend debugging

Check browser console for frontend errors

Monitor network tab for API requests

📈 Monitoring
Backend Health Checks
Gateway: http://localhost:3000/status

User Service: http://localhost:3001/health

Article Service: http://localhost:3002/health

Notification Service: http://localhost:3003/health

Frontend Development
Application: http://localhost:4200

Angular DevServer: http://localhost:4200 with hot reload



Check MongoDB connection

Additional Resources
For more information on using the Angular CLI, including detailed command references, visit the Angular CLI Overview and Command Reference page.

Built with ❤️ using Microservices Architecture & Angular
