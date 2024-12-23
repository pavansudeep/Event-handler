**Project Documentation for Event Management Web App**
DIRECT LINK :https://genuine-bunny-c647fe.netlify.app/
---

### **Introduction**
This document provides detailed instructions to set up and run the Event Management Web Application. The application is developed using React for the front end, Node.js for the backend, Supabase as the database, and deployed via Netlify.

---

### **1. Project Setup**

#### **Prerequisites**
1. Node.js (version 14 or higher)
2. npm or yarn
3. Supabase account and project set up
4. Netlify account
5. Code editor (e.g., Visual Studio Code)

#### **Steps to Set Up the Project**

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. **Install Dependencies**:
   ```bash
   npm install
   ```
   or
   ```bash
   yarn install
   ```

3. **Set Up Environment Variables**:
   Create a `.env` file in the root directory and add the following variables:
   ```env
   REACT_APP_SUPABASE_URL=<Your Supabase URL>
   REACT_APP_SUPABASE_ANON_KEY=<Your Supabase Anon Key>
   API_BASE_URL=<Your Backend API Base URL>
   ```

4. **Run the Application**:
   - **Development Mode**:
     ```bash
     npm start
     ```
     or
     ```bash
     yarn start
     ```
   - The app will be accessible at `http://localhost:3000/`.

5. **Build for Production**:
   ```bash
   npm run build
   ```
   or
   ```bash
   yarn build
   ```
   The production build files will be in the `build/` directory.

6. **Deploy on Netlify**:
   - Connect your Git repository to Netlify.
   - Set up environment variables in Netlify settings.
   - Deploy the project.

---

### **2. API Details**

The backend of this application is powered by Node.js and provides the following APIs:

#### **Authentication**

1. **User Signup**
   - **Endpoint**: `/api/auth/signup`
   - **Method**: POST
   - **Description**: Registers a new user.
   - **Request Body**:
     ```json
     {
       "email": "user@example.com",
       "password": "securepassword"
     }
     ```
   - **Response**:
     ```json
     {
       "message": "User registered successfully",
       "userId": "12345"
     }
     ```

2. **User Login**
   - **Endpoint**: `/api/auth/login`
   - **Method**: POST
   - **Description**: Authenticates a user.
   - **Request Body**:
     ```json
     {
       "email": "user@example.com",
       "password": "securepassword"
     }
     ```
   - **Response**:
     ```json
     {
       "token": "jwt_token"
     }
     ```

#### **Events Management**

1. **Create Event**
   - **Endpoint**: `/api/events`
   - **Method**: POST
   - **Description**: Adds a new event.
   - **Request Body**:
     ```json
     {
       "name": "Event Name",
       "date": "2024-12-31",
       "location": "Online",
       "description": "Event Details"
     }
     ```
   - **Response**:
     ```json
     {
       "message": "Event created successfully",
       "eventId": "67890"
     }
     ```

2. **Fetch Events**
   - **Endpoint**: `/api/events`
   - **Method**: GET
   - **Description**: Retrieves all events.
   - **Response**:
     ```json
     [
       {
         "id": "67890",
         "name": "Event Name",
         "date": "2024-12-31",
         "location": "Online",
         "description": "Event Details"
       }
     ]
     ```

3. **Update Event**
   - **Endpoint**: `/api/events/:id`
   - **Method**: PUT
   - **Description**: Updates an existing event.
   - **Request Body**:
     ```json
     {
       "name": "Updated Event Name",
       "date": "2025-01-01",
       "location": "Hybrid",
       "description": "Updated Details"
     }
     ```
   - **Response**:
     ```json
     {
       "message": "Event updated successfully"
     }
     ```

4. **Delete Event**
   - **Endpoint**: `/api/events/:id`
   - **Method**: DELETE
   - **Description**: Deletes an event.
   - **Response**:
     ```json
     {
       "message": "Event deleted successfully"
     }
     ```

#### **Integration with Supabase**
- **Supabase Functions**:
  - Supabase is used to store and retrieve event data.
  - Use Supabase SDK to interact with the database in both frontend and backend.
  
- **Example Query to Fetch Events**:
  ```javascript
  import { createClient } from '@supabase/supabase-js';

  const supabase = createClient(SUPABASE_URL, SUPABASE_ANON_KEY);

  async function fetchEvents() {
    const { data, error } = await supabase
      .from('events')
      .select('*');
    if (error) throw error;
    return data;
  }
  ```

---

### **3. Project Architecture**

1. **Frontend**:
   - Built with React and styled using CSS.
   - State management handled via React Context API.

2. **Backend**:
   - Node.js server using Express.
   - Authentication with JWT.
   - API endpoints hosted on Netlify Functions.

3. **Database**:
   - Supabase for managing event data.

4. **Deployment**:
   - Frontend deployed on Netlify.
   - Backend APIs hosted on Netlify Functions.

---

### **4. Conclusion**
This documentation serves as a guide for developers and users to understand, set up, and interact with the Event Management Web App. For further assistance, refer to the official documentation of React, Node.js, Supabase, and Netlify.

