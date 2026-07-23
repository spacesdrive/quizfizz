# Register

POST /api/v1/auth/register

- Request
```
{
    "username": "ujjwal",
    "email": "ujjwal@gmail.com",
    "password": "ujjwal@123",
}
```
- Response
```
{
    "id": 1,
    "username": "ujjwal",
    "email": "ujjwal@gmail.com"
}
```

### Status Codes

- **201 Created**
  - User registered successfully.

- **400 Bad Request**
  - Missing required fields.
  - Invalid email format.
  - Password doesn't meet requirements.
  - Invalid request body.

- **409 Conflict**
  - Username already exists.
  - Email already registered.

# Login

GET /api/v1/auth/login

- Request
```
{
    "email": "ujjwal@gmail.com",
    "password": "ujjwal@123",
}
```
- Response
```
{
  "accessToken": "...",
  "refreshToken": "...",
  "user": {
    "id": 1,
    "username": "ujjwal"
  }
}
```

### Status Codes

- **200 OK**
  - Login successful

- **400 Bad Request**
  - Invalid request body
  - Missing email or password
  - Invalid email format

- **401 Unauthorized**
  - Invalid email or password

- **429 Too Many Requests**
  - Too many failed login attempts (optional)

- **500 Internal Server Error**
  - Unexpected server error


# Create Space

Creates a new space and generates a unique invite code.

## Endpoint

```http
POST /api/v1/spaces
```

## Request Headers

```http
Content-Type: application/json
Authorization: Bearer <access_token>
```

## Request Body

```json
{
  "name": "IIT Madras"
}
```

## Success Response

**Status:** `201 Created`

```json
{
  "id": 1,
  "name": "IIT Madras",
  "inviteCode": "1A3RTM"
}
```

## Status Codes

- **201 Created**
  - Space created successfully.

- **400 Bad Request**
  - Space name is missing.
  - Space name is invalid.

- **409 Conflict**
  - A space with the same name already exists.

- **401 Unauthorized**
  - User is not authenticated.

- **500 Internal Server Error**
  - Unexpected server error.


# Join Space

Joins an existing space using an invite code.

## Endpoint

```http
POST /api/v1/spaces/join
```

## Request Headers

```http
Content-Type: application/json
Authorization: Bearer <access_token>
```

## Request Body

```json
{
  "inviteCode": "1A3RTM"
}
```

## Success Response

**Status:** `200 OK`

```json
{
  "id": 1,
  "name": "IIT Madras",
  "inviteCode": "1A3RTM"
}
```

## Status Codes

- **200 OK**
  - Joined space successfully.

- **400 Bad Request**
  - Invite code is missing.
  - Invalid request body.

- **401 Unauthorized**
  - User is not authenticated.

- **404 Not Found**
  - Invalid invite code.
  - Space does not exist.

- **409 Conflict**
  - User is already a member of this space.

- **500 Internal Server Error**
  - Unexpected server error.