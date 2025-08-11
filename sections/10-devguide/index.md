---
title: Developer guide
has_children: false
nav_order: 11
---

# Developer Guide

This section serves as a comprehensive guide for developers who wish to interact with the source code or the API of the **CompanyWindow** project.

## Getting Started

To begin development on the project, refer to the *Deployment* section for complete setup instructions.

For development, start both servers:
```bash
# Backend (Terminal 1)
cd server
npm run dev

# Frontend (Terminal 2)  
cd client
npm run dev
```

## API Specification

The API is accessible under the base path: **/api/v1/**. Endpoints marked with 🔐 require authentication via Bearer token: `Authorization: Bearer <JWT_TOKEN>`.

### Authentication
- `POST /api/v1/auth/register` - Register new user
- `POST /api/v1/auth/login` - Login user

### Analysis 🔐
- `GET /api/v1/analyze/:company` - Get sentiment analysis for company

### Account Management 🔐
- `GET /api/v1/account/profile` - Get user profile
- `PUT /api/v1/account/profile` - Update profile
- `PUT /api/v1/account/password` - Change password
- `DELETE /api/v1/account` - Delete account

### Saved Searches 🔐
- `POST /api/v1/saved-searches` - Save analysis result
- `GET /api/v1/saved-searches` - Get all saved searches
- `DELETE /api/v1/saved-searches/:id` - Delete saved search

### Example Usage

```javascript
// Login
const response = await fetch('/api/v1/auth/login', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    email: 'user@example.com',
    password: 'password123'
  })
});

const { token } = await response.json();

// Get analysis
const analysis = await fetch('/api/v1/analyze/Amazon', {
  headers: { 'Authorization': `Bearer ${token}` }
});
```

### Response Format

```json
// Success
{
  "success": true,
  "data": { /* response data */ }
}

// Error
{
  "success": false,
  "error": { "message": "Error description" }
}
```

## Contributing to the Project

### Testing

The project includes comprehensive testing across all components:

```bash
# Backend tests (API endpoints, controllers, models)
cd server && npm test

# Frontend tests (React components, hooks, pages)
cd client && npm test

# Python scripts tests
cd scripts && python -m pytest tests/
```

### Contribution Workflow
1. **Fork** the repository and create a feature branch
2. **Make changes** following existing code style
3. **Test locally** - Run relevant test suites above
4. **Commit** with clear message: `git commit -m "feat: add new feature"`
5. **Create Pull Request** to `develop` branch
6. **CI/CD checks** - GitHub Actions will run `check.yml`, `backend-check.yml` and `frontend-check.yml`

### Project Structure
```
CompanyWindow/
├── .github/workflows/    # CI/CD pipelines
│   ├── check.yml
│   ├── backend-check.yml
│   └── frontend-check.yml
├── server/              # Node.js backend
│   ├── controllers/     # API logic
│   ├── models/         # Database schemas
│   ├── routes/         # API endpoints
│   └── middleware/     # Auth & validation
├── client/             # React frontend
│   ├── src/components/ # UI components
│   ├── src/hooks/      # Custom React hooks
│   ├── src/pages/      # Page components
│   └── src/contexts/   # React contexts
├── scripts/            # Python analysis
│   ├── scraping/       # Data collection (Glassdoor, Indeed)
│   ├── sentiment/      # AI sentiment analysis
```

This guide provides the essential information needed to start developing with CompanyWindow.
