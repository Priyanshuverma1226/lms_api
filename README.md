# API Documentation for `https://smartcoderz.shop/api/`

## Base URL:
`https://smartcoderz.shop/api/`

## **Available Endpoints**

---
# Course API Documentation

This repository contains the API endpoints for managing and retrieving course-related data. Below is the documentation for all available endpoints.

---

## **1. `get_course_all`**

- **Method**: `POST`
- **Endpoint**: `/get_course_all/`
- **Description**: Retrieves all available courses. It checks the provided key for validity, and if the key is valid, it returns a list of all courses along with additional details like the number of lessons and documents associated with each course.
- **Request Data**:
    - `key`: API key for authentication (passed in POST data).
- **Response**: JSON with a list of all courses, including lesson count, document count, and related data (lessons, documents, dialogues, etc.).

---

## **2. `all_course`**

- **Method**: `POST`
- **Endpoint**: `/all_course/`
- **Description**: Retrieves all courses along with their associated lessons, sub-lessons, topics, documents, dialogues, features, and testimonials.
    - For each lesson, it further retrieves sub-lessons and topics associated with it.
    - It also retrieves media files associated with the course's sub-lessons, dialogues, and documents.
- **Request Data**:
    - `key`: API key for authentication.
 
- **Optional**:
    - `deivice_id`: Check User Course Assign or Enroll.
- **Response**: JSON with all course data, including lessons, sub-lessons, topics, documents, dialogues, features, and testimonials.

---

## **3. `get_course`**

- **Method**: `POST`
- **Endpoint**: `/get_course/`
- **Description**: Retrieves a single course based on the provided `id`. It returns all related data for that course (lessons, documents, dialogues, etc.).
- **Request Data**:
    - `id`: ID of the course to be retrieved.
    - `key`: API key for authentication.
 
- **Optional**:
    - `deivice_id`: Check User Course Assign or Enroll.
- **Response**: JSON with the course data, including lessons, documents, dialogues, features, and testimonials.

---

## **4. `get_lesson`**

- **Method**: `POST`
- **Endpoint**: `/get_lesson/`
- **Description**: Retrieves a single lesson based on the provided `id`. It returns the lesson data, including associated sub-lessons, topics, and related files.
- **Request Data**:
    - `id`: ID of the lesson to be retrieved.
    - `key`: API key for authentication.
- **Response**: JSON with lesson data, including sub-lessons, topics, and related files.

---

## **5. `get_document`**

- **Method**: `POST`
- **Endpoint**: `/get_document/`
- **Description**: Retrieves a single document based on the provided `id`. It returns document data along with associated sub-documents and files.
- **Request Data**:
    - `id`: ID of the document to be retrieved.
    - `key`: API key for authentication.
- **Response**: JSON with document data, including sub-documents and related files.

---

## **6. `get_dialogue`**

- **Method**: `POST`
- **Endpoint**: `/get_dialogue/`
- **Description**: Retrieves a single dialogue based on the provided `id`. It returns dialogue data along with related sub-dialogues, files, and audio.
- **Request Data**:
    - `id`: ID of the dialogue to be retrieved.
    - `key`: API key for authentication.
- **Response**: JSON with dialogue data, including sub-dialogues and related media files (audio, files).

---

## **7. `get_progress`**

- **Method**: `POST`
- **Endpoint**: `/get_progress/`
- **Description**: Retrieves the progress of a student on a specific course based on the `source` (course) and `student` (student ID).
- **Request Data**:
    - `source`: ID of the course.
    - `student`: ID of the student.
    - `key`: API key for authentication.
- **Response**: JSON with progress data related to the student and course.

---

## **8. `set_progress`**

- **Method**: `POST`
- **Endpoint**: `/set_progress/`
- **Description**: Sets or updates the progress of a student on a course, requiring the student ID, course ID, and a timestamp indicating the student's progress.
- **Request Data**:
    - `source`: ID of the course.
    - `student`: ID of the student.
    - `time_stamp`: Timestamp of the student's progress.
    - `key`: API key for authentication.
- **Response**: JSON indicating success or failure in setting/updating progress.

---

## **9. `add_user`**

- **Method**: `POST`
- **Endpoint**: `/add_user/`
- **Description**: Allows the creation of a new user (student) by providing an email address. It generates an OTP for the user’s password and links the user to the `student` model.
- **Request Data**:
    - `email`: Email address of the user.
    - `key`: API key for authentication.
- **Response**: JSON indicating whether the user was already created or newly created, along with the user ID.

---

## **10. `get_file`**

- **Method**: `POST`
- **Endpoint**: `/get_file/`
- **Description**: Retrieves a file based on its ID, returning the details of the file.
- **Request Data**:
    - `id`: ID of the file to be retrieved.
    - `key`: API key for authentication.
- **Response**: JSON with file details.

---

## **11. `notification_get`**

- **Method**: `POST`
- **Endpoint**: `/notification_get/`
- **Description**: Retrieves all notifications, returning all notifications from the `notification` model.
- **Request Data**:
    - `key`: API key for authentication.
- **Response**: JSON with a list of all notifications.

---

## **12. `get_meeting`**

- **Method**: `POST`
- **Endpoint**: `/get_meeting/`
- **Description**: Retrieves details about all meetings, returning a list of all meeting details from the `meeting_details` model.
- **Request Data**:
    - `key`: API key for authentication.
- **Response**: JSON with a list of all meeting details.

---


## **13. `enrollment_form`**

- **Method**: `POST`
- **Endpoint**: `/enrollment_form/`
- **Request Data**:
    - `key`: API key for authentication.
    - `name`: User Data.
    - `language`: User Data.
    - `mobile_no`: User Data.
- **Response**: JSON with a list of all meeting details.

---

## **14. `enroll_list`**

- **Method**: `POST`
- **Endpoint**: `/enroll_list/`
- **Description**: Retrieves details about all enrollment, returning a list of all enrollment details from the `enroll_list` model.
- **Request Data**:
    - `key`: API key for authentication.
    - `device_id`: User device_id .

- **Response**: JSON with a list of all meeting details.

---

## **How to Use:**

1. **Authentication**: Each API request requires a valid `key` for authentication, which should be passed in the POST data.
2. **Response Format**: All responses are returned as JSON containing the requested data.
3. **Request Tools**: You can use any HTTP client (e.g., Postman, cURL) to make POST requests to the above endpoints with the required data.

---

## **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
