+++
title = 'Clerks'
date = 2024-05-08T12:19:55+03:00
draft = true
weight = 14
+++

## Overview

The Clerk endpoints within the QEase API manage clerk operations. These endpoints facilitate creating, retrieving, and deleting clerk information, crucial for managing clerks assigned to various service windows within the application.

## Endpoints

### Get All Clerks

- **URL:** `/clerks/`
- **Method:** GET
- **Authorization:** Bearer Token (required)
- **Description:** Retrieves all clerk entries.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    [
      {
        "service_id": 1,
        "window_id": 1
      },
      {
        "service_id": 2,
        "window_id": 2
      }
    ]
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Validation error"
    }
    ```

### Create Clerk

- **URL:** `/clerks/`
- **Method:** POST
- **Authorization:** Bearer Token (required)
- **Description:** Adds a new clerk entry.
- **Request Body:**
  - **Content:** 
    ```json
    {
      "service_id": 1,
      "window_id": 1
    }
    ```
- **Successful Response:**
  - **Code:** 201
  - **Content:** 
    ```json
    {}
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Validation error"
    }
    ```

### Delete Clerk Entry by Window ID

- **URL:** `/clerks/{window_id}`
- **Method:** DELETE
- **Authorization:** Bearer Token (required)
- **Description:** Deletes a clerk entry based on the specified window ID.
- **Parameters:**
  - `window_id` (path, required, integer): The ID of the window associated with the clerk entry to delete.
- **Successful Response:**
  - **Code:** 204
  - **Content:** None

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Clerk entry not found or deletion not permitted."
    }
    ```

### Delete All Clerk Entries

- **URL:** `/clerks/`
- **Method:** DELETE
- **Authorization:** Bearer Token (required)
- **Description:** Removes all clerk entries from the system.
- **Successful Response:**
  - **Code:** 204
  - **Content:** None

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Deletion not permitted or failed."
    }
    ```

## Security Considerations

- All endpoints require authentication using HTTP Bearer tokens to ensure that only authorized personnel can manage clerk data.
- Proper permission checks should be in place to prevent unauthorized deletions or modifications.

## Usage

- These endpoints are intended primarily for administrators responsible for managing clerks and their assignments to service windows.
- Ensure that actions on these endpoints are logged and audited for security and compliance purposes.

{{% notice note %}}
This website can be automatically published and hosted with [Github Pages](https://pages.github.com/). To learn more about it visit [Github pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
{{% /notice %}}