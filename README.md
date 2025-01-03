
# Project Management API For TechForing

This is a project management API built using Django and Django REST Framework (DRF). It provides endpoints to manage users, projects, tasks, and comments. This API is designed to be consumed by web and mobile applications.

## Features

- **User Management**: Register, login, update, and delete users.
- **Project Management**: Create, retrieve, update, and delete projects.
- **Task Management**: Create, retrieve, update, and delete tasks within projects.
- **Comment Management**: Add, update, retrieve, and delete comments on tasks.

## Prerequisites

Before starting, ensure you have the following installed:

- Python 3.8 or higher
- Django 3.2 or higher
- Django REST Framework
- pip (Python package installer)
- Git (for cloning the repository)

## Installation Steps

### 1. Clone the Repository

Start by cloning this repository to your local machine:

```bash
git clone https://github.com/Shafiul-Sabbir/techforing_pm.git
```

### 2. Set up a Virtual Environment

It’s a good practice to use a virtual environment to manage your dependencies. If you don't have `virtualenv` installed, you can install it using:

```bash
pip install virtualenv
```

Then create and activate your virtual environment:

```bash
# Create a virtual environment
virtualenv venv

# Activate the virtual environment
# On macOS/Linux
source venv/bin/activate
# On Windows
source venv/Scripts/activate
```

### 3. Install Dependencies

Once the virtual environment is activated, install the required dependencies:

```bash
cd techforing_pm
pip install -r requirements.txt
```

The `requirements.txt` file includes Django, Django REST Framework, and other dependencies needed for the project.

### 4. Configure the Database

The project uses a database to store user, project, task, and comment information. For development purposes, SQLite is used by default.

To set up the database, run the following commands:

```bash
# Run database migrations to set up the schema
python manage.py makemigrations
python manage.py migrate
```

### 5. Create a Superuser

To interact with the admin panel and manage the application, you'll need a superuser account. Run the following command to create one:

```bash
python manage.py createsuperuser
```

You will be prompted to enter a username, email, and password for the superuser.

### 6. Start the Development Server

Now, you're ready to run the development server. Start it with:

```bash
python manage.py runserver
```

Your application will be running on `http://127.0.0.1:8000/` by default.

---

## API Documentation

### Authentication

- **Register User** (POST `/api/users/register/`): 
  - Register a new user by providing `username`, `email`, `password`, `first_name`, `last_name`.
  - Returns a user object for each successful registration.

- **Login User** (POST `/api/users/login/`):
  - Authenticate the user using `username` and `password`.
  - Returns a token that must be used for authentication in subsequent requests.

- **Get User Details** (GET `/api/users/{id}/`):
  - Retrieve the details of a specific user by providing their user `id`.

- **Update User** (PUT/PATCH `/api/users/{id}/`):
  - Update user details such as `first_name`, `last_name`, and `email`.

- **Delete User** (DELETE `/api/users/{id}/`):
  - Delete a specific user account.

### Projects

- **List Projects** (GET `/api/projects/`):
  - Retrieve a list of all projects.

- **Create Project** (POST `/api/projects/`):
  - Create a new project by providing `name`, `description`, and `owner_id` (User).

- **Retrieve Project** (GET `/api/projects/{id}/`):
  - Get details of a specific project by its `id`.

- **Update Project** (PUT/PATCH `/api/projects/{id}/`):
  - Update the project details.

- **Delete Project** (DELETE `/api/projects/{id}/`):
  - Delete a specific project.

### Tasks

- **List Tasks** (GET `/api/projects/{project_id}/tasks/`):
  - List all tasks within a specific project.

- **Create Task** (POST `/api/projects/{project_id}/tasks/`):
  - Create a new task under a project by providing task details like `title`, `description`, `status`, `priority`, `assigned_to`, and `due_date`.

- **Retrieve Task** (GET `/api/tasks/{id}/`):
  - Retrieve details of a specific task by its `id`.

- **Update Task** (PUT/PATCH `/api/tasks/{id}/`):
  - Update task details like `status`, `priority`, `assigned_to`, etc.

- **Delete Task** (DELETE `/api/tasks/{id}/`):
  - Delete a specific task.

### Comments

- **List Comments** (GET `/api/tasks/{task_id}/comments/`):
  - Retrieve a list of comments on a task.

- **Create Comment** (POST `/api/tasks/{task_id}/comments/`):
  - Add a new comment to a task by providing the `content`.

- **Retrieve Comment** (GET `/api/comments/{id}/`):
  - Retrieve details of a specific comment.

- **Update Comment** (PUT/PATCH `/api/comments/{id}/`):
  - Update comment content.

- **Delete Comment** (DELETE `/api/comments/{id}/`):
  - Delete a specific comment.

---

## Testing the API

You can test the API using tools like **Postman** or **cURL**.

Here’s how you can test the **Login** and **Task Management** API:

1. **Login:**
   - Send a `POST` request to `/api/users/login/` with `username` and `password`.
   - You will receive a token in the response.

2. **Using the Token:**
   - For subsequent requests, pass the token as a header in your requests:
     ```bash
     Authorization: Token <your_token_here>
     ```

3. **Create a Task:**
   - Send a `POST` request to `/api/projects/{project_id}/tasks/` with the task details. Don’t forget to include the `Authorization` token in the headers.

---

## Troubleshooting

- **Migrations fail**: If you encounter any issues with migrations, try deleting the SQLite database file (`db.sqlite3`) and running migrations again.
- **CORS errors**: If testing from a frontend app, ensure that CORS is correctly configured in the Django settings. You may need to install `django-cors-headers` for this.

---

## License

This project is licensed under shafiulsabbir95@gmail.com

---
