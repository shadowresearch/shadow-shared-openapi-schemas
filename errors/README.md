# Standardized Error Schema

## Overview

The **Standardized Error Schema** repository provides a reusable OpenAPI schema that standardizes error responses across APIs and services. By defining a consistent structure for error reporting, this schema improves the quality of communication between teams and streamlines error handling across all services.

This schema is designed to unify error responses, including HTTP status codes, error types, reasons, domains, metadata, and detailed messages. It promotes consistency in error reporting, making it easier to troubleshoot and integrate with different APIs.

## Key Features

- **Standardized Error Format**: The schema defines a common structure for error responses, including details such as:
  - **Error Type**: Enumerated values like `INTERNAL_API_ERROR`, `INVALID_REQUEST_ERROR`, `AUTHENTICATION_ERROR`.
  - **Error Reason**: A unique error reason in `UPPER_SNAKE_CASE`, providing clarity and consistency in error identification.
  - **URL**: The endpoint path that generated the error, helping to identify the specific service or resource.
  - **Metadata**: Additional context, such as rate limits or service-specific data, to aid in error diagnosis.
  - **Details**: Detailed error messages and optional additional information, ensuring that developers can easily understand the cause of the issue.

- **Authentication Errors**: The schema includes specialized error handling for unauthenticated requests, ensuring that authentication-related issues are reported consistently.

- **Clear Structure**: The error structure is designed for easy consumption by other APIs and services, reducing redundancy and promoting best practices in error handling.

## Schema Components

The **Error** schema defines the core structure for error responses, and includes the following properties:

- `errorType`: A string value representing the general error type, formatted in UPPER_SNAKE_CASE (e.g., `INTERNAL_API_ERROR`, `AUTHENTICATION_ERROR`).
- `reason`: A string value that explains the specific reason for the error, formatted in UPPER_SNAKE_CASE (e.g., `INVALID_REQUEST_ERROR`).
- `url`: The URL or endpoint path where the error occurred. This can include the service domain or a specific API endpoint (e.g., `/v1/users/{userId}/update`).
- `metadata`: A set of key-value pairs providing additional context for the error, such as rate limits or detailed information about the failure.
- `details`: A set of detailed messages that provide more information about the error. At least the `message` field is required, and optionally, additional information can be provided.

## Example Use Case

When an unauthenticated request is made to an API, the error response will be structured as follows:

```json
{
  "errorType": "AUTHENTICATION_ERROR",
  "reason": "UNAUTHORIZED",
  "url": "/v1/users/{userId}/update",
  "metadata": {
    "retryAfter": "30"
  },
  "details": {
    "message": "Authentication credentials were missing or invalid."
  }
}
```
