# API Specification Template

## Overview

- Purpose of the API
- Primary consumers
- Authentication model

## Base URL

- Production:
- Staging:
- Local:

## Authentication

- Scheme (Bearer token, API key, etc.)
- Required scopes/roles

## Endpoints

### Endpoint Name

**Method:** GET/POST/PUT/PATCH/DELETE

**Path:** /v1/example

**Description:**

**Request Headers:**
- Authorization: Bearer <token>
- Content-Type: application/json

**Request Body:**
```json
{}
```

**Response (200):**
```json
{}
```

**Error Responses:**
- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 500: Internal Server Error

## Rate Limits

- Requests per minute:
- Burst limit:

## Data Models

### Model Name

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| id | string | Yes | Unique identifier |

## Notes

- Any special behavior or constraints
