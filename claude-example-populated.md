# Example: Populated CLAUDE.md for a Python Project

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Methodologies

This project follows two key frameworks:
- **Development Framework**: See `dev-framework.md` for implementation workflow and standards
- **Analysis Framework**: See `analysis-framework.md` for code analysis and documentation methodology

## Project Overview

UserAPI is a FastAPI-based REST API service for user management. It provides authentication, authorization, and user profile management with PostgreSQL database backend and Redis caching.

## Build and Development Commands

**Install dependencies:**
```bash
pip install -r requirements.txt
pip install -r requirements-dev.txt  # Development dependencies
```

**Run development server:**
```bash
uvicorn app.main:app --reload --port 8000
```

**Run production server:**
```bash
gunicorn app.main:app -w 4 -k uvicorn.workers.UvicornWorker
```

**Database migrations:**
```bash
alembic upgrade head  # Apply migrations
alembic revision --autogenerate -m "Description"  # Create new migration
```

**Run tests:**
```bash
pytest
pytest --cov=app  # With coverage
```

## Architecture

### Project Structure

```
user-api/
├── app/
│   ├── api/           # API endpoints
│   │   ├── auth.py    # Authentication endpoints
│   │   ├── users.py   # User management endpoints
│   │   └── health.py  # Health check endpoints
│   ├── core/          # Core functionality
│   │   ├── config.py  # Configuration management
│   │   ├── security.py # JWT and password handling
│   │   └── database.py # Database connection
│   ├── models/        # SQLAlchemy models
│   │   └── user.py    # User model
│   ├── schemas/       # Pydantic schemas
│   │   └── user.py    # User request/response schemas
│   ├── services/      # Business logic
│   │   └── user_service.py
│   └── main.py        # FastAPI application entry
├── alembic/           # Database migrations
├── tests/             # Test files
├── docker-compose.yml # Local development services
└── requirements.txt   # Python dependencies
```

### Core Components

1. **FastAPI Application** (`app/main.py`)
   - CORS middleware configuration
   - Router registration
   - Startup/shutdown events

2. **Authentication System** (`app/core/security.py`)
   - JWT token generation and validation
   - Password hashing with bcrypt
   - Token refresh mechanism

3. **Database Layer** (`app/core/database.py`)
   - SQLAlchemy async session management
   - Connection pooling
   - Transaction handling

4. **Caching Layer** (`app/services/cache.py`)
   - Redis integration for session storage
   - Cache invalidation strategies

### Technology Stack

- **Language**: Python 3.11
- **Framework**: FastAPI 0.104.0
- **Database**: PostgreSQL 15 with SQLAlchemy 2.0
- **Cache**: Redis 7.0
- **Authentication**: JWT (python-jose)
- **Testing**: pytest, pytest-asyncio
- **Documentation**: Auto-generated OpenAPI/Swagger

## Key Features

- RESTful API with automatic OpenAPI documentation
- JWT-based authentication with refresh tokens
- Role-based access control (RBAC)
- Async request handling
- Database migrations with Alembic
- Redis caching for sessions
- Comprehensive input validation
- Rate limiting per user
- Structured logging with correlation IDs

## Dependencies

**Production:**
- fastapi==0.104.0
- sqlalchemy==2.0.23
- asyncpg==0.29.0
- redis==5.0.1
- pydantic==2.5.0
- python-jose[cryptography]==3.3.0
- passlib[bcrypt]==1.7.4
- python-multipart==0.0.6

**Development:**
- pytest==7.4.3
- pytest-asyncio==0.21.1
- black==23.11.0
- ruff==0.1.5

## Configuration

**Environment Variables:**
```bash
DATABASE_URL=postgresql+asyncpg://user:pass@localhost/dbname
REDIS_URL=redis://localhost:6379
SECRET_KEY=your-secret-key-here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
REFRESH_TOKEN_EXPIRE_DAYS=7
ENVIRONMENT=development  # development, staging, production
LOG_LEVEL=INFO
```

**Configuration File:** `app/core/config.py` uses Pydantic Settings for validation

## Usage Examples

**Authentication:**
```python
# POST /api/auth/login
{
    "username": "user@example.com",
    "password": "securepassword"
}
# Returns: { "access_token": "...", "refresh_token": "...", "token_type": "bearer" }
```

**Create User:**
```python
# POST /api/users
# Headers: Authorization: Bearer <token>
{
    "email": "new@example.com",
    "full_name": "John Doe",
    "password": "password123",
    "role": "user"
}
```

**Get User Profile:**
```python
# GET /api/users/me
# Headers: Authorization: Bearer <token>
```

## Testing

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=app --cov-report=html

# Run specific test file
pytest tests/test_auth.py

# Run with verbose output
pytest -v
```

Test structure:
- Unit tests for services and utilities
- Integration tests for API endpoints
- Fixtures for database and Redis setup

## Important Notes

- **Async/Await**: All database operations must use async/await
- **Connection Pooling**: Database connections are pooled, max_connections=100
- **Rate Limiting**: 100 requests per minute per user
- **CORS**: Configure allowed origins in production
- **Security**: Never commit .env files, rotate SECRET_KEY regularly
- **Python Version**: Requires Python 3.11+ for improved async performance
- **Database Indexes**: Ensure indexes on frequently queried fields

## Documentation

- **API Documentation**: Available at `/docs` (Swagger UI) and `/redoc` (ReDoc)
- **Architecture Guide**: See `docs/ARCHITECTURE.md`
- **Deployment Guide**: See `docs/DEPLOYMENT.md`
- **API Reference**: Auto-generated at runtime via FastAPI

## Project-Specific Guidelines

- Use async/await for all I/O operations
- Follow REST naming conventions for endpoints
- Use Pydantic schemas for all request/response validation
- Implement proper error handling with HTTPException
- Write tests for all new endpoints
- Use dependency injection for database sessions
- Log all authentication attempts
- Cache user sessions in Redis with 15-minute TTL
- Use correlation IDs for request tracking
- Follow PEP 8 style guide (enforced by Black)
- Type hints required for all functions
