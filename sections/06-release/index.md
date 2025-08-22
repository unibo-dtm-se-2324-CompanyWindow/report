---
title: Release
has_children: false
nav_order: 7
---

# Release

This chapter details the release strategy for the CompanyWindow application, including the choice of licensing, versioning, and the distribution process.  

## Release strategy
The release of the CompanyWindow application involves two main components: the frontend and the backend.  

- **Frontend:** The frontend, developed with React, Vite, and TypeScript, is a static web application. It will be built into a set of static files (HTML, CSS, JavaScript) that can be served by any web server.  
  - **How:** A CI/CD pipeline will be configured to automatically build and bundle the frontend code.  
  - **Where:** The static files will be deployed to a cloud hosting service (e.g., Vercel, Netlify, or an AWS S3 bucket) that can serve them efficiently to users worldwide.  

- **Backend:** The backend, built with Node.js and Express, is a server-side application responsible for handling all API requests, user authentication, and orchestrating the data analysis scripts.  
  - **How:** The backend will be packaged into a deployable container image (e.g., Docker). This ensures that the application runs consistently across different environments.  
  - **Where:** The Docker image will be deployed to a cloud platform that supports containerized applications (e.g., AWS Elastic Beanstalk, Heroku, or a Kubernetes cluster), allowing for scalability and high availability.  

Currently, the project is running locally. For setup and execution details, refer to the `artifact repository` documentation (`README.md`).  

## License  

The CompanyWindow project is released under the **MIT License**.

This license was chosen for its simplicity and permissiveness, which makes it particularly suitable for academic and research projects. It allows anyone to freely use, modify, and distribute the software with minimal restrictions, requiring only that the copyright notice and license are preserved.This choice facilitates learning, collaboration, and reuse of the project, while keeping the legal framework lightweight and easy to understand.


## Choice of the Versioning Schema  

The project follows a **Semantic Versioning (SemVer)** schema, as mentioned in the *Development* section.  

