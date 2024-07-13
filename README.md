Swagger Boilerplate - OpenAPI 3.0
This repository contains a boilerplate for an API designed using OpenAPI 3.0. It defines endpoints and schemas for managing organisations, contents, users, and contacts.
Table of Contents
- Introduction
- Setup
- Endpoints
- Organisation
- Contents
- Users
- Contacts
- Schemas
- Contributing
Introduction
This API serves as a foundation for managing various entities such as organisations, contents (blogs or articles), users, and contact messages. It follows the OpenAPI 3.0 specification and is designed to be straightforward to integrate and extend.
Setup
# Installation
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

# Endpoint

Organisation

POST /organisation
Create a new organisation.
- **Request Body**: JSON object with the following properties:
  - `userId` (string): ID of the user creating the organisation.
  - `name` (string): Name of the organisation.
  - `address` (string): Address of the organisation.
  - `email` (string, format: email): Email address of the organisation.
  - `phone` (string): Phone number of the organisation.
  - `created_at` (string, format: date-time): Timestamp of creation.
  - `updated_at` (string, format: date-time): Timestamp of last update.
GET /organisation/{id}
Retrieve an organisation by ID.
PUT /organisation/{id}
Update an existing organisation by ID.
#### DELETE /organisation/{id}
Delete an organisation by ID.


### Content Management

#### 11. Create a Content

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

#### 12. Update a Content

**Endpoint**

```
PUT /contents/{contentId}
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

#### 13. Delete a Content

**Endpoint**

```
DELETE /contents/{contentId}
```

**Request Parameters**

- \`contentId\` (path parameter) - The ID of the content to delete.

**Responses**

- \`204 No Content\` - Content deleted successfully.
- \`404 Not Found\` - Content not found.

#### 14. Read All Content in Blog

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
    ...
  ]
  ```

#### 15. Read All Content for a Particular User

**Endpoint**

```
GET /contents/user/{userId}
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
    ...
  ]
  ```
- \`404 Not Found\` - User not found.

#### 16. Read a Content by ID

**Endpoint**

```
GET /contents/{contentId}
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




### Contents
#### GET /contents
Retrieve all contents (blogs/articles).
#### POST /contents
Create a new content (blog/article).
#### GET /content/{id}
Retrieve a content by ID.
#### PUT /content/{id}
Update a content by ID.
#### DELETE /content/{id}
Delete a content by ID.
#### GET /contents/{userId}
Retrieve all contents associated with a specific user.
### Users
#### GET /users
Retrieve all users.
#### GET /users/{id}
Retrieve a user by ID.
#### PUT /users/{id}
Update a user by ID.
#### DELETE /users/{id}
Delete a user by ID.
### Contacts
#### POST /contacts
Create a new contact message.
- **Request Body**: JSON object with the following properties:
  - `message` (string): Message content.
  - `phone` (string): Phone number of the contact.
  - `email` (string, format: email): Email address of the contact.
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
## Contributing
Contributions are welcome! Please fork this repository and submit a pull request with your improvements.
---
Feel free to adjust the sections, add more details, or include any specific setup instructions as per your project's needs. (edited) 
3:49
See sample of readMe file


