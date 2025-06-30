# REST API (Flask User Management)

A simple RESTful API built with Flask, demonstrating fundamental API development concepts and basic user data management.

## Project Objective

The primary objective of this project is to create a REST API that manages user data, providing practical experience with:
* Designing and implementing RESTful endpoints.
* Handling GET, POST, PUT, and DELETE HTTP methods.
* Working with Flask for web service development.

## Features

* **Create User:** Add new user records (`POST /users`)
* **Get All Users:** Retrieve a list of all stored users (`GET /users`)
* **Get Single User:** Retrieve details for a specific user by ID (`GET /users/<id>`)
* **Update User:** Modify existing user information (`PUT /users/<id>`)
* **Delete User:** Remove a user record (`DELETE /users/<id>`)

## Technologies Used

* **Python 3.x**
* **Flask** (Web Framework)

## Setup and Installation

Follow these steps to get the API running locally on your machine:

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/codebyte09/REST-API.git](https://github.com/codebyte09/REST-API.git)
    cd REST-API
    ```

2.  **Create and activate a virtual environment (recommended):**
    ```bash
    python -m venv venv
    # On Windows:
    .\venv\Scripts\activate
    # On macOS/Linux:
    source venv/bin/activate
    ```

3.  **Install dependencies:**
    ```bash
    pip install Flask
    ```

4.  **Run the Flask application:**
    ```bash
    python rest_api.py
    ```
    The API will start running on `http://127.0.0.1:5000/`.

## API Endpoints and Usage

You can test these endpoints using tools like [Postman](https://www.postman.com/downloads/) or `curl`.

**Base URL:** `http://127.0.0.1:5000`

---

### 1. Get All Users

* **URL:** `/users`
* **Method:** `GET`
* **Description:** Retrieves a list of all users.
* **Response:**
    ```json
    [
        {
            "id": 1,
            "name": "Alice Smith",
            "email": "alice@example.com"
        },
        {
            "id": 2,
            "name": "Bob Johnson",
            "email": "bob@example.com"
        }
    ]
    ```

---

### 2. Get Single User by ID

* **URL:** `/users/<user_id>` (e.g., `/users/1`)
* **Method:** `GET`
* **Description:** Retrieves a single user's details.
* **Response (Success):**
    ```json
    {
        "id": 1,
        "name": "Alice Smith",
        "email": "alice@example.com"
    }
    ```
* **Response (Not Found):**
    ```json
    {
        "error": "User not found"
    }
    ```
    Status: `404 Not Found`

---

### 3. Create a New User

* **URL:** `/users`
* **Method:** `POST`
* **Description:** Adds a new user.
* **Request Body (JSON):**
    ```json
    {
        "name": "New User Name",
        "email": "new.user@example.com"
    }
    ```
* **Response (Success):**
    ```json
    {
        "id": 3,
        "name": "New User Name",
        "email": "new.user@example.com"
    }
    ```
    Status: `201 Created`

---

### 4. Update an Existing User

* **URL:** `/users/<user_id>` (e.g., `/users/1`)
* **Method:** `PUT`
* **Description:** Updates an existing user's details.
* **Request Body (JSON - can include `name` or `email` or both):**
    ```json
    {
        "name": "Updated Name",
        "email": "updated.email@example.com"
    }
    ```
* **Response (Success):**
    ```json
    {
        "id": 1,
        "name": "Updated Name",
        "email": "updated.email@example.com"
    }
    ```
* **Response (Not Found):**
    ```json
    {
        "error": "User not found"
    }
    ```
    Status: `404 Not Found`

---

### 5. Delete a User

* **URL:** `/users/<user_id>` (e.g., `/users/1`)
* **Method:** `DELETE`
* **Description:** Deletes a user from the system.
* **Response (Success):**
    ```json
    {
        "message": "User deleted successfully"
    }
    ```
    Status: `204 No Content`
* **Response (Not Found):**
    ```json
    {
        "error": "User not found"
    }
    ```
    Status: `404 Not Found`

---

## Data Storage

User data is stored in an in-memory Python dictionary. This means all data will be lost when the Flask application is restarted.
