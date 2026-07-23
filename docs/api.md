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