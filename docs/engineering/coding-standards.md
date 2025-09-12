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
- Follow the principle of least surprise [https://en.wikipedia.org/wiki/Principle_of_least_surprise](https://en.wikipedia.org/wiki/Principle_of_least_surprise)
- Write self-documenting code with meaningful names
- Keep functions small and focused (ideally < 20 lines)
- Limit line length to 88 characters (Black standard)
- Use consistent indentation (4 spaces for Python, 2 spaces for JS/TS)

### Code Organization
- Follow the project's established structure
- Keep related code together
- Separate concerns appropriately
- Avoid circular dependencies [https://en.wikipedia.org/wiki/Circular_dependency](https://en.wikipedia.org/wiki/Circular_dependency)

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
- Use formatter for linting
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
- Never commit secrets or credentials (use environment variables or secret management)
- Validate and sanitize all user inputs
- Implement the principle of least privilege
- Use secure defaults for all configurations
- Keep security headers enabled (CSP, HSTS, XSS Protection) when appropriate

### Authentication & Authorization
- Use OAuth 2.0 with PKCE for web/mobile apps when appropriate
- Implement proper session management when appropriate
- Use JWT with appropriate expiration times when appropriate
- Implement role-based access control (RBAC) or attribute-based access control (ABAC) when appropriate
- Enforce strong password policies when appropriate

### API Security
- Use HTTPS for all communications (enforce with HSTS) when appropriate
- Implement rate limiting and request throttling when appropriate
- Validate all request/response schemas when appropriate
- Use proper CORS policies (be specific with allowed origins) when appropriate
- Implement API versioning when appropriate
- Return generic error messages to clients when appropriate

### Data Protection
- Encrypt sensitive data at rest and in transit
- Use parameterized queries to prevent SQL injection
- Implement proper data validation and sanitization
- Regular security audits and penetration testing when appropriate

### Dependencies
- Use Dependabot for security updates
- Audit dependencies regularly (OWASP Dependency-Check)
- Pin versions in production
- Remove unused dependencies
- Only use well-maintained, widely-used packages

## Error Handling & Logging

### General Principles
- Fail fast and fail visibly
- Never expose stack traces to end users
- Include unique error codes for production issues
- Log all security-relevant events

### Error Handling
- Use specific exception types
- Include context in error messages
- Implement proper error boundaries in frontend
- Use custom error types for business logic errors
- Document all possible error responses in APIs

### Logging Standards
- Use structured logging (JSON format)
- Include correlation IDs in distributed systems
- Log at appropriate levels:
  - ERROR: System failures
  - WARN: Unexpected but handled conditions
  - INFO: Important business events
  - DEBUG: Debug information
  - TRACE: Detailed execution flow
  - But dont log too much information in production because it can be computationally expensive
- Never log sensitive information (PII, credentials, tokens)
- Set up log rotation and retention policies

### Monitoring & Alerting
- Set up error tracking (Sentry, Datadog, etc.)
- Create dashboards for key metrics
- Set up alerts for critical errors
- Monitor for security events

## Code Review Process

### Review Guidelines
- All code must be reviewed before merging to main
- Use the "Approve with suggestions" option when possible
- Request changes for critical issues
- Keep PRs small and focused (300-500 lines max)

### Review Checklist
- [ ] Code follows style guidelines
- [ ] Tests are included and pass
- [ ] Documentation is updated
- [ ] Security considerations addressed
- [ ] Performance impact considered
- [ ] Error handling is appropriate
- [ ] No sensitive data exposed

### Review Etiquette
- Be respectful and constructive
- Explain the "why" behind suggestions
- Use inline comments for specific suggestions
- Keep discussions focused on the code
- Recognize good patterns as well as issues

## Testing Guidelines

### Test Types
- **Unit Tests**: Test individual functions/methods in isolation
- **Integration Tests**: Test interactions between components
- **E2E Tests**: Test complete user flows
- **Performance Tests**: Test under load
- **Security Tests**: SAST/DAST scanning

### Test Quality
- Follow the Arrange-Act-Assert pattern
- Tests should be isolated and independent
- Use meaningful test names (test_<method>_when_<condition>_then_<result>)
- Aim for high test coverage (>80%)
- Test edge cases and error conditions

### Test Data
- Use factories/fixtures for test data
- Keep tests deterministic
- Clean up test data after tests
- Use realistic test data
- Consider using test data builders

### Test Performance
- Keep tests fast (complete in seconds)
- Mock external dependencies
- Use test doubles appropriately
- Run tests in parallel when possible
- Monitor and optimize test suite performance

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
