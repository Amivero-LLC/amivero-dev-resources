# Development Environment Setup

## Prerequisites
- Python 3.9+
- Node.js 16+
- Docker 20.10+
- Git 2.30+
- Python Virtual Environment (recommended)

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/Amivero-LLC/amivero-dev-resources.git
cd amivero-dev-resources
```

### 2. Set Up Python Environment
```bash
# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 3. Install Pre-commit Hooks
```bash
pip install pre-commit
pre-commit install
```

### 4. Environment Variables
Create a `.env` file in the project root:
```env
# Application Settings
ENVIRONMENT=development
DEBUG=True
SECRET_KEY=your-secret-key-here

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/amivero_dev

# API Keys (if needed)
# OPENAI_API_KEY=your-api-key
```

## Development Workflow

### Running Tests
```bash
# Run all tests
pytest

# Run specific test file
pytest tests/test_module.py

# Run with coverage
pytest --cov=src tests/
```

### Code Formatting
```bash
# Auto-format Python code
black .

# Sort imports
isort .

# Check for style issues
flake8
```

### Pre-commit Checks
```bash
# Run all pre-commit checks
pre-commit run --all-files
```

## IDE Setup

### VS Code
Recommended extensions:
- Python
- Pylance
- Prettier
- ESLint
- Docker
- GitLens

### PyCharm
- Enable Black and isort as external tools
- Configure Python interpreter to use the virtual environment
- Enable ESLint and Prettier for frontend code

## Troubleshooting

### Common Issues
1. **Dependency Conflicts**:
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt --no-cache-dir
   ```

2. **Database Connection Issues**:
   - Verify database service is running
   - Check `.env` file for correct credentials
   - Run database migrations if needed

3. **Frontend Build Issues**:
   ```bash
   cd frontend
   npm install
   npm run build
   ```

## Getting Help
- Check the [FAQ](#) (coming soon)
- Open an issue in the repository
- Join our [Slack channel](#) (internal link)
- Contact the engineering team at engineering@amivero.com
