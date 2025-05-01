# API Documentation for `https://smartcoderz.shop/api/`

## Base URL:
`https://smartcoderz.shop/api/`

## **Available Endpoints**

---

### **1. `GET /`**

- **Description**: Returns a welcome message or a general status about the API.
- **Request Type**: `GET`
- **Response**: JSON containing status information or a message.

---

### **2. `GET /courses/`**

- **Description**: Retrieves a list of all available courses.
- **Request Type**: `GET`
- **Request Data**: None
- **Response**: JSON with a list of courses.

---

### **3. `POST /course/{id}/`**

- **Description**: Retrieves detailed information about a specific course.
- **Request Type**: `POST`
- **Request Data**: 
    - `id`: The course ID you want to retrieve details for.
- **Response**: JSON with detailed course information including lessons, topics, documents, etc.

---

### **4. `POST /user/register/`**

- **Description**: Registers a new user on the platform.
- **Request Type**: `POST`
- **Request Data**:
    - `email`: The email of the user.
    - `password`: The password for the user account.
- **Response**: JSON with user ID and registration status.

---

### **5. `POST /user/login/`**

- **Description**: Logs a user into the system.
- **Request Type**: `POST`
- **Request Data**:
    - `email`: The email of the user.
    - `password`: The password for the user account.
- **Response**: JSON with login status and user information.

---

### **6. `POST /progress/`**

- **Description**: Updates or retrieves the progress of a student in a course.
- **Request Type**: `POST`
- **Request Data**:
    - `course_id`: The ID of the course.
    - `student_id`: The ID of the student.
    - `progress`: Current progress (e.g., percentage or timestamp).
- **Response**: JSON indicating whether the progress update was successful.

---

### **7. `GET /notifications/`**

- **Description**: Retrieves all notifications for a user or course.
- **Request Type**: `GET`
- **Request Data**: None
- **Response**: JSON with a list of notifications.

---

### **8. `POST /upload/file/`**

- **Description**: Allows a user to upload a file for a specific course or lesson.
- **Request Type**: `POST`
- **Request Data**:
    - `file`: The file to upload (multipart/form-data).
    - `lesson_id`: The ID of the lesson or course related to the file.
- **Response**: JSON indicating the status of the upload.

---

### **Error Handling**

- **400**: Bad Request — The request is invalid or missing required parameters.
- **401**: Unauthorized — Invalid API key or authentication credentials.
- **404**: Not Found — The requested resource could not be found.
- **500**: Internal Server Error — There was an error processing the request on the server.

---

## **Authentication**

All endpoints require authentication via API key in the request header or body.

- **Key**: API key used for accessing the endpoints.
- Example of API key inclusion: 
  - In header: `Authorization: Bearer YOUR_API_KEY`
  - In body: `key=YOUR_API_KEY`

## **Rate Limits**

- The API might have rate limits to prevent abuse. Typically, the rate limit is 100 requests per minute per API key.

## **How to Use**

1. Make sure to include a valid API key for all requests.
2. Use the appropriate request type (GET, POST) based on the API endpoint.
3. Ensure that the required parameters are sent correctly for each request.

## **License**

This API is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
