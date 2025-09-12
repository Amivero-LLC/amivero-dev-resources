# 🛠️ Amivero Development Setup Guide

## 🔑 Access

### Request Access to Development Tools

- **Confluence & Jira**: Email [helpdesk@amivero.com](mailto:helpdesk@amivero.com)
- **GitHub**: Contact the DevOps team for repository access

## 📦 Prerequisites

Before starting any project, ensure you have the following tools installed on your development machine:

### Required

- [Python](https://www.python.org/downloads/) 3.12 or higher
- [Docker](https://www.docker.com/products/docker-desktop) (Latest version)
- [Docker Compose](https://docs.docker.com/compose/install/) (Comes with Docker Desktop)
- [AWS CLI](https://aws.amazon.com/cli/) v2 or higher
- [Git](https://git-scm.com/downloads) (Latest version)
- **IDE/Code Editor**:
  - [VS Code](https://code.visualstudio.com/) (Recommended)
  - [PyCharm](https://www.jetbrains.com/pycharm/)
  - [Sublime Text](https://www.sublimetext.com/)

### Optional

- [Postman](https://www.postman.com/downloads/) - For API testing
- [TablePlus](https://tableplus.com/) - Database management
- [DBeaver](https://dbeaver.io/) - Alternative database tool

## 🚀 Quick Start

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd <project-directory>
   ```

2. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. **Start development environment**
   ```bash
   docker-compose up -d
   ```

## 📚 Additional Resources

- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [LocalStack Documentation](https://docs.localstack.cloud/)
- [AWS CLI Documentation](https://docs.aws.amazon.com/cli/)
- [Docker Documentation](https://docs.docker.com/)
- [Git Documentation](https://git-scm.com/doc)

## 🆘 Getting Help

- For technical issues: `#engineering-support` on Slack
- For access requests: [helpdesk@amivero.com](mailto:helpdesk@amivero.com)
- For urgent matters: Contact the DevOps team on Slack
