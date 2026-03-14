Car-and-bike-parking
A parking management system including a Backend API (NestJS) and an Android Mobile App (Kotlin). The system helps manage vehicle entry and exit, users, and parking operations.

**Table of Contents**

Overview
Features
System Architecture
Prerequisites
Installation
Configuration
Usage
API Documentation
Authentication
Testing
Contributing
License
Author
Overview

Parking System is designed to support efficient parking lot management through a mobile application and a backend system. The project consists of two main parts:

Backend: NestJS, TypeScript
Mobile App: Android, Kotlin
**Features**

User

Sign up / log in
JWT-based authentication
Manage personal profile
View parking lot status
Administrator

Manage users
Manage parking lots
Control vehicle entry and exit
Manage access permissions
Image Upload

Upload images using Cloudinary
Security

JWT Authentication
Admin Guard
Auth Guard
**System Architecture**

Code
Mobile App (Android - Kotlin)
        │
        │ REST API
        ▼
Backend (NestJS)
        │
        ▼
Database
Backend Project Structure

Code
src/
 ├── admin/
 │   ├── admin.controller.ts
 │   ├── admin.service.ts
 │   └── admin.module.ts
 │
 ├── auth/
 │   ├── auth.controller.ts
 │   ├── auth.service.ts
 │   └── auth.module.ts
 │
 ├── Guard/
 │   ├── jwt-auth.guard.ts
 │   └── AdminGuard.guard.ts
 │
 ├── cloudinary/
 │
 ├── app.module.ts
 ├── app.controller.ts
 └── app.service.ts
Mobile App Project Structure

Code
ParkingSystem-done/
 ├── app/
 ├── gradle/
 ├── build.gradle
 └── settings.gradle
**Prerequisites**

Backend

Node.js >= 16.x
npm >= 8.x
MongoDB or PostgreSQL (choose based on your setup)
Mobile App

Android Studio >= 4.0
Android SDK 21 or higher
Kotlin 1.5+
**Installation**

Backend Setup

Clone the project
bash
git clone https://github.com/phuc852456-sketch/Car-and-bike-parking.git
cd Car-and-bike-parking
Install dependencies
bash
npm install
Configure environment variables
bash
cp .env.example .env
Run the project in development mode
bash
npm run start:dev
Default server address: http://localhost:3000

Available Backend Scripts

Command	Description
npm run start	Run the project
npm run start:dev	Run in development mode with hot reload
npm run build	Build the project
npm run test	Run tests
Mobile App Setup

Open Android Studio
Open the project folder Car-and-bike-parking
Sync Gradle files (File > Sync Now)
Select a device/emulator and click Run App
**Configuration**

Environment Variables (.env)

Create a .env file in the backend root directory:

env
# Database
DATABASE_URL=mongodb://localhost:27017/parking_system
# or for PostgreSQL: DATABASE_URL=postgresql://user:password@localhost:5432/parking_system

# JWT
JWT_SECRET=your_secret_key_here
JWT_EXPIRATION=7d

# Cloudinary
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Server
PORT=3000
NODE_ENV=development
Cloudinary Setup

Create an account at Cloudinary
Get your API credentials from the dashboard
Add them to your .env file
**Usage**

Backend API

Once the server is running at http://localhost:3000, you can:

Access API endpoints for user management, parking operations, etc.
Use the JWT token in the Authorization header for authenticated requests
Mobile App

The Android app connects to the backend API and provides:

User authentication
Real-time parking status
Vehicle entry/exit management
Image uploads for vehicle and user profiles
**Authentication**

The system uses JWT (JSON Web Tokens) for authentication.

Authentication Workflow

Code
1. User Login
    ↓
2. Server validates credentials and returns JWT token
    ↓
3. Client stores JWT and sends it in request headers
    ↓
4. Auth Guard validates the token on each request
    ↓
5. Authorized request is processed
Example Request Header

Code
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
**Testing**

Run the test suite:

bash
npm run test
For test coverage:

bash
npm run test:cov
**API Documentation**

For detailed API documentation, please refer to the API endpoints:

Base URL: http://localhost:3000
Auth Endpoints: /api/auth
User Endpoints: /api/users
Admin Endpoints: /api/admin
(Consider adding Swagger/OpenAPI documentation for comprehensive API docs)

**Contributing**

Contributions are welcome! Please:

Fork the repository
Create a feature branch (git checkout -b feature/amazing-feature)
Commit your changes (git commit -m 'Add amazing feature')
Push to the branch (git push origin feature/amazing-feature)
Open a Pull Request
**License**

This project is licensed under the MIT License - see the LICENSE file for details.

**Author**

Huynh Thanh Phuc

Email: phuc852456@gmail.com
GitHub: @phuc852456-sketch
For issues, questions, or suggestions, please open an issue on GitHub or contact the author.
