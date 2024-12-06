# Shared OpenAPI Schemas

## Overview
This repository contains reusable OpenAPI schemas designed to standardize error handling and other shared components across multiple codebases. By providing a centralized library of well-defined schemas, this repository aims to improve consistency, maintainability, and collaboration in API development.

## Contents
The repository includes:
- **Standardized Error Schemas**: Definitions for common error response formats (e.g., validation errors, server errors, not found errors).
- **Predefined Components**: Reusable OpenAPI components for consistent use across APIs.
- **Documentation**: Guidance on integrating these schemas into your OpenAPI specifications and using them effectively.

## Key Features
- **Standardized Error Handling**: Ensure uniform error response structures across APIs, making integration and troubleshooting easier.
- **Reusability**: Avoid duplication of error definitions by referencing centralized schemas.
- **Consistency**: Promote consistent API design practices across all services and teams.
- **Version Control**: Manage and evolve shared schemas with clear versioning and change history.

## How to Use
1. **Reference the Schema**  
   Import and reference components from this repository in your OpenAPI definitions using `$ref`. For example:
   ```yaml
   responses:
     "400":
       $ref: "https://your-repo-url/errors-schema.yaml#/components/responses/ValidationErrorResponse"
     "500":
       $ref: "https://your-repo-url/errors-schema.yaml#/components/responses/InternalServerErrorResponse"
   ```

2. **Integrate with Your APIs**  
   Replace duplicated error definitions in your API specifications with references to this repository.

3. **Contribute**  
   Submit pull requests to propose changes or additions to the schema, ensuring alignment with the overall standard.

## Example Use Case
If an API returns a validation error, all teams can ensure it follows the same format:
```json
{
  "message": "Validation failed",
  "code": "ERR001",
  "details": [
    {
      "field": "email",
      "issue": "Email format is invalid"
    }
  ]
}
```
This structure helps developers quickly understand and address issues.

## Repository Intentions
- **Standardization**: Provide a single source of truth for shared API schemas to prevent inconsistencies.
- **Collaboration**: Enable teams to contribute and adopt best practices in API design.
- **Efficiency**: Reduce overhead by simplifying schema management and API integration.

## Getting Started
1. Clone this repository:
   ```bash
   git clone https://github.com/your-org/shared-openapi-schemas.git
   ```
2. Host the schema file (if not already hosted) or use the raw file link for `$ref`.

## Contributing
We welcome contributions! To contribute:
1. Fork the repository.
2. Create a feature branch (`feature/your-feature`).
3. Submit a pull request with detailed descriptions of your changes.
