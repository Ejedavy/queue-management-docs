+++
title = 'Windows'
date = 2024-05-08T12:19:42+03:00
draft = true
weight = 13
+++

## Overview

The Windows Service in the QEase API provides functionalities for managing windows through which services are offered. These endpoints allow administrators to create, retrieve, update, and delete window records, ensuring effective management of service delivery points.

## Endpoints

### List Windows

- **URL:** `/windows/`
- **Method:** GET
- **Authorization:** Bearer Token (required)
- **Description:** Retrieves all window entries, with an optional search parameter to filter the results.
- **Query Parameters:**
  - `search` (string, optional): A search term to filter windows by attributes such as window number.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    [
      {
        "window_id": 1,
        "window_number": "W001",
        "published": true
      },
      {
        "window_id": 2,
        "window_number": "W002",
        "published": true
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

### Create Window

- **URL:** `/windows/`
- **Method:** POST
- **Authorization:** Bearer Token (required)
- **Description:** Creates a new window record.
- **Request Body:**
  - **Content:** 
    ```json
    {
      "window_number": "W003",
      "published": true
    }
    ```
- **Successful Response:**
  - **Code:** 201
  - **Content:** 
    ```json
    {
      "window_id": 3,
      "window_number": "W003",
      "published": true
    }
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Validation error"
    }
    ```

### Get Window

- **URL:** `/windows/{id}`
- **Method:** GET
- **Authorization:** Bearer Token (required)
- **Description:** Retrieves details of a specific window by ID.
- **Parameters:**
  - `id` (path, required, integer): The ID of the window to retrieve.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    {
      "window_id": 1,
      "window_number": "W001",
      "published": true
    }
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Window not found or access denied."
    }
    ```

### Update Window

- **URL:** `/windows/{id}`
- **Method:** PUT
- **Authorization:** Bearer Token (required)
- **Description:** Updates details of a specific window by ID.
- **Parameters:**
  - `id` (path, required, integer): The ID of the window to update.
- **Request Body:**
  - **Content:** 
    ```json
    {
      "window_number": "W001-updated",
      "published": false
    }
    ```
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    {
      "window_id": 1,
      "window_number": "W001-updated",
      "published": false
    }
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Validation error or operation not permitted."
    }
    ```

### Delete Window

- **URL:** `/windows/{id}`
- **Method:** DELETE
- **Authorization:** Bearer Token (required)
- **Description:** Deletes a specific window by ID.
- **Parameters:**
  - `id` (path, required, integer): The ID of the window to delete.
- **Successful Response:**
  - **Code:** 204
  - **Content:** None

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Window not found or deletion not permitted."
    }
    ```

## Security Considerations

- All endpoints require authenticated access, with actions permitted only for users having appropriate roles.
- It is recommended to enforce strict access control and to audit all operations related to window management.

## Usage

- These endpoints are crucial for administrators tasked with setting up and managing service windows within the application.
- Care should be taken to ensure that only authorized changes are made to window configurations to prevent disruptions in service delivery.

{{% notice note %}}
This website can be automatically published and hosted with [Github Pages](https://pages.github.com/). To learn more about it visit [Github pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
{{% /notice %}}
