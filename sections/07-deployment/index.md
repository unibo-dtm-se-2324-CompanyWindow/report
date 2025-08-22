---
title: Deployment
has_children: false
nav_order: 8
---

# Deployment
### System Requirements 

 

To run the CompanyWindow application, you need the following tools installed on your system: 

 

 * **Node.js**: Version 20.11 or later is required for the backend server. 

 * **Python**: Version 3.8 or later is needed for the data analysis scripts. 

* **MongoDB**: A locally installed instance of MongoDB or access to a cloud-hosted instance. 

* **Git**: To clone the project repository. 

* **npm** or **Yarn**: A package manager for the Node.js dependencies. 

* **pip**: The package manager for Python dependencies. 

 

----- 

 

### Instructions 

 

#### 1st Step: Clone the Repository 

 

The project is structured within a single repository. The first step is to clone it and navigate into the main directory. 

 

```bash 
git clone https://github.com/unibo-dtm-se-2324-CompanyWindow/artifact 
``` 

 

#### 2nd Step: Install Dependencies 

 

Navigate into the respective directories to install the required packages for both the Node.js backend/frontend and the Python scripts. 

 

```bash 
# Install Node.js dependencies for the backend 

cd server 

npm install 

cd .. 

# Install Python dependencies for the data analysis scripts 

pip install -r requirements.txt 

# Install Node.js dependencies for the frontend 

cd client 

npm install 

cd .. 
``` 


#### 3rd Step: Get Your API Keys and create a MongoDB Atlas Instance  

Before you can run the application with live data, you'll need to obtain free API keys for the scraping and sentiment analysis services. 

 

* **Scrapfly API Key**: The application uses Scrapfly for web scraping. You can get a free API key with a generous number of credits by signing up on their website. 
   * Go to the Scrapfly website. 
  * Sign up for a free account. 
  * Find your API key in the dashboard and paste it into the `SCRAPFLY_API_KEY` variable in the `.env` file. 

* **Gemini API Key**: Sentiment analysis is performed using Google Gemini. A free API key is available for a limited number of requests. 
  * Visit the Google AI Studio website. 
  * Log in with your Google account. 
  * Click on "Get API Key" to generate a new key. 
  * Copy the key and add it to the `GEMINI_API_KEY` variable in the `.env` file. 

     

* **How to Create a MongoDB Atlas Instance** 

    If you choose to use a cloud-hosted database, MongoDB Atlas is the recommended option. Here are the steps to create a free instance: 
    1.  **Sign Up**: Go to the MongoDB Atlas website and sign up for a free account. 
    2.   **Create a Project**: Once logged in, create a new project. 
    3.   **Build a Database**: Select the "Build a Database" option. Choose the "M0" plan, which is free. Select your preferred cloud provider (e.g., AWS, GCP) and a region close to you.
    4.   **Create a User**: In the "Database Access" section, create a new database user with a secure username and password. Remember these credentials, as they will be used in your `MONGODB_URI`. 
    5.  **Configure Network Access**: In the "Network Access" section, click "Add IP Address." For development purposes, you can add your current IP address or choose "Allow Access from Anywhere" (for local development, you might need to use `0.0.0.0/0`). 
    6.   **Get the Connection String**: After your cluster is deployed, go to the "Database" section and click "Connect." Select the "Connect your application" option, choose the Node.js driver, and copy the connection string. This is your `MONGODB_URI`. Make sure to replace `<username>`, `<password>`, and `<databaseName>` in the URI with your credentials. 

  

 

#### 4th Step: Configure Environment Variables 

This is a critical step for configuring both the backend and the Python scripts. Sensitive information like API keys and database credentials must be set in `.env` files. 

 

* **Backend (`./server/.env`)**: Create a `.env` file in the `./server` directory. This file will store variables for the server and database. 


``` 
NODE_ENV=development 

PORT=3000 
    MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/database_name 


# JWT Secret and Expiration 

JWT_SECRET=your_secret_jwt_key 

JWT_EXPIRE=1h 


# Configuration for Python Scripts 

USE_MOCK=true 

SCRAPFLY_API_KEY=your_scrapfly_api_key 

GEMINI_API_KEY=your_gemini_api_key 
``` 

 

* `NODE_ENV`: Use `development` for local testing. 

* `USE_MOCK`: Set to `false` to enable live scraping; otherwise, it will use mock data. 

 

#### 5th Step: Run the Application 

 

With all dependencies and environment variables configured, you can start the backend server and the frontend application in separate terminal sessions. 

 

```bash 
# In the first terminal, start the Node.js backend server 

cd server 

npm run dev #or node index.js 

# In a separate terminal, start the React development server 

cd client 

npm run dev 
``` 

 

The backend API will be available at a specific port (e.g., `http://localhost:3000`), and the frontend will be accessible via your browser (e.g., `http://localhost:5173`). 

 

  

 
 

----- 

 

### Future Deployment Strategy 

 

The instructions above are for a local development environment. The future deployment strategy is to transition the application to a production-ready state, making it directly accessible to end-users without manual setup. This will involve the following steps, as outlined in the **Release** section.  
