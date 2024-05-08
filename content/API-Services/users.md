+++
title = 'Users'
date = 2024-05-08T12:19:21+03:00
draft = true
weight = 11
+++

## Overview

The User Service in the QEase API provides functionalities for managing user information. It allows fetching, updating, and deleting user data, as well as listing all users registered in the system. These endpoints are critical for managing access and roles within the application.

## Endpoints

### Current User

- **URL:** `/users/me`
- **Method:** GET
- **Authorization:** Bearer Token (required)
- **Description:** Retrieve details of the currently authenticated user.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    {
      "id": 1,
      "username": "currentuser",
      "role": "user",
      "created_at": "2021-01-01T12:00:00Z"
    }
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Authentication credentials were not provided or are invalid."
    }
    ```

### Get User by ID

- **URL:** `/users/{user_id}`
- **Method:** GET
- **Authorization:** Bearer Token (required)
- **Description:** Fetch details of a user by their unique ID.
- **Parameters:**
  - `user_id` (path, required, integer): The ID of the user to retrieve.
- **Successful Response:**
  - **Code:** 200
  - **Content:**
    ```json
    {
      "id": 2,
      "username": "sampleuser",
      "role": "user",
      "created_at": "2021-02-01T12:00:00Z"
    }
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:**
    ```json
    {
      "detail": "User not found or access denied."
    }
    ```

### Edit User

- **URL:** `/users/{user_id}`
- **Method:** PUT
- **Authorization:** Bearer Token (required)
- **Description:** Update details of a specific user by ID.
- **Parameters:**
  - `user_id` (path, required, integer): The ID of the user to update.
- **Request Body:**
  - **Content:** 
    ```json
    {
      "username": "newusername",
      "role": "admin"
    }
    ```
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    {
      "id": 2,
      "username": "newusername",
      "role": "admin",
      "created_at": "2021-02-01T12:00:00Z"
    }
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Invalid data provided or operation not permitted."
    }
    ```

### Delete User

- **URL:** `/user/{id}`
- **Method:** DELETE
- **Authorization:** Bearer Token (required)
- **Description:** Delete a user by their unique ID.
- **Parameters:**
  - `id` (path, required, integer): The ID of the user to delete.
- **Successful Response:**
  - **Code:** 204
  - **Content:** None

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "User not found or operation not permitted."
    }
    ```

### List All Users

- **URL:** `/users`
- **Method:** GET
- **Authorization:** Bearer Token (required)
- **Description:** Retrieve a list of all users. Optional query parameter to filter users by username.
- **Parameters:**
  - `username` (query, optional, string): Filter users by username.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    [
      {
        "id": 1,
        "username": "userone",
        "role": "user",
        "created_at": "2021-01-01T12:00:00Z"
      },
      {
        "id": 2,
        "username": "usertwo",
        "role": "admin",
        "created_at": "2021-02-01T12:00:00Z"
      }
    ]
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Error retrieving users or no users found."
    }
    ```

## Security Considerations

- All user-related endpoints require an authenticated user with appropriate permissions, typically enforced through HTTP Bearer authentication.
- Ensure secure handling of user data, especially personal information and passwords.

## Usage

- These endpoints are intended for use by administrators and authorized personnel tasked with user management within the application.
- For updating and deleting users, ensure that the operation is permitted for the authenticated user's role.


{{% notice note %}}
This website can be automatically published and hosted with [Github Pages](https://pages.github.com/). To learn more about it visit [Github pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
{{% /notice %}}