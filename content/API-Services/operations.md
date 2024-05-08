+++
title = 'Operations'
date = 2024-05-08T12:20:05+03:00
weight = 15
+++


## Overview

The Operations Service of the QEase API provides endpoints for managing operational aspects of services and windows, including queue management and client servicing. These endpoints are essential for the dynamic interaction between clients, services, and service windows.

## Endpoints

### Get Service from Window

- **URL:** `/operations/getService/{window_id}`
- **Method:** GET
- **Authorization:** Bearer Token (required)
- **Description:** Retrieves the service associated with a specific window.
- **Parameters:**
  - `window_id` (path, required, integer): The ID of the window whose service is to be retrieved.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    {
      "service_id": 1,
      "service_name": "Customer Support",
      "service_description": "Handling customer support queries"
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

### Get Window from Service

- **URL:** `/operations/getWindow/{service_id}`
- **Method:** GET
- **Authorization:** Bearer Token (required)
- **Description:** Retrieves the window serving a specific service.
- **Parameters:**
  - `service_id` (path, required, integer): The ID of the service whose window is to be retrieved.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    {
      "window_id": 1,
      "window_number": "W001"
    }
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Service not found or access denied."
    }
    ```

### Join Queue

- **URL:** `/operations/joinQueue/{service_id}`
- **Method:** POST
- **Authorization:** Bearer Token (required)
- **Description:** Allows a client to join a queue for a specific service.
- **Parameters:**
  - `service_id` (path, required, integer): The ID of the service to join.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    {
      "message": "Added to queue successfully."
    }
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Failed to add to queue."
    }
    ```

### Get Queue Pendings

- **URL:** `/operations/getQueuePendings`
- **Method:** GET
- **Authorization:** Bearer Token (required)
- **Description:** Retrieves a list of all pending entries in the queue across all services.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    [
      {
        "ticket_id": 101,
        "service_id": 1,
        "status": "waiting"
      },
      {
        "ticket_id": 102,
        "service_id": 1,
        "status": "waiting"
      }
    ]
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Error retrieving queue."
    }
    ```

### Process Client by Window

- **URL:** `/operations/processClientByWindow`
- **Method:** POST
- **Authorization:** Bearer Token (required)
- **Description:** Processes the next client in the queue for a specified window.
- **Query Parameters:**
  - `ticket_id` (integer, required): The ticket ID of the client to be processed.
  - `window_id` (integer, required): The ID of the window where the client is being serviced.
- **Successful Response:**
  - **Code:** 200
  - **Content:** 
    ```json
    {
      "message": "Client processed successfully."
    }
    ```

- **Error Response:**
  - **Code:** 422
  - **Content:** 
    ```json
    {
      "detail": "Failed to process client."
    }
    ```

## Security Considerations

- All endpoints require authenticated access, utilizing Bearer tokens to ensure that operations are securely managed.
- Ensure roles and permissions are properly set to allow only authorized users to execute operations, particularly for sensitive actions like processing clients or managing queues.

## Usage

- These endpoints are intended for administrators and operators managing the daily operations of service windows.
- Proper monitoring and logging of these actions are recommended to maintain an audit trail for security and operational accountability.


{{% notice note %}}
This website can be automatically published and hosted with [Github Pages](https://pages.github.com/). To learn more about it visit [Github pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
{{% /notice %}}