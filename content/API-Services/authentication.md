+++
title = 'Authentication'
date = 2024-05-08T12:19:06+03:00
draft = true
weight = 10
+++


## Overview

The Authentication Service in the QEase API provides mechanisms for managing user authentication. This includes user registration, login, token refresh, and logout functionalities. These endpoints are crucial for securing access to the application and ensuring that user credentials are handled safely.

## Endpoints

### [Register](https://qease-app-04a682a52c08.herokuapp.com/docs#/auth/register_register_post) 

- **URL:** `/register`
- **Method:** POST
- **Authorization:** None
- **Description:** Register a new user with a username and password.
- **Request Body:**

  ```json
  {
    "username": "newuser",
    "password": "password123",
    "role": "user"
  }
    ```

- **Successful Response:**
    - **Code:** 201
    - **Content:** `{}`
    - **Error Response:**
        - **Code:** 422
        - **Content:**  
        ```json
        {   
            "detail": [{ "loc": ["body", "username"], 
            "msg": "field required",   
            "type": "value_error.missing" }] 
        }
        ```

### [Login](https://qease-app-04a682a52c08.herokuapp.com/docs#/auth/login_login_post)
- **URL:** `/login`
- **Method:** POST
- **Authorization:** None
- **Description:** Authenticate a user by username and password.
- **Parameters:**
username (string, required): User's username.
password (string, required): User's password.
- **Successful Response:**
    - **Code:** 200
    - **Content:** `{ "access_token": "jwt-token", "token_type": "bearer" }`
- **Error Response:**
    - **Code:** 422
    - **Content:**  
        ```json
        {   
            "detail": [{ "loc": ["body", "username"], 
            "msg": "field required",   
            "type": "value_error.missing" }] 
        }
        ```


### [Refresh Token](https://qease-app-04a682a52c08.herokuapp.com/docs#/auth/refresh_token_refresh_post)
- **URL:** `/refresh`
- **Method:** POST
- **Authorization:** Bearer Token (refresh token)
- **Description:** Refresh the access token using a refresh token.
- **Parameters:**
refresh_token (string, required): Refresh token provided during login or previous refresh.
- **Successful Response:**
    - **Code:** 200
    - **Content:** `{ "access_token": "new-jwt-token", "token_type": "bearer" }`
- **Error Response:**
    - **Code:** 422
    - **Content:**`{ "detail": "Invalid token" }`

### [Logout](https://qease-app-04a682a52c08.herokuapp.com/docs#/auth/logout_logout_post)
- **URL:** `/logout`
- **Method:** `POST`
- **Authorization:** Bearer Token
- **Description:** Log out a user by invalidating their authentication token.
- **Successful Response:**
    - **Code:** 200
    - **Content:** {}
- **Error Response:**
    - **Code:** 422
    - **Content:** `{ "detail": "Invalid token" }`

{{% notice note %}}
This website can be automatically published and hosted with [Github Pages](https://pages.github.com/). To learn more about it visit [Github pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
{{% /notice %}}