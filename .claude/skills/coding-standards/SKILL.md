---
name: coding-standards
description: 【Mandatory Priority Call】This skill must be called first to load coding standards before any code-related operations. Trigger conditions include but are not limited to: writing new code, modifying existing code, code review, refactoring, technology selection, architecture design. This is a mandatory requirement that must be called before executing code operations and cannot be skipped.
---

## Project Coding Standards

The following coding standards must be followed:

## Important Notice
When generating or modifying code, the following coding standards must be strictly followed. These standards are mandatory and cannot be ignored.
---

## Naming Conventions

### Variables
**Convention**: camelCase
**Description**: Variable names must use lower camelCase
**Correct Examples**: userName, isActive, totalCount
**Incorrect Examples**: user_name, is_active, TotalCount

### Constants
**Convention**: UPPER_SNAKE_CASE
**Description**: Constant names must use uppercase snake case
**Correct Examples**: MAX_SIZE, API_KEY, DEFAULT_TIMEOUT
**Incorrect Examples**: maxSize, apiKey, defaultTimeout

### Functions
**Convention**: camelCase
**Description**: Function names must use lower camelCase and should start with a verb
**Correct Examples**: getUserData, calculateTotal, isValid
**Incorrect Examples**: get_user_data, CalculateTotal, valid

### Classes
**Convention**: PascalCase
**Description**: Class names must use PascalCase (upper camelCase)
**Correct Examples**: UserService, HttpClient, DatabaseConnection
**Incorrect Examples**: userService, httpClient, database_connection

### Files
**Convention**: kebab-case
**Description**: File names should use kebab-case (hyphen-separated)
**Correct Examples**: user-service.js, http-client.ts, data-processor.py
**Incorrect Examples**: UserService.js, httpClient.ts, data_processor.py

## Formatting Standards

### Indentation
**Description**: Use 2 spaces for indentation, do not use tabs

### Quotes
**Description**: Prefer single quotes for strings, unless the string contains single quotes
**Correct Examples**: 'hello world', "it's a test"
**Incorrect Examples**: "hello world"

### Semicolons
**Description**: Semicolons are not mandatory in JavaScript/TypeScript (can be adjusted based on project requirements)

### Line Length
**Description**: Maximum 100 characters per line

## Comment Standards

### Function Comments
**Description**: Public functions and methods must have documentation comments
**Example**:
```javascript
/**
 * Get user data
 * @param {string} userId - User ID
 * @returns {Promise<User>} User object
 */
function getUserData(userId) { ... }
```

### Complex Logic Comments
**Description**: Complex business logic must have explanatory comments

### TODO Comments
**Description**: Use TODO markers for pending tasks

## Best Practices

### Error Handling
**Description**: Errors and exceptions must be handled properly, avoid empty catch blocks
**Example**:
```javascript
try {
  // code
} catch (error) {
  console.error('Error:', error)
  // appropriate error handling
}
```

### Magic Numbers
**Description**: Avoid using magic numbers, define them as constants
**Example**:
```javascript
const MAX_RETRY_COUNT = 3

for (let i = 0; i < MAX_RETRY_COUNT; i++) { ... }
```

### Function Length
**Description**: A single function should not exceed 50 lines, long functions should be split

### Single Responsibility
**Description**: Functions and classes should follow the Single Responsibility Principle, each function should do only one thing

## Security Standards

### No Hardcoded Sensitive Information
**Description**: Hardcoding passwords, API keys, and other sensitive information is prohibited
**Solution**: Use environment variables or configuration files

### Input Validation
**Description**: All external inputs must be validated to prevent injection attacks

### SQL Injection Prevention
**Description**: Use parameterized queries to prevent SQL injection

### XSS Prevention
**Description**: Escape user input to prevent XSS attacks
```

Please strictly follow the above coding standards in all code writing and modification work.
