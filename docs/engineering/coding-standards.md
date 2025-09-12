# Amivero Engineering Coding Standards

## Table of Contents
1. [General Principles](#general-principles)
2. [Git Workflow](#git-workflow)
3. [Python Standards](#python-standards)
4. [JavaScript/TypeScript Standards](#javascripttypescript-standards)
5. [Documentation](#documentation)
6. [Testing](#testing)
7. [Security](#security)

## General Principles

### Code Style
- Follow the principle of least surprise
- Write self-documenting code with meaningful names
- Keep functions small and focused (ideally < 20 lines)
- Limit line length to 88 characters (Black standard)
- Use consistent indentation (4 spaces for Python, 2 spaces for JS/TS)

### Code Organization
- Follow the project's established structure
- Keep related code together
- Separate concerns appropriately
- Avoid circular dependencies

## Git Workflow

### Branch Naming
- `feature/`: New features or enhancements
- `bugfix/`: Bug fixes
- `hotfix/`: Critical production fixes
- `chore/`: Maintenance tasks
- `docs/`: Documentation updates

Example: `feature/user-authentication`

### Commit Messages
Follow the Conventional Commits specification:
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

Types:
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation only changes
- `style`: Changes that do not affect the meaning of the code
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `perf`: A code change that improves performance
- `test`: Adding missing tests or correcting existing tests
- `chore`: Changes to the build process or auxiliary tools

Example:
```
feat(auth): add OAuth2 support for Google

- Implement Google OAuth2 authentication
- Add user session management
- Update documentation

Closes #123
```

## Python Standards

### Style
- Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/)
- Use Black for code formatting
- Use isort for import sorting
- Use type hints for all new code
- Use f-strings for string formatting (Python 3.6+)

### Naming Conventions
- Variables and functions: `snake_case`
- Classes: `PascalCase`
- Constants: `UPPER_SNAKE_CASE`
- Private members: `_private_member`
- "Protected" members: `_protected_member` (convention only)

### Imports
Group imports in the following order:
1. Standard library imports
2. Third-party imports
3. Local application/library specific imports

```python
# Standard library
import os
from typing import List, Dict

# Third-party
import pandas as pd
from fastapi import FastAPI

# Local
from .models import User
from .utils import helper_function
```

## JavaScript/TypeScript Standards

### Style
- Use Prettier for consistent formatting
- Use ESLint for linting
- Use TypeScript for all new projects
- Use ES6+ features

### Naming Conventions
- Variables and functions: `camelCase`
- Classes: `PascalCase`
- Constants: `UPPER_SNAKE_CASE`
- Private members: `privateMember` (TypeScript) or `_privateMember` (JavaScript)

### TypeScript Specifics
- Always define types/interfaces for function parameters and return values
- Use strict mode
- Prefer `interface` over `type` for object shapes
- Use generics for reusable components

## Documentation

### Inline Documentation
- Use docstrings for all public modules, classes, and functions
- Follow Google-style docstrings for Python
- Use JSDoc for JavaScript/TypeScript

### API Documentation
- Document all API endpoints with OpenAPI/Swagger
- Include example requests and responses
- Document authentication requirements
- List possible error responses

## Testing

### General Guidelines
- Write tests for all new features
- Follow the Arrange-Act-Assert pattern
- Tests should be isolated and independent
- Aim for high test coverage (>80%)

### Test Naming
- Test files should be named `test_*.py` or `*.test.ts`
- Test functions should be descriptive
- Use `@pytest.mark` for test categorization

### Test Structure
```python
def test_functionality_description():
    # Arrange
    test_data = prepare_test_data()
    
    # Act
    result = function_under_test(test_data)
    
    # Assert
    assert result.expected_property == expected_value
```

## Security

### General
- Never commit secrets or credentials
- Use environment variables for configuration
- Validate all user inputs
- Use parameterized queries to prevent SQL injection
- Implement proper authentication and authorization

### Dependencies
- Keep dependencies up to date
- Use Dependabot for security updates
- Audit dependencies regularly
- Pin versions in production

### API Security
- Use HTTPS for all communications
- Implement rate limiting
- Validate all request/response schemas
- Use proper CORS policies

## Performance

### Database
- Use indexes for frequently queried fields
- Optimize queries (use EXPLAIN ANALYZE)
- Use connection pooling
- Implement proper caching

### Application
- Use async/await for I/O-bound operations
- Implement proper error handling
- Use pagination for large datasets
- Optimize asset loading

## Code Review
- All code must be reviewed before merging to main
- At least one approval required
- Use PR templates
- Address all comments before merging

## Continuous Integration
- All tests must pass before merging
- Code coverage should not decrease
- Static analysis must pass
- Security scanning must pass
