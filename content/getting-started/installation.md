+++
title = 'Installation'
date = 2024-05-08T11:24:54+03:00
draft = true
weight = 6
+++

The following steps are here to help you initialize your backend server locally. If you don't know programming at all, we strongly suggest you learn more about it by following this [great documentation for beginners](https://www.python.org/about/gettingstarted/).

## Prerequisites
Before you begin, ensure you have the following installed:
- [Git](https://git-scm.com/downloads)
- [Docker](https://www.docker.com/products/docker-desktop)
- [Python](https://www.python.org/downloads/) (version 3.8 or higher)

## Cloning the Repository

Start by cloning the repository to your local machine:

```bash
git clone https://github.com/eaaniwezi/QEase.git
cd QEase
Setting Up PostgreSQL with Docker
Run a PostgreSQL server using Docker:
```

``` bash
docker run --name postgresql -e POSTGRES_USER=yourusername -e POSTGRES_PASSWORD=yourpassword -p 5432:5432 -d postgres
```

Replace `yourusername` and `yourpassword` with your desired username and password. This command starts a PostgreSQL server that listens on the default port 5432.

## Virtual Environment Setup
It's recommended to use a virtual environment to isolate project dependencies. You can set one up using:

```bash

python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
Install Dependencies
Install the required Python dependencies with pip:
```

```bash
pip install -r requirements.txt
Database Migrations
Set up your initial database schema using Alembic:
```

```bash
alembic upgrade head
```
Ensure you have the correct database connection string in your Alembic configuration or environment variables.

## Running the Application
### Run the application using Uvicorn:

``` bash
uvicorn app.main:app --reload
``` 
This command will start the FastAPI application with live reloading enabled.

## Access the Application
Visit `http://127.0.0.1:8000` in your web browser to see the running application. For API documentation, navigate to `http://127.0.0.1:8000/docs`.

{{% notice note %}}
This website can be automatically published and hosted with [Github Pages](https://pages.github.com/). To learn more about it visit [Github pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
{{% /notice %}}