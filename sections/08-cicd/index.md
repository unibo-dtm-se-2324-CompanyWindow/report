---
title: CI/CD
has_children: false
nav_order: 9
---

# CI/CD

The **CompanyWindow** project implements automated code quality validation through GitHub Actions workflows. Every time code is pushed or a pull request is created, the system automatically checks for syntax errors, linting issues, and build failures across the entire technology stack.

This prevents problematic code from reaching the main branches and ensures consistent quality standards across all contributors.

## Automation Strategy

The project uses **GitHub Actions** to automatically validate code quality on every commit and pull request across all technology stacks:

**Automated Checks:**
- **Backend**: Node.js code linting and build verification (`backend-check.yml`)
- **Frontend**: TypeScript compilation and build checks (`frontend-check.yml`)  
- **Python Scripts**: Code quality and syntax validation (`check.yml`)

**Not Automated:**
- Test suite execution: it is not automated due to external service dependencies that require controlled usage. To ensure efficient resource management tests are executed manually when needed
- Deployment to production environments

## The impact of this approach

**Technical Benefits:**
- **Quality Assurance**: Prevents broken code from reaching main branches
- **Consistency**: Enforces uniform code standards across the entire stack
- **Early Detection**: Catches integration issues before they impact the team

**Process Benefits:**
- **Automated Gatekeeping**: No manual intervention needed for basic quality checks
- **Developer Confidence**: Safe to merge when all checks pass
- **Scalable Workflow**: Supports multiple developers without coordination overhead

## GitHub Actions Implementation

**Workflow Structure:**
```
.github/workflows/
├── backend-check.yml    # Node.js server validation
├── frontend-check.yml   # React client validation
└── check.yml           # Python scripts validation
```

**Execution Model:**
1. **Trigger**: Push to main/develop or pull request creation
2. **Parallel Execution**: All relevant workflows run simultaneously  
3. **Path-Based Optimization**: Only affected components are checked
4. **Fail-Fast**: Immediate feedback on first error encountered
5. **Branch Protection**: Merge blocked until all checks pass

**Key Implementation Features:**
- **Multi-Stack Coverage**: Validates Node.js, React, and Python code
- **Smart Triggering**: Path-based filters prevent unnecessary workflow runs
- **Consistent Environment**: Ubuntu latest with specified Node.js/Python versions

This ensures code quality while keeping the CI/CD pipeline simple and maintainable.
