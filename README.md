# IDPHCS

IDPHCS This project leverages Django Rest Framework for robust API management and Django WebSocket for real-time Chat communication.

## Installation

Follow these steps to set up the project locally.

### Prerequisites

Ensure you have the following installed:

- Python 3.x
- pip
- virtualenv

### Steps

1. **Clone the repository**

    ```bash
    git clone https://github.com/yourusername/IDPHCS.git
    cd IDPHCS
    ```

2. **Create a virtual environment**

    ```bash
    python -m venv env
    source env/bin/activate   # On Windows use `env\Scripts\activate`
    ```

3. **Install dependencies**

    ```bash
    pip install -r requirements.txt
    ```

4. **Apply migrations**

    ```bash
    python manage.py migrate
    ```

5. **Run the development server**

    ```bash
    python manage.py runserver
    ```

## API Endpoints

### GET Endpoints

Here is a list of available GET API endpoints:

| Method | Endpoint                            | Description                         |
|--------|-------------------------------------|-------------------------------------|
| GET    | /auth/profile/                      | Retrieve user profile               |
| GET    | /auth/users/                        | Retrieve a list of users            |
| GET    | /auth/users/search/                 | Search for a user                   |
| GET    | /app/connections/                   | Retrieve all connections            |
| GET    | /app/connections/{id}/              | Retrieve a connection by ID         |
| GET    | /app/stories/                       | Retrieve a list of stories          |
| GET    | /app/stories/{id}/                  | Retrieve a story by ID              |
| GET    | /app/getstorybyid/{id}/             | Retrieve stories of connected users |
| GET    | /app/comments/{id}/                 | Retrieve a comment by ID            |
| GET    | /app/complains/                     | Retrieve all complains              |
| GET    | /app/complains/{id}/                | Retrieve a complain by ID           |
| GET    | /app/reports/                       | Retrieve all reports                |
| GET    | /app/reports/{id}/                  | Retrieve a report by ID             |
| GET    | /app/resources/                     | Retrieve all resources              |
| GET    | /app/resources/{id}/                | Retrieve a resource by ID           |
| GET    | /app/resources/user/{user_id}/      | Retrieve resources by user          |
| GET    | /app/announcements/                 | Retrieve all announcements          |
| GET    | /app/announcements/{id}/            | Retrieve an announcement by ID      |
| GET    | /app/announcements/user/{user_id}/  | Retrieve announcements by user      |
| GET    | /app/sharings/                      | Retrieve all sharings               |
| GET    | /app/sharings/{id}/                 | Retrieve a sharing by ID            |
| GET    | /auth/activate-user/{id}/           | Activate User Account               |
| GET    | /auth/deactivate/{id}/              | Deactivate User Account             |

### POST Endpoints

Here is a list of available POST API endpoints:

| Method | Endpoint                          | Description                            |
|--------|-----------------------------------|----------------------------------------|
| POST   | /auth/token/                      | Login                                  |
| POST   | /app/register-host/               | Register a host                        |
| POST   | /app/register_camp/               | Register a camp admin                  |
| POST   | /app/register-ngo/                | Register an NGO                        |
| POST   | /app/register_volunteer/          | Register a volunteer                   |
| POST   | /app/register_idppre/             | Register an IDP pre                    |
| POST   | /app/register_idp/                | Register an IDP                        |
| POST   | /app/connections/                 | Create a connection                    |
| POST   | /app/stories/                     | Create a story                         |
| POST   | /app/upload/images/               | Upload images                          |
| POST   | /app/comments/                    | Create a comment                       |
| POST   | /app/complains/                   | Create a complain                      |
| POST   | /app/reports/                     | Create a report                        |
| POST   | /app/resources/                   | Create a resource                      |
| POST   | /app/announcements/               | Create an announcement                 |
| POST   | /app/sharings/                    | Create a sharing                       |
| POST   | /accountmgt/update_password/      | Update users password                  |


### PUT Endpoints

Here is a list of available PUT API endpoints:

| Method | Endpoint                          | Description                            |
|--------|-----------------------------------|----------------------------------------|
| PUT    | /app/stories/{id}/                | Update a story                         |
| PUT    | /app/comments/{id}/update/        | Update a comment                       |
| PUT    | /app/complains/{id}/update/       | Update a complain                      |
| PUT    | /app/reports/{id}/update/         | Update a report                        |
| PUT    | /app/resources/{id}/update/       | Update a resource                      |
| PUT    | /app/resources/{id}/approve/      | Approve a resource                     |
| PUT    | /app/announcements/{id}/update/   | Update an announcement                 |
| PUT    | /app/sharings/{id}/update/        | Update a sharing                       |
| PUT    | /accountmgt/host/{id}/            | Update a host account                  |
| PUT    | /accountmgt/idp/{id}/             | Update an IDP account                  |
| PUT    | /accountmgt/ngo/{id}/             | Update an NGO account                  |
| PUT    | /accountmgt/camp/{id}/            | Update a camp admin account            |

### DELETE Endpoints

Here is a list of available DELETE API endpoints:

| Method | Endpoint                          | Description                            |
|--------|-----------------------------------|----------------------------------------|
| DELETE | /app/connections/{id}/delete/     | Delete a connection                    |
| DELETE | /app/stories/{id}/                | Delete a story                         |
| DELETE | /app/comments/{id}/delete/        | Delete a comment                       |
| DELETE | /app/complains/{id}/delete/       | Delete a complain                      |
| DELETE | /app/reports/{id}/delete/         | Delete a report                        |
| DELETE | /app/resources/{id}/delete/       | Delete a resource                      |
| DELETE | /app/announcements/{id}/delete/   | Delete an announcement                 |
| DELETE | /app/sharings/{id}/delete/        | Delete a sharing                       |

## API Endpoints Details

### GET Endpoints

#### 1. User Login

**Description:**  
Login for registered users.

**Endpoint:**  
`/auth/token/`

**Method:**  
POST

**Authentication Required:**  
NO

**JSON to be Sent:**  
```json
{
    "username":"username",
    "password":"password"
}
```

**JSON Received:**
```json
{
    "refresh": "refrest token",
    "access": "access token"
}
```

#### 2. Retrieve User Profile

**Description:**  
Retrieve the profile information of the authenticated user.

**Endpoint:**  
`/auth/profile/`

**Method:**  
GET

**Authentication Required:**  
Yes

**JSON to be Sent:**  
N/A (This endpoint does not require a JSON payload)

**JSON Received:**
User Profile in json


#### 3. Retrieve List of users

**Description:**  
Retrieve the List of all user name with id.

**Endpoint:**  
`/auth/users/`

**Method:**  
GET

**Authentication Required:**  
Yes

**JSON to be Sent:**  
N/A (This endpoint does not require a JSON payload)

**JSON Received:**

```json
[
    {
        "id": 2,
        "username": "anteneh"
    }
]
```
#### 4. Search Users

**Description:**  
API to search users by filtering first_name, last_name, email and phone_number

**Endpoint:**  
`/app/search-users/?phone_number=&first_name&last_name&email`

**Method:**  
GET

**Authentication Required:**  
Yes

**JSON to be Sent:**  
N/A (This endpoint does not require a JSON payload)

**JSON Received:**
Filtered User Profile in json
