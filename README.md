# API Documentation for `https://smartcoderz.shop/api/`

## Base URL:
`https://smartcoderz.shop/api/`

## **Available Endpoints**

---
# Course API Documentation

This repository contains the API endpoints for managing and retrieving course-related data. Below is the documentation for all available endpoints.




## 🔐 Common Parameter (Required for all endpoints)

| Name | Type   | Description                |
|------|--------|----------------------------|
| key  | string | Authentication token value |

---

## 1. 📦 `/all_course` - Get All Courses with Full Hierarchy

**Description:** Returns all courses with full details including lesson structure, documents, dialogues, features, and testimonials.

**Additional Parameters:**

| Name       | Type   | Required | Description                  |
|------------|--------|----------|------------------------------|
| device_id  | string | No       | Device ID to check enrollment |

**Returns:**

- `lesson` → `sub_lesson` → `topic` → `module`
- `document` → `sub_document` → `source`
- `dialogue` → `sub_dialogue` → `file`, `audio`
- `features`
- `testimonals`
- `enrolled_status`, `enrollded_data` (if `device_id` provided)

---

## 2. 📘 `/get_course` - Get Single Course by ID

**Description:** Fetch a course with its full nested data.

**Parameters:**

| Name       | Type   | Required | Description                  |
|------------|--------|----------|------------------------------|
| key        | string | Yes      | Auth token                   |
| id         | int    | Yes      | Course ID                    |
| device_id  | string | No       | Device ID to check enrollment |

**Returns:** Same nested structure as `/all_course` but only for one course.

---

## 3. 📝 `/enrollment_form` - Submit Enrollment Form

**Description:** Store basic user enrollment form data.

**Parameters:**

| Name       | Type   | Required | Description       |
|------------|--------|----------|-------------------|
| key        | string | Yes      | Auth token        |
| name       | string | Yes      | Name of user      |
| language   | string | Yes      | Preferred language|
| mobile_no  | string | Yes      | Mobile number     |

**Returns:** Form submission status.

---

## 4. 📋 `/enroll_list` - Get Enrolled Courses

**Description:** Get list of enrolled courses for a student.

**Parameters:**

| Name        | Type   | Required | Description         |
|-------------|--------|----------|---------------------|
| key         | string | Yes      | Auth token          |
| device_id   | string | Yes      | Device ID           |
| student_id  | string | Yes      | Student unique ID   |

**Returns:** Enrollments related to provided student and device.

---

## 5. 📖 `/get_lesson` - Get All Lessons of a Course

**Description:** Returns all lessons, sub-lessons, topics, and modules for a course.

**Parameters:**

| Name | Type   | Required | Description   |
|------|--------|----------|---------------|
| key  | string | Yes      | Auth token    |
| id   | int    | Yes      | Course ID     |

**Returns:**  
- Lessons  
  └─ Sub-lessons  
     └─ Topics  
        └─ Modules  
     └─ Source file (`source_id`)

---

## 6. 📄 `/get_document` - Get Single Document

**Description:** Returns document and sub-documents with associated files.

**Parameters:**

| Name | Type   | Required | Description   |
|------|--------|----------|---------------|
| key  | string | Yes      | Auth token    |
| id   | int    | Yes      | Document ID   |

**Returns:**  
- Sub-documents  
  └─ Files (`source_id`)

---

## 7. 🎙 `/get_dialogue` - Get Single Dialogue

**Description:** Returns dialogue and sub-dialogue structure.

**Parameters:**

| Name | Type   | Required | Description   |
|------|--------|----------|---------------|
| key  | string | Yes      | Auth token    |
| id   | int    | Yes      | Dialogue ID   |

**Returns:**  
- Sub-dialogues  
  └─ File (`file_id`)  
  └─ Audio (`audio_id`)

---

## 8. 🧪 `/get_course_all` - Get Courses (Lite - Dev/Test)

**Description:** Returns all courses with just lesson and document counts. Mainly for internal use or testing.

**Parameters:**

| Name | Type   | Required | Description   |
|------|--------|----------|---------------|
| key  | string | Yes      | Auth token    |

**Returns:**  
- `lesson` count  
- `documents` count

---

## 📈 `/get_progress` – Get Student's Progress

**Description:** Fetch progress details of a student for a given source (lesson, document, or video).

**Parameters:**

| Name     | Type   | Required | Description                  |
|----------|--------|----------|------------------------------|
| key      | string | Yes      | Auth token                   |
| source   | string | Yes      | Source ID (e.g., lesson ID)  |
| student  | string | Yes      | Student ID                   |

**Returns:**  
Progress entry list with `time_stamp`.

---

## 📥 `/set_progress` – Set/Update Student's Progress

**Description:** Save or update progress (e.g., video playback position).

**Parameters:**

| Name        | Type   | Required | Description                   |
|-------------|--------|----------|-------------------------------|
| key         | string | Yes      | Auth token                    |
| source      | string | Yes      | Source ID (e.g., lesson ID)   |
| student     | string | Yes      | Student ID                    |
| time_stamp  | string | Yes      | Progress timestamp (in sec)   |

**Returns:**  
- Message confirming creation or update of progress.

---

## 👤 `/add_user` – Add or Get User by Email

**Description:**  
- If user exists → return existing.
- If not → create user + student record + assign device.

**Parameters:**

| Name       | Type   | Required | Description       |
|------------|--------|----------|-------------------|
| key        | string | Yes      | Auth token        |
| email      | string | Yes      | User email        |
| device_id  | string | Yes      | Device identifier |

**Returns:**  
- Status = `Already` or `Created`  
- `user_id` JSON

---

## 📂 `/get_file` – Get File Metadata

**Description:** Return file information by file ID.

**Parameters:**

| Name | Type   | Required | Description |
|------|--------|----------|-------------|
| key  | string | Yes      | Auth token  |
| id   | int    | Yes      | File ID     |

**Returns:**  
- File metadata

---

## 📂 `/get_file_free_resource` – Get Free Resource Files

**Description:** Fetch files flagged as free resources.

**Parameters:**

| Name     | Type    | Required | Description                   |
|----------|---------|----------|-------------------------------|
| key      | string  | Yes      | Auth token                    |
| is_free  | boolean | Yes      | Whether file is free or not   |

**Returns:**  
- List of free `Files`

---

## 📅 `/get_meeting` – Get Active Meeting Links

**Description:** Fetch scheduled meetings that are active.

**Parameters:**

| Name       | Type   | Required | Description                     |
|------------|--------|----------|---------------------------------|
| key        | string | Yes      | Auth token                      |
| course_id  | int    | No       | Filter meetings by course ID    |

**Returns:**  
- Meeting details (`status=True`)


## 👤 `/edit_user` – Edit User Profile

**Description:** Update user information like name, score, location, and profile photo.

**Parameters:**

| Name          | Type     | Required | Description                     |
|---------------|----------|----------|---------------------------------|
| key           | string   | Yes      | Auth token                      |
| email         | string   | Yes      | User email                      |
| name          | string   | No       | Full name                       |
| score         | string   | No       | User score                      |
| location      | string   | No       | User location                   |
| profile_photo | file     | No       | Profile image (multipart form)  |

**Returns:**  
- User update status

---

## 🔑 `/token_page` – Token Management (HTML Page)

**Description:** Display all generated tokens on a webpage.

---

## ➕ `/add_token` – Add a New API Token

**Description:** Generate a 24-character random token and save it.

**Parameters (POST only):**

| Name | Type   | Required | Description     |
|------|--------|----------|-----------------|
| name | string | Yes      | Token label     |

**Returns:**  
- Redirect with success message

---

## ❌ `/delete_token/<id>` – Delete a Token

**Description:** Delete token by its ID.

---

## 🔔 `/notification_get` – Get Notifications for a Student

**Description:** Returns all notifications assigned to a student with message and title.

**Parameters:**

| Name        | Type   | Required | Description        |
|-------------|--------|----------|--------------------|
| key         | string | Yes      | Auth token         |
| student_id  | string | Yes      | Student ID         |

**Returns:**  
- Notification list with `viewed` status and message details

---

## 🔄 `/notification_update` – Mark Notification as Viewed

**Description:** Update notification viewed status.

**Parameters:**

| Name            | Type   | Required | Description              |
|-----------------|--------|----------|--------------------------|
| key             | string | Yes      | Auth token               |
| notification_id | string | Yes      | Notification instance ID |

**Returns:**  
- Viewed = True

---

## 📽️ `/recording_get` – Get Course Recordings

**Description:** Return all video class recordings for a course.

**Parameters:**

| Name       | Type   | Required | Description         |
|------------|--------|----------|---------------------|
| key        | string | Yes      | Auth token          |
| course_id  | int    | Yes      | Course ID           |

**Returns:**  
- List of class recordings with optional course info

---

## 🌐 `/free_resource_get` – Get All Free Resources

**Description:** Return all public/free learning resources.

**Parameters:**

| Name | Type   | Required | Description  |
|------|--------|----------|--------------|
| key  | string | Yes      | Auth token   |

**Returns:**  
- List of free resources  
- Each resource includes associated `Files` object under `source_data`









## **How to Use:**

1. **Authentication**: Each API request requires a valid `key` for authentication, which should be passed in the POST data.
2. **Response Format**: All responses are returned as JSON containing the requested data.
3. **Request Tools**: You can use any HTTP client (e.g., Postman, cURL) to make POST requests to the above endpoints with the required data.

---

## **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
