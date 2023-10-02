# Bookmark Application - NestJS Project
This is a NestJS project for a simple bookmark management application. It allows users to sign up, sign in, create, edit, and delete bookmarks. The project uses Prisma as the ORM for database operations and JWT for authentication. Below is how to get started and an overview of the project's file structure and functionalities.

## Getting Started
1. Clone the repository:

`git clone <repository_url>`

2. Install dependencies:

`cd <project_directory>`
`yarn install`

3. Configure environment variables:
* Create a .env file for development and a .env.test file for testing.
* Define the DATABASE_URL and JWT_SECRET variables in both files.

4. Start the development database (PostgreSQL) using Docker Compose:
* yarn db:

## File Structure
### Prisma Schema (../prisma/schema.prisma)
* This file defines the database schema using Prisma DSL.
* It specifies the data models (User and Bookmark) and their relationships.
* Prisma is a powerful tool for database management and is used to interact with the PostgreSQL database.
### Custom Decorators (../src/auth/decorator/get-user.decorator.ts)
* This file contains a custom decorator @GetUser, which retrieves user information from the request object.
* It is used to access user details in the controllers.
### Auth Module (../src/auth)
* Decorator Export (../src/auth/decorator/index.ts)
* This file exports the @GetUser decorator to make it accessible in other parts of the application.
#### Data Transfer Object (../src/auth/dto/auth.dto.ts)
* This file defines the data transfer object (DTO) for user authentication.
* It specifies validation rules for email and password fields.
#### DTO Export (../src/auth/dto/index.ts)
* This file exports the authentication DTO for use in other parts of the application.
#### Guard Export (../src/auth/guard/index.ts)
* This file exports the JWT authentication guard for use in other parts of the application.
#### JWT Guard (../src/auth/guard/jwt.guard.ts)
* This file contains a custom JWT authentication guard.
* It is used to protect routes that require authentication using JWT tokens.
#### Strategy Export (../src/auth/strategy/index.ts)
* This file exports the JWT authentication strategy for use in other parts of the application.
#### JWT Strategy (../src/auth/strategy/jwt.strategy.ts)
* This file defines the JWT authentication strategy.
* It validates JWT tokens and retrieves user information from the database.
#### Auth Controller (../src/auth/auth.controller.ts)
* This file defines the authentication controller, including signup and signin routes.
#### Auth Module (../src/auth/auth.module.ts)
* This file defines the authentication module, including controller and provider registration.
#### Auth Service (../src/auth/auth.service.ts)
* This file contains the business logic for user authentication, signup, and signin.
* It interacts with the Prisma service to perform database operations.
### Bookmark Module (../src/bookmark)
#### Data Transfer Objects (../src/bookmark/dto)
* This directory contains DTOs for creating and editing bookmarks.
#### Bookmark Controller (../src/bookmark/bookmark.controller.ts)
* This file defines the bookmark controller, including routes for creating, editing, and deleting bookmarks.
#### Bookmark Module (../src/bookmark/bookmark.module.ts)
* This file defines the bookmark module, including controller and service registration.
#### Bookmark Service (../src/bookmark/bookmark.service.ts)
* This file contains the business logic for bookmark management, including CRUD operations.
### Prisma Service (../src/prisma)
#### Prisma Module (../src/prisma/prisma.module.ts)
* This file defines the Prisma module, which provides the Prisma client as a singleton service.
#### Prisma Service (../src/prisma/prisma.service.ts)
* This file contains the Prisma service, which initializes the Prisma client and provides methods for interacting with the database.
* It also includes a method to clean the database for testing purposes.
### User Module (../src/user)
#### Data Transfer Object (../src/user/dto/edit-user.dto.ts)
* This file defines the DTO for editing user profile information.
#### DTO Export (../src/user/dto/index.ts)
* This file exports the user DTO for use in other parts of the application.
#### User Controller (../src/user/user.controller.ts)
* This file defines the user controller, including routes for retrieving user information and editing profiles.
#### User Module (../src/user/user.module.ts)
* This file defines the user module, including controller and service registration.
#### User Service (../src/user/user.service.ts)
* This file contains the business logic for editing user profiles.
* It interacts with the Prisma service to update user data.
### Main Application (../src/app.module.ts)
* This file defines the main application module, including the registration of all modules used in the application.
* It also includes global validation pipe setup.
### Entry Point (../src/main.ts)
* This file serves as the entry point of the application.
* It creates the NestJS application, sets up global validation pipes, and starts the server.
### End-to-End Tests (test/app.e2e-spec.ts)
* This file contains end-to-end tests using Jest and Pactum for the entire application.
* It tests routes related to authentication, user management, and bookmark management.
### Jest E2E Configuration (test/jest-e2e.json)
* This file specifies the configuration for Jest end-to-end testing.
### Environment Configuration (.env and .env.test)
* These files contain environment variables for configuring the database connection and JWT secret.
* .env is used for development, and .env.test is used for testing.
### ESLint Configuration (.eslintrc.js)
* This file contains ESLint configuration rules for the project.
### Docker Compose (docker-compose.yml)
* This file defines Docker Compose services for development and testing databases (PostgreSQL).
### Package.json (package.json)
* This file contains project dependencies, scripts for building, running, and testing the application.
### Nest CLI Configuration (nest-cli.json)
* This file specifies the configuration for the Nest CLI.
### TypeScript Build Configuration (ts.build.json)
* This file extends the TypeScript configuration for building the application.
### TypeScript Configuration (tsconfig.json)
* This file contains TypeScript compiler options for the project.