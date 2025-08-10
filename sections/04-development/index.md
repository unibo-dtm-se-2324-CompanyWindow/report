---
title: Development
has_children: false
nav_order: 5
---

# Development Process

This section details the development process of the **CompanyWindow** project, outlining our strategy for version control, collaboration, and key implementation decisions.  

The initial phase focused heavily on documenting the project, leading to a **documentation-centric workflow**. As we transitioned to code implementation, we established a more robust and professional development strategy.

---
### Distributed Version Control System (DVCS)

Our project utilized **Git** as its Distributed Version Control System.  
This choice enabled a collaborative environment while maintaining a structured and clear history of the project's evolution.

---

### Branch Strategy

The project follows a branching strategy inspired by **Git Flow**, designed to separate stable, release-ready code from active development.  
This was a significant evolution from our initial process of committing directly to the `main` branch for documentation updates.

- **main branch**: Contains only production-ready code that has been thoroughly tested.  
- **develop branch**: Main integration branch where new features and bug fixes are aggregated before merging into `main`. Serves as the primary collaboration point.  
- **feature/[feature-name] branches**: Dedicated branches for new features, forked from `develop`. All development starts here, and completed work is merged back into `develop` before release.  

This structured workflow mandates that **all new work is reviewed and tested via a Pull Request (PR)** before merging into `develop`, ensuring code quality and stability.

---

### Merge Management

All merges are handled through **Pull Requests** to guarantee:
- Code review before integration  
- A clear commit history  
- Automated checks (tests, linting) before approval  

During development, we also created **intermediate merges** in a safe environment to test and verify the code before final integration.

---

### Commit Conventions

We adopted the **Conventional Commits** specification to maintain a consistent and machine-readable commit history.  
Format: `<type>(<scope>): <description>`

- **feat**: New features  
  > e.g., `feat: gemini AI integration added for automatic synthesis of company reviews`  
- **fix**: Bug fixes  
  > e.g., `fix: resolve UnicodeDecodeError by adding 'latin-1' encoding`  
- **docs**: Documentation-only changes  
  > Primary commit type in early stages, especially for the repository report.  
- **refactor**: Code refactoring  
  > e.g., `refactor: streamline code, remove redundancies`  
- **test**: Adding or improving tests  
- **chore**: Build processes or other maintenance tasks  

This convention proved crucial for differentiating between documentation updates and code changes, enabling **automation of the release process**.

---

### Versioning and Automation

The project adheres to **Semantic Versioning (SemVer)**.  
Our goal was to have version numbers **automatically calculated and updated** via a CI/CD pipeline based on commit history.  

The intended workflow involved **semantic-release**, which would:
- Increase **PATCH** version for `fix` commits.  
- Increase **MINOR** version for `feat` commits.  
- Generate an updated `CHANGELOG.md`.  
- Create a new Git tag and GitHub Release.  

This automated process would remove manual version management and provide a **clear, traceable evolution of the software**.  

> ⚠️ Due to project constraints, full automation was not implemented, but remains the intended strategy.

</br>

# Implementation details

At the core of this architecture is a central orchestrator module that coordinates the entire data processing pipeline, from data acquisition to sentiment analysis, and delivers results back to the user in an efficient and structured manner.

When a user submits a company name in the search bar, the backend initiates a single Python script: **`company_orchestrator.py`**. This module acts as the central control for the entire data pipeline.

The orchestrator's function is to manage a series of sequential and parallel tasks:

1. **Scraping** – It first launches the web scraping scripts to collect reviews from sources like *Indeed* and *Glassdoor*.  
2. **Analysis** – After the raw data is gathered, the orchestrator passes it to the **`sentiment.py`** script for sentiment analysis.  
3. **Consolidation** – Finally, it takes the processed results, prepares them for the frontend, and sends the response back to the user.  

We chose this design to make the system **highly modular and resilient**. 
By centralizing the flow in the orchestrator, we ensure that each sub-script (for scraping or analysis) has a **single, well-defined responsibility**. This makes the code easier to maintain and test.  

For example, if a new data source needs to be added, only the orchestrator needs to be updated to launch an additional scraping script, without changing the core sentiment analysis logic. This architectural choice reflects our commitment to **robust and scalable software design**.

