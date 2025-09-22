# Technical Overview: AI Ticketing System  

This document provides a simplified technical blueprint for building a prototype of the AI-Powered IT Ticketing System, tailored for a hackathon environment. The focus is on rapid development and demonstrating core functionality.

### **1. System Architecture: Monolithic Server**

For a hackathon, we will use a **Monolithic Architecture**. All core logic will reside in a single backend server application. This drastically reduces complexity and deployment time.

**Core Components (Modules within the Monolith):**

- **Backend Server (Node.js/Express):** A single application that will handle everything:
    
    - **API Endpoints:** A set of REST APIs to serve the frontend.
        
    - **Authentication:** Simple, session-based, or JWT authentication. We'll skip complex SSO/LDAP integration and use a basic email/password login for the demo.
        
    - **Ticket Logic:** All business logic for creating, reading, and updating tickets.
        
    - **AI Wrapper:** A dedicated module that manages all calls to the Google Gemini API for classification, chatbot responses, etc.
        
    - **Notification Logic:** Functions that directly call email/SMS services (e.g., Nodemailer for email) when a ticket status changes.
        
    - **Ingestion (Optional Stretch Goal):** If time permits, a simple function can be added to check an email inbox on-demand or via a simple cron job.
        

Communication:

All communication will be through direct function calls within the single Node.js application. The frontend will communicate with the backend via a single set of REST APIs.

### **2. Simplified Technology Stack**

- **Backend (Node.js & Express.js):** Remains an excellent choice for its speed of development and non-blocking I/O.
    
- **Frontend (React.js):** Perfect for building a Single Page Application (SPA) for the chatbot and ticket dashboard. We'll skip the mobile app (React Native) to save time.
    
- **Database (MongoDB Atlas):** The free tier of MongoDB Atlas is perfect for a hackathon. Its flexible schema is ideal for quick iterations.
    
- **AI Engine (Google Gemini API):** This remains the core of the project's intelligence.
    
- **Deployment:**
    
    - **Frontend:** Vercel or Netlify (offers a fast, free, and simple git-based deployment for React apps).
        
    - **Backend:** Render or Heroku (provides a simple PaaS environment for deploying Node.js applications).
        

### **3. Detailed Data Flow (Simplified)**

#### **Scenario: Ticket Creation via Chatbot**

1. **User Interaction:** An employee sends a message ("My laptop won't turn on") to the React chatbot component.
    
2. **API Call:** The frontend makes a `POST` request to the backend's `/api/chat` endpoint, sending the message and user token.
    
3. **Backend Controller:** The Express router forwards the request to the `chatController`.
    
4. **AI Analysis:** The `chatController` calls a local `geminiService` module. This service sends the user's message to the Gemini API with a prompt.
    
5. **AI Response:** Gemini determines a ticket is needed and responds with JSON: `{"action": "create_ticket", "description": "User's laptop won't turn on.", "category": "Hardware", "urgency": "High"}`.
    
6. **Ticket Creation:** The `geminiService` returns this structured data to the `chatController`. The controller then calls a `ticketService` module, which creates a new document in the MongoDB `tickets` collection.
    
7. **Notification:** After successfully saving to the database, the `ticketService` calls a `notificationService` module, which uses Nodemailer to send a confirmation email directly. The response is then sent back to the frontend.
    

### **4. MongoDB Schema Design**

The schema design remains the same as it is well-suited for this purpose.

#### `tickets` Collection

```
{
  "_id": ObjectId("64f5a..."),
  "ticketId": "PWR-IT-2025-0001",
  "title": "Laptop Power Issue",
  "description": "User's laptop won't turn on.",
  "status": "Open",
  "priority": "High",
  "category": "Hardware",
  "source": "Chatbot",
  "requester": {
    "userId": ObjectId("64f5b..."),
    "name": "Employee Name",
    "email": "employee@powergrid.co.in"
  },
  "assignee": {},
  "createdAt": ISODate("2025-09-23T10:00:00Z"),
  "updatedAt": ISODate("2025-09-23T10:00:00Z"),
  "history": [
    {
      "timestamp": ISODate("2025-09-23T10:00:00Z"),
      "user": "System",
      "action": "Ticket created via Chatbot."
    }
  ]
}
```

#### `users` Collection

```
{
  "_id": ObjectId("64f5b..."),
  "employeeId": "12345",
  "name": "Employee Name",
  "email": "employee@powergrid.co.in",
  "role": "Employee",
  "password": "hashed_password_here" 
}
```

### **5. Hackathon Deployment Strategy**

1. **Code Repository:** Use a single GitHub repository with two folders: `/client` for the React app and `/server` for the Node.js app.
    
2. **Database:** Set up a free cluster on MongoDB Atlas and get the connection URI.
    
3. **Backend Deployment:**
    
    - Create a new "Web Service" on Render or Heroku.
        
    - Connect it to your GitHub repository.
        
    - Set the build command (`npm install`) and start command (`npm start`).
        
    - Add your `MONGO_URI` and `GEMINI_API_KEY` as environment variables in the Render/Heroku dashboard.
        
4. **Frontend Deployment:**
    
    - Create a new project on Vercel.
        
    - Connect it to the same GitHub repository, but point it to the `/client` directory.
        
    - Set the backend API URL as an environment variable (e.g., `REACT_APP_API_URL`).
        
    - Vercel will automatically build and deploy the React app.
        