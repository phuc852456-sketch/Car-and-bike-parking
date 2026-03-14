# Parking Lot Management System

**Car-and-bike-parking** is a modern parking lot management solution that includes a Backend API built with NestJS and an Android mobile application developed in Kotlin. The system provides comprehensive features for managing vehicle entry and exit, users, and parking lot operations.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [System Architecture](#system-architecture)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Authentication](#authentication)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Overview

The parking lot management system is designed to support efficient parking operations through a mobile application and a robust backend system. The project consists of two main components:

- **Backend**: NestJS + TypeScript
- **Mobile Application**: Android + Kotlin

## Features

### User
- Sign up / Log in
- JWT-based authentication
- Manage personal profile
- View parking lot status

### Administrator
- Manage users
- Manage parking lots
- Control vehicle entry and exit
- Manage access permissions

### Image Upload
- Supports image upload via Cloudinary

### Security
- JWT authentication
- Admin Guard
- Auth Guard

## System Architecture

```text
   Mobile Application (Android - Kotlin)
            |
            | REST API
            v
   Backend (NestJS)
            |
            v
   Database
Backend Structure
src/
├── admin/                    # Administrator management
│   ├── admin.controller.ts
│   ├── admin.service.ts
│   └── admin.module.ts
├── auth/                     # Authentication & authorization
│   ├── auth.controller.ts
│   ├── auth.service.ts
│   └── auth.module.ts
├── guard/                    # Guards
│   ├── jwt-auth.guard.ts
│   └── admin.guard.ts
├── cloudinary/               # Cloudinary integration
├── app.module.ts
├── app.controller.ts
└── app.service.ts
Mobile Application Structure
ParkingSystem-done/
├── app/
├── gradle/
├── build.gradle
└── settings.gradle
Requirements
Backend
Node.js >= 16.x
npm >= 8.x
MongoDB or PostgreSQL
Mobile Application
Android Studio >= 4.0
Android SDK 21+
Kotlin 1.5+
Installation
Backend
Clone the repository
git clone https://github.com/phuc852456-sketch/Car-and-bike-parking.git
cd Car-and-bike-parking
Install dependencies
npm install
Set up environment variables
cp .env.example .env
Run in development mode
npm run start:dev
Default server: http://localhost:3000
Backend Commands
Command	Description
npm run start	Run the project
npm run start:dev	Run in development mode (hot reload)
npm run build	Build the project
npm run test	Run tests
Mobile Application
Open Android Studio
Open the Car-and-bike-parking project folder
Sync Gradle files (File > Sync Now)
Select a device/emulator and click Run App
Configuration
Environment Variables (.env)
Create a .env file in the backend root directory:
# Database
DATABASE_URL=mongodb://localhost:27017/parking_system
# Or PostgreSQL: DATABASE_URL=postgresql://user:password@localhost:5432/parking_system

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
Cloudinary Configuration
Create an account on Cloudinary
Get your API credentials from the dashboard
Add them to the .env file
Usage
Backend API
When the server is running at http://localhost:3000:
Access the API endpoints for user management, parking operations, and more
Use the JWT token in the Authorization header for authenticated requests
Mobile Application
The Android application connects to the Backend API and provides:
User authentication
Real-time parking lot status
Vehicle entry and exit management
Uploading vehicle images and user profile pictures
Authentication
The system uses JWT (JSON Web Tokens) for authentication.
Authentication Flow
1. User logs in
   |
   v
2. Server validates credentials and returns a JWT token
   |
   v
3. Client stores the JWT and sends it in request headers
   |
   v
4. Auth Guard validates the token on each request
   |
   v
5. Authorized requests are processed
Example Request Header
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
Testing
Run the test suite:
npm run test
Check test coverage:
npm run test:cov
API Documentation
Base URL: http://localhost:3000
Auth Endpoints: /api/auth
User Endpoints: /api/users
Admin Endpoints: /api/admin
Note: Consider adding Swagger/OpenAPI for more comprehensive API documentation.
Contributing
Contributions are welcome. Please follow these steps:
Fork the repository
Create a feature branch (git checkout -b feature/amazing-feature)
Commit your changes (git commit -m 'Add amazing feature')
Push to the branch (git push origin feature/amazing-feature)
Open a Pull Request
License
This project is licensed under the MIT License. See the LICENSE file for details.
Author
Huynh Thanh Phuc
Email: phuc852456@gmail.com
GitHub: @phuc852456-sketch
If you have any issues, questions, or suggestions, please open an issue on GitHub or contact the author.
