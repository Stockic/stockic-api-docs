# Introduction
Welcome to the official documentation for our project. This documentation covers all major aspects of the project, including API specifications for both V2 and V3.

---

# API V2 Overview
API V2 is the second version of our API, offering enhanced performance and new features.

- **Endpoints**: Detailed descriptions of available API endpoints.
- **Authentication**: Information on how to authenticate with the API.

---

# API V2 Endpoints
## GET /v2/users
Retrieve a list of users.

**Request:**
```bash
GET /v2/users
```

**Response:**
```json
[
  {"id": 1, "name": "John Doe"},
  {"id": 2, "name": "Jane Smith"}
]
```

## POST /v2/users
Create a new user.

**Request:**
```bash
POST /v2/users
{
  "name": "New User"
}
```

**Response:**
```json
{"id": 3, "name": "New User"}
```
---
