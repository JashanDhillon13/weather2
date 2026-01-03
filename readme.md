Weather App – Serverless Web Application on GCP

A simple, cloud-native weather application built to demonstrate how a static frontend can interact with a serverless backend on Google Cloud Platform.

This project focuses on understanding real-world cloud architecture patterns such as static hosting, HTTP-based serverless APIs, and clean separation between frontend and backend.

Live Demo

The application is deployed and publicly accessible:

Frontend: Hosted on Google Cloud Storage (static website)
Backend: Deployed on Google Cloud Run

Anyone with the frontend URL can use the application to fetch weather data.

Architecture Overview


User (Browser)
    ↓
Static Frontend (Cloud Storage)
    ↓  HTTP Request (fetch)
Cloud Run Service (Serverless Backend)
    ↓
External Weather API
    ↓
Cloud Run Response (JSON)
    ↓
Frontend UI Update


The frontend and backend are fully decoupled and communicate only via HTTP.



Frontend
Single-page static application (HTML, CSS, JavaScript)
Developed locally using VS Code
Uses JavaScript fetch() to call the backend API
Deployed to a public Google Cloud Storage bucket configured for static website hosting

The frontend contains no backend logic or API credentials and acts purely as the user interface.
Backend (Cloud Run)

Deployed as a serverless Cloud Run service
Exposes an HTTP endpoint
Executes only when invoked
Scales automatically based on incoming requests

Backend responsibilities:

1. Accepts a city name as a query parameter
2. Calls an external weather API to resolve location and fetch weather data
3. Processes and formats the response
4. Returns a clean JSON response to the frontend

The backend does not store state and does not serve frontend files.

End-to-End Flow

1. User opens the frontend URL
2. Enters a city name and clicks Get Weather
3. Frontend sends an HTTP request to the Cloud Run endpoint
4. Cloud Run fetches data from the external weather API
5. Weather data is returned as JSON
6. Frontend updates the UI dynamically

Each button click results in a new backend invocation.
Why This Architecture

Static hosting for simplicity, performance, and low cost
Serverless backend to avoid infrastructure management
Clear separation of concerns between UI and business logic
Production-style design commonly used in real applications
Key Learnings

Hosting static websites on Google Cloud Storage
Invoking Cloud Run services via HTTP
Frontend–backend communication using `fetch()`
Serverless execution and auto-scaling behavior
Structuring small but realistic cloud-native projects

Tech Stack
HTML, CSS, JavaScript
Google Cloud Storage (Static Website Hosting)
Google Cloud Run
External Weather API



Possible Enhancements

Input validation and improved error handling
Backend security using IAM or API Gateway
Caching responses to reduce external API calls
Improved UI/UX
CI/CD pipeline for automated deployments



Current Status

Frontend successfully hosted on Cloud Storage
Backend deployed and functioning on Cloud Run
Weather data fetched and displayed correctly from the hosted frontend



Conclusion

This project serves as a practical example of building and deploying a serverless web application on GCP. It prioritizes clarity, architecture, and correct cloud usage over complexity, making it a solid foundation for more advanced projects.
