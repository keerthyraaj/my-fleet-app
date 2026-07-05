# Project structure guide

This document explains the folder structure of the project and the purpose of each main file.

## Main project folder

The root folder is named my-fleet-app and it contains two main parts:

- backend/ — the server that handles login and database requests
- frontend/ — the user interface that users see in the browser

## Backend folder

The backend folder contains the server-side code.

### backend/index.js
This is the main backend file.

It does the following:
- starts the Express server
- connects to PostgreSQL
- handles the login request
- checks the password using bcrypt
- returns dashboard statistics for the logged-in user

### backend/package.json
This file lists the backend dependencies and scripts.

It tells Node.js which packages are needed, such as:
- express
- pg
- bcrypt
- cors
- dotenv

It also defines commands like npm start.

### backend/package-lock.json
This file locks the exact package versions that were installed.

It helps keep the project consistent and prevents unexpected changes when someone installs dependencies later.

### backend/.env
This file stores private environment variables.

It is used for sensitive information such as the PostgreSQL connection string.

Important:
- never share this file publicly
- never upload it to GitHub

### backend/.gitignore
This file tells Git which files should be ignored.

It prevents folders and files like:
- node_modules/
- .env

from being committed to version control.

### backend/README.md
This is a beginner-friendly explanation of the backend setup.

It helps you understand what the backend is doing and how to run it.

### backend/backend_postgresql_ddl.txt
This file contains SQL statements for creating the database tables.

It defines the structure for:
- users
- fleets
- user_fleets

## Frontend folder

The frontend folder contains the React app that users interact with.

### frontend/index.html
This is the main HTML file for the app.

It is the entry page loaded by the browser and contains the root element where React renders the UI.

### frontend/package.json
This file contains the frontend dependencies and scripts.

It includes packages such as:
- react
- react-dom
- vite

It also defines commands such as npm run dev and npm run build.

### frontend/vite.config.js
This file configures Vite, the tool used to run and build the React app.

It defines settings such as:
- the development server port
- React plugin support

### frontend/src/
This folder contains the React source code.

### frontend/src/APP.jsx
This is the main React component.

It contains:
- the login form
- the login logic
- the dashboard UI after login
- the request to the backend

### frontend/src/main.jsx
This is the entry point for React.

It mounts the App component into the HTML page so the interface appears in the browser.

### frontend/public/
This folder is used for static files.

Examples include:
- images
- icons
- favicons

These files are served directly by the app.

## Why these files matter

Each file has a specific role:

- backend files handle logic and database access
- frontend files handle what the user sees and interacts with
- configuration files tell the tools how to run and build the app
- documentation files help you understand the project later

## Simple mental model

Think of the project like this:

- the frontend is the face of the app
- the backend is the brain of the app
- the database stores the actual data

## Summary

If you are new to this project, remember:

- edit React code in the frontend folder
- edit server logic in the backend folder
- keep secrets in .env and never commit them
- use the README files when you need help understanding the project
