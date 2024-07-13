# Team Fenom Boilerplate
This repository contains a boilerplate for an API designed using OpenAPI 3.0. It defines endpoints and schemas for managing organisations, contents, users, and contacts.

## Table of Contents
- [Introduction](#introduction)
- [Setup](#setup)
- [Endpoints](#endpoints)
  - [Authentication](#authentication)
  - [Users](#users)
  - [Organisation](#organisation)
  - [Content](#content)
  - [Contact Us](#contact)
- [Schemas](#schemas)
- [Contributing](#contribution)
  
## Introduction
This API serves as a foundation for managing various entities such as organisations, contents (blogs or articles), users, and contact messages. It follows the OpenAPI 3.0 specification and is designed to be straightforward to integrate and extend.

https://drawsql.app/teams/nana-papi/diagrams/team-fenom

## Setup
To set up this project locally, follow these steps:

1. Clone the repository:
```
git clone https://github.com/Shabzynana/UserOrgApi.git
cd UserOrgApi
```

2. Install dependencies:
```
npm install
```
3. Start the server:
```
npm start
```


## Endpoints

### Authentication

#### 1. Register a New User

**Endpoint**

```
POST /auth/register
```

**Request Body**

```json
{
  "first_name": "John",
  "last_name": "Doe",
  "username": "johndoe24",
  "email": "user@example.com",
  "password": "password123",
}
```

**Responses**

- \`201 Created\` - User successfully registered.
- \`400 Bad Request\` - Missing or invalid fields.

#### 2. Login a User

**Endpoint**

```
POST /auth/login
```

**Request Body**

```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Responses**

- \`200 OK\` - Login successful. Returns a token.
  ```json
  {
    "token": "your-jwt-token"
  }
  ```
- \`401 Unauthorized\` - Invalid credentials.

#### 3. Logout a User

**Endpoint**

```
POST /auth/logout
```

**Responses**

- \`200 OK\` - Logout successful.

#### 4. Verify Email

**Endpoint**

```
POST /auth/verify-email
```

**Request Body**

```json
{
  "email": "user@example.com",
  "verification_code": "123456"
}
```

**Responses**

- \`200 OK\` - Email verified successfully.
- \`400 Bad Request\` - Missing or invalid fields.
- \`404 Not Found\` - User not found.

#### 5. Request Password Reset

**Endpoint**

```
POST /auth/request-reset-password
```

**Request Body**

```json
{
  "email": "user@example.com"
}
```

**Responses**

- \`200 OK\` - Password reset request successful.
- \`404 Not Found\` - User not found.

#### 6. Reset Password

**Endpoint**

```
POST /auth/reset-password
```

**Request Body**

```json
{
  "email": "user@example.com",
  "reset_token": "your-reset-token",
  "new_password": "newpassword123"
}
```

**Responses**

- \`200 OK\` - Password reset successful.
- \`400 Bad Request\` - Missing or invalid fields.
- \`404 Not Found\` - User not found.


### Users

#### 7. Update a User

**Endpoint**

```
PUT /users/{id}
```

**Request Parameters**

- \`id\` (path parameter) - The ID of the user to update.

**Request Body**

```json
{
  "first_name": "John",
  "last_name": "Doe",
  "username": "johndoe24"
  "email": "user@example.com",
  "password": "newpassword123",
  "profile_picture": "url/to/profile/picture",
  "role": "user",
  "isverified": true
}
```

**Responses**

- \`200 OK\` - User updated successfully.
- \`400 Bad Request\` - Missing or invalid fields.
- \`404 Not Found\` - User not found.

#### 8. Delete a User

**Endpoint**

```
DELETE /users/{id}
```

**Request Parameters**

- \`id\` (path parameter) - The ID of the user to delete.

**Responses**

- \`204 No Content\` - User deleted successfully.
- \`404 Not Found\` - User not found.

#### 9. Read All Users

**Endpoint**

```
GET /users
```

**Responses**

- \`200 OK\` - Returns a list of users.
  ```json
  [
    {
      "id": 1,
      "email": "user1@example.com",
      "first_name": "John",
      "last_name": "Doe",
      "profile_picture": "url/to/profile/picture",
      "role": "user",
      "isverified": true,
      "created_at": "2023-01-01T00:00:00Z",
      "updated_at": "2023-01-01T00:00:00Z"
    },
  ]
  ```

#### 10. Read a User by ID

**Endpoint**

```
GET /users/{id}
```

**Request Parameters**

- \`id\` (path parameter) - The ID of the user to retrieve.

**Responses**

- \`200 OK\` - Returns the user details.
  ```json
  {
    "id": 1,
    "email": "user@example.com",
    "first_name": "John",
    "last_name": "Doe",
    "profile_picture": "url/to/profile/picture",
    "role": "user",
    "isverified": true,
    "created_at": "2023-01-01T00:00:00Z",
    "updated_at": "2023-01-01T00:00:00Z"
  }
  ```
- \`404 Not Found\` - User not found.


## Organisation

#### 11. Create an Organisation

**Endpoint**

```
POST /organisations
```

**Request Body**

```json
{
  "name": "Organisation Name",
  "address": "123 Main St",
  "email": "contact@organisation.com",
  "phone": "123-456-7890"
}
```

**Responses**

- \`201 Created\` - Organisation successfully created.
- \`400 Bad Request\` - Missing or invalid fields.

#### 12. Update an Organisation

**Endpoint**

```
PUT /organisations/{id}
```

**Request Parameters**

- \`id\` (path parameter) - The ID of the organisation to update.

**Request Body**

```json
{
  "name": "Updated Organisation Name",
  "address": "123 Main St, Suite 200",
  "email": "newcontact@organisation.com",
  "phone": "098-765-4321"
}
```

**Responses**

- \`200 OK\` - Organisation updated successfully.
- \`400 Bad Request\` - Missing or invalid fields.
- \`404 Not Found\` - Organisation not found.

#### 13. Delete an Organisation

**Endpoint**

```
DELETE /organisations/{id}
```

**Request Parameters**

- \`id\` (path parameter) - The ID of the organisation to delete.

**Responses**

- \`204 No Content\` - Organisation deleted successfully.
- \`404 Not Found\` - Organisation not found.

#### 14. Read an Organisation by ID

**Endpoint**

```
GET /organisations/{id}
```

**Request Parameters**

- \`id\` (path parameter) - The ID of the organisation to retrieve.

**Responses**

- \`200 OK\` - Returns the organisation details.
  ```json
  {
    "id": 1,
    "name": "Organisation Name",
    "address": "123 Main St",
    "email": "contact@organisation.com",
    "phone": "123-456-7890",
    "created_at": "2023-01-01T00:00:00Z",
    "updated_at": "2023-01-01T00:00:00Z"
  }
  ```
- \`404 Not Found\` - Organisation not found.


## Content

#### 15. Create a Content

**Endpoint**

```
POST /contents
```

**Request Body**

```json
{
  "userId": 1,
  "title": "Content Title",
  "description": "Content Description"
}
```

**Responses**

- \`201 Created\` - Content created successfully.
- \`400 Bad Request\` - Missing or invalid fields.

#### 16. Update a Content

**Endpoint**

```
PUT /contents/{id}
```

**Request Parameters**

- \`contentId\` (path parameter) - The ID of the content to update.

**Request Body**

```json
{
  "title": "Updated Title",
  "description": "Updated Description"
}
```

**Responses**

- \`200 OK\` - Content updated successfully.
- \`400 Bad Request\` - Missing or invalid fields.
- \`404 Not Found\` - Content not found.

#### 17. Delete a Content

**Endpoint**

```
DELETE /contents/{id}
```

**Request Parameters**

- \`id\` (path parameter) - The ID of the content to delete.

**Responses**

- \`204 No Content\` - Content deleted successfully.
- \`404 Not Found\` - Content not found.

#### 18. Read All Content in Blog

**Endpoint**

```
GET /contents
```

**Responses**

- \`200 OK\` - Returns a list of all content.
  ```json
  [
    {
      "contentId": 1,
      "userId": 1,
      "title": "Content Title",
      "description": "Content Description"
    },
  ]
  ```

#### 19. Read All Content for a Particular User

**Endpoint**

```
GET /contents/{userId}
```

**Request Parameters**

- \`userId\` (path parameter) - The ID of the user to retrieve content for.

**Responses**

- \`200 OK\` - Returns a list of content for the specified user.
  ```json
  [
    {
      "contentId": 1,
      "userId": 1,
      "title": "Content Title",
      "description": "Content Description"
    },
  ]
  ```
- \`404 Not Found\` - User not found.

#### 20. Read a Content by ID

**Endpoint**

```
GET /contents/{id}
```

**Request Parameters**

- \`contentId\` (path parameter) - The ID of the content to retrieve.

**Responses**

- \`200 OK\` - Returns the content details.
  ```json
  {
    "contentId": 1,
    "userId": 1,
    "title": "Content Title",
    "description": "Content Description"
  }
  ```
- \`404 Not Found\` - Content not found.


## Contact

#### 21. Create a Contant Us message

**Endpoint**

```
POST /contacts
```

**Request Body**

```json
{
  "id": 1,
  "message": "I want to have a meeting wth you",
  "phone": "12345678"
  "email": "example@example.com"
}
```

**Responses**

- \`201 Created\` - Contact created successfully.
- \`400 Bad Request\` - Missing or invalid fields.


## Security
This API uses API key authentication (`ApiKeyAuth`) via the `authorization` header.

## Schemas

### Organisation

Defines the schema for an organisation object, including `id`, `userId`, `name`, `address`, `email`, `phone`, `created_at`, and `updated_at`.

### Other Schemas

- `contents_body`: Schema for creating/updating content.
- `inline_response_200`, `inline_response_200_1`: Response schemas for various endpoints.
- `contact`: Schema for creating a contact message.
- `users_id_body`: Schema for updating a user.

## Contribution

### Contributions are welcome!


Feel free to adjust the sections, add more details, or include any specific setup instructions as per your project's needs.


