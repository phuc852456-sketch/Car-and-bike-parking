# Car-and-bike-parking

A parking management system including a Backend API (NestJS) and an Android Mobile App (Kotlin). The system helps manage vehicle entry and exit, users, and parking operations.

## Overview

Parking System is designed to support efficient parking lot management through a mobile application and a backend system. The project consists of two main parts:

- Backend: NestJS, TypeScript
- Mobile App: Android, Kotlin

## Features

### User
- Sign up / log in
- JWT-based authentication
- Manage personal profile
- View parking lot status

### Administrator
- Manage users
- Manage parking lots
- Control vehicle entry and exit
- Manage access permissions

### Image Upload
- Upload images using Cloudinary

### Security
- JWT Authentication
- Admin Guard
- Auth Guard

## System Architecture

```text
Mobile App (Android - Kotlin)
        │
        │ REST API
        ▼
Backend (NestJS)
        │
        ▼
Database
Backend
Project Structure
src
 ├── admin
 │   ├── admin.controller.ts
 │   ├── admin.service.ts
 │   └── admin.module.ts
 │
 ├── auth
 │   ├── auth.controller.ts
 │   ├── auth.service.ts
 │   └── auth.module.ts
 │
 ├── Guard
 │   ├── jwt-auth.guard.ts
 │   └── AdminGuard.guard.ts
 │
 ├── cloudinary
 │
 ├── app.module.ts
 ├── app.controller.ts
 └── app.service.ts
Installation
1. Clone the project
git clone https://github.com/your-repo/parking-system.git
cd ParkingSystem_Backend
2. Install dependencies
npm install
3. Run the project in development mode
npm run start:dev
Default server address:
http://localhost:3000
Scripts
Command	Description
npm run start	Run the project
npm run start:dev	Run in development mode
npm run build	Build the project
npm run test	Run tests
Android App
Technologies
Kotlin
Android Studio
REST API
Project Structure
ParkingSystem-done
 ├── app
 ├── gradle
 ├── build.gradle
 └── settings.gradle
Run the Application
Open the project in Android Studio
Sync Gradle
Click Run App
Authentication
The system uses JWT tokens.
Workflow:
Login
   ↓
Server returns JWT
   ↓
Client sends JWT in the header
   ↓
Auth Guard validates the token
Example header:
Authorization: Bearer <token>
Cloudinary
Used to upload:
Vehicle images
User images
Configure the following variables in the .env file:
CLOUDINARY_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=
Testing
npm run test
Author
Huynh Thanh Phuc
Email: phuc852456@gmail.com
