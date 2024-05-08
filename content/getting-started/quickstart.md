+++
title = 'Quickstart'
date = 2024-05-08T12:00:49+03:00
draft = true
weight = 7
+++

QEase API Quick Reference Guide

## Base URL
[Base URL](https://qease-app-04a682a52c08.herokuapp.com/docs)
`https://qease-app-04a682a52c08.herokuapp.com/docs`


## Authentication

| Endpoint          | Method | Description                     |
|-------------------|--------|---------------------------------|
| `/login`          | POST   | Logs in a user                  |
| `/logout`         | POST   | Logs out a user                 |
| `/register`       | POST   | Registers a new user            |
| `/registerAdmin`  | POST   | Creates a new admin user        |
| `/refresh`        | POST   | Refreshes an authentication token|

## Users

| Endpoint          | Method | Description                         |
|-------------------|--------|-------------------------------------|
| `/users/me`       | GET    | Retrieves the current user's profile |
| `/users/{user_id}`| GET    | Fetches details of a user by ID      |
| `/users/{user_id}`| PUT    | Updates a user's details             |
| `/users/{user_id}`| DELETE | Deletes a user by ID                 |
| `/users`          | GET    | Retrieves a list of users            |

## Services

| Endpoint          | Method | Description               |
|-------------------|--------|---------------------------|
| `/services/`      | GET    | Lists all services        |
| `/services/`      | POST   | Creates a new service     |
| `/services/{id}`  | GET    | Retrieves a service by ID |
| `/services/{id}`  | PUT    | Updates a service by ID   |
| `/services/{id}`  | DELETE | Deletes a service by ID   |

## Windows

| Endpoint          | Method | Description               |
|-------------------|--------|---------------------------|
| `/windows/`       | GET    | Lists all windows         |
| `/windows/`       | POST   | Creates a new window      |
| `/windows/{id}`   | GET    | Retrieves a window by ID  |
| `/windows/{id}`   | PUT    | Updates a window by ID    |
| `/windows/{id}`   | DELETE | Deletes a window by ID    |

## Clerks

| Endpoint                  | Method | Description                  |
|---------------------------|--------|------------------------------|
| `/clerks/`                | GET    | Retrieves all clerks         |
| `/clerks/`                | POST   | Posts clerks information     |
| `/clerks/{window_id}`     | DELETE | Deletes a clerk entry by window ID |

## Operations

| Endpoint                           | Method | Description                            |
|------------------------------------|--------|----------------------------------------|
| `/operations/getService/{window_id}` | GET  | Fetches service by window ID           |
| `/operations/getWindow/{service_id}` | GET  | Retrieves window by service ID         |
| `/operations/joinQueue/{service_id}` | POST | User joins a queue by service ID       |
| `/operations/callClientByWindow`   | POST   | Calls client by window                  |
| `/operations/processClientByWindow`| POST   | Processes client by window              |
| `/operations/acceptClientByWindow` | POST   | Accepts client by window                |
| `/operations/rejectClientByWindow` | POST   | Rejects client by window                |

### Security

Most endpoints require authentication using HTTP Bearer tokens. Ensure to include an appropriate authorization header where necessary.

For more detailed descriptions, parameters, request bodies, and responses, please refer to the full API documentation at [QEase API Docs](https://qease-app-04a682a52c08.herokuapp.com/docs).

{{% notice note %}}
This website can be automatically published and hosted with [Github Pages](https://pages.github.com/). To learn more about it visit [Github pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
{{% /notice %}}