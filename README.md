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

### 1. User Login

**Description:**  Login for registered users.

**Endpoint:**  `/auth/token/`

**Method:**  POST

**Authentication Required:**  NO

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
### <span style="color: blue;">2. Retrieve User Profile</span>
**Description:**  
Retrieve the profile information of the authenticated user.

**Endpoint:**  `/auth/profile/`

**Method:**  GET

**Authentication Required:**  Yes

**JSON to be Sent:**  
N/A (This endpoint does not require a JSON payload)

**JSON Received:**
User Profile in json


### 3. Retrieve List of users

**Description:**  Retrieve the List of all user name with id.

**Endpoint:**  `/auth/users/`

**Method:**  GET

**Authentication Required:**  Yes

**JSON to be Sent:**  N/A (This endpoint does not require a JSON payload)

**JSON Received:**

```json
[
    {
        "id": 2,
        "username": "anteneh"
    }
]
```
### 4. Search Users

**Description:**  API to search users by filtering first_name, last_name, email and phone_number

**Endpoint:**  `/app/search-users/?phone_number=&first_name&last_name&email`

**Method:**  GET

**Authentication Required:**  Yes

**JSON to be Sent:**  N/A (This endpoint does not require a JSON payload)

**JSON Received:** Filtered User Profile in json

### 5. Search Users

**Description:**  API to search users by filtering first_name, last_name, email and phone_number

**Endpoint:**  `/app/search-users/?phone_number=&first_name&last_name&email`

**Method:**  GET

**Authentication Required:**  Yes

**JSON to be Sent:**  N/A (This endpoint does not require a JSON payload)

**JSON Received:**    Filtered User Profile in json


### 6. Register Host

**Description:**  API to Register Host

**Endpoint:**  `/auth/register-host/`

**Method:**  POST

**Authentication Required:**  Yes

**JSON to be Sent:**  
```json
{
    "username": "string",
    "email": "email",
    "password": "password",
    "firstname": "string",
    "lastname": "string",
    "capacity": int,
    "preference": "string",
    "language": "string",
    "hosting_experience": "string",
    "location": "string",
    "contact_info": "string",
    "legal_doc_id": "string",
    "economic_status": "string",
    "phone_number": "string",
    "user_type": "Host"
}
```

**JSON Received:**  Json with user id

### 7. Register Camp Admin 

**Description:**  API to Register Camp Admin

**Endpoint:**  `/auth/register_camp/`

**Method:**  POST

**Authentication Required:**  Yes

**JSON to be Sent:**  
```json
{
    "username": "string",
    "email": "email",
    "password": "password",
    "firstname": "string",
    "lastname": "string",
    "name": "string",
    "location": "string",
    "capacity": int,
    "current_population": int,
    "demographic_info": "string",
    "shelter_type": "string",
    "economic_activities": "string",
    "health_education_info": "string",
    "status": "string",
    "phone_number": "string",
    "user_type": "Camp Admin"
}

```

**JSON Received:**    Json with user id

### 8. Register NGO

**Description:**  API to Register NGO 

**Endpoint:**  `/auth/register-ngo/`

**Method:**  POST

**Authentication Required:**  Yes

**JSON to be Sent:**  
```json
{
    "username": "sting",
    "email": "email",
    "password": "password",
    "name": "string",
    "location": "string",
    "capacity": int,
    "legal_doc": "string",
    "country": "sting",
    "status": "Active",
    "phone_number": "string",
    "user_type": "NGO"
}
```
**JSON Received:**    Json with user id

### 9. Register Volunteer

**Description:**  API to Register Volunteer

**Endpoint:**  `/auth/register_volunteer/`

**Method:**  POST

**Authentication Required:**  Yes

**JSON to be Sent:**  
```json
{
    "username": "string",
    "email": "email",
    "password": "password",
    "firstname": "string",
    "lastname": "string",
    "location": "string",
    "phone_number": "string",
    "user_type": "Volunteer"
}

```
**JSON Received:** Json with user id


### 10. IDP Pre Registration

**Description:**  API to register IDP Pre registration for verification

**Endpoint:**  `/auth/register_idppre/`

**Method:**  POST

**Authentication Required:**  Yes

**JSON to be Sent:**  
```json
{
    "first_name": "string",
    "last_name": "string",
    "email": "email",
    "phone_number": "string"
}

```

**JSON Received:**    Json with user id

### 11. IDP registration

**Description:**  API to Register IDP

**Endpoint:**  `/auth/register_idp/`

**Method:**  POST

**Authentication Required:**  Yes

**JSON to be Sent:**  
```json
{
    "username": "string",
    "password": "string",
    "email": "email",  // Ensure this matches an existing IDPPre entry
    "firstname": "string",
    "lastname": "string",
    "location": "string",
    "phone_number": "string",
    "place_of_origin": "string",
    "contact_information": "string",
    "household_composition": int,
    "vulnerability_status": "string",
    "health_status": "string",
    "documentation_status": "string",
    "education_level": "string",
    "language_spoken": "string",
    "previous_assistance_received": "string",
    "protection_concerns": "string",
    "economic_status": "string",
    "is_verified": false,
    "age": int,
    "gender": "Male/ Female",
    "user_type": "IDP"
}

```
**JSON Received:**    Json with user id
    
### 12. Deactivate User Account

**Description:**  API to Deactivate User Account and only used by super admin

**Endpoint:**  `/auth/deactivate-user/user_id/`

**Method:**  GET

**Authentication Required:**  Yes

**JSON to be Sent:**  N/A (This endpoint does not require a JSON payload)

**JSON Received:**
```json
{
    "message": "User deactivated successfully"
}
```
### 13. Activate User Account

**Description:**  API to Activate User Account and only used by super admin

**Endpoint:**  `/auth/activate-user/user_id/`

**Method:**  GET

**Authentication Required:**  Yes

**JSON to be Sent:**  N/A (This endpoint does not require a JSON payload)

**JSON Received:**
```json
{
    "message": "User activated successfully"
}
```


### 14. Update Host Account

**Description:**  API to Update the Host information

**Endpoint:**  `/accountmgt/hosts/id/`

**Method:**  PUT

**Authentication Required:**  Yes

**JSON to be Sent:**
```json
{
  "capacity": int,
  "preference": "string",
  "language": "string",
  "hosting_experience": "string",
  "location": "string",
  "contact_info": "string",
  "legal_doc_id": "string",
  "economic_status": "string"
}

```

**JSON Received:** Json with user id

### 15. Update IDP Account

**Description:**  API to update the IDP Account

**Endpoint:**  `/accountmgt/idps/id/`

**Method:**  PUT

**Authentication Required:**  Yes

**JSON to be Sent:**  
```json
{
  "place_of_origin": "string",
  "contact_information": "string",
  "household_composition": int,
  "vulnerability_status": "string",
  "health_status": "string",
  "documentation_status": "string",
  "education_level": "string",
  "language_spoken": "string",
  "previous_assistance_received": "string",
  "protection_concerns": "string",
  "economic_status": "string",
  "is_verified": true,
  "age": 30,
  "gender": "Female"
}

```

**JSON Received:** Json with user id

### 16. Update NGO Account

**Description:**  API to Update NGO Account

**Endpoint:**  `/accountmgt/ngos/id/`

**Method:**  PUT

**Authentication Required:**  Yes

**JSON to be Sent:** 
```json
{
  "location": "string",
  "capacity": int,
  "name": "string",
  "legal_doc": "string",
  "country": "string",
  "status": "Active"
}

```

**JSON Received:** Json with user id

### 17.  update Camp Account

**Description:**  API to update camp account

**Endpoint:**  `/accountmgt/camps/id/`

**Method:**  PUT

**Authentication Required:**  Yes

**JSON to be Sent:**  
```json
{
  "name": "string",
  "location": "string",
  "capacity": int,
  "current_population": int,
  "demographic_info": "string",
  "shelter_type": "string",
  "economic_activities": "string",
  "health_education_info": "string",
  "status": "string"
}

```

**JSON Received:**  Json with user id

### 18. Profile image upload 

**Description:**  API to upload the user profile image

**Endpoint:**  `/accountmgt/upload_image/`

**Method:**  POST

**Authentication Required:**  Yes

**JSON to be Sent:**  Form data with "image"
**JSON Received:** Status of 200 with data json

### 19. Change Password

**Description:**  API to Change the user password

**Endpoint:**  `/accountmgt/update_password/`

**Method:**  PUT

**Authentication Required:**  Yes

**JSON to be Sent:**  
```json
{
  "old_password": "old_password",
  "new_password": "new_password"
}

```

**JSON Received:** 
```json
{
    "message": "Password updated successfully"
}
```

### 20. Get Messages

**Description:** API to retrieve messages between the authenticated user and another specified user.

**Endpoint:** `/messages/<int:other_party_id>/`

**Method:** GET

**Authentication Required:** Yes

**JSON to be Sent:** N/A (This endpoint does not require a JSON payload)

**JSON Received:**
```json
[
    {
        "id": 1,
        "sender": {
            "name": "sender_username"
        },
        "receiver": {
            "name": "receiver_username"
        },
        "message_text": "Hello!",
        "sent_at": "2023-01-01T12:00:00Z"
    }
]
```

### 21. Create Connection

**Description:** API to create a new connection between two users. This endpoint will either create a new connection if none exists between the specified users, or reactivate an inactive connection.

**Endpoint:** `/connections/create/`

**Method:** POST

**Authentication Required:** Yes

**Permissions:** User must be authenticated.

**JSON to be Sent:**
Provide the `follower` and `followed_by` user IDs to establish a connection. The `follower` is the user who initiates the follow, and `followed_by` is the user who is being followed.
```json
{
    "follower": "<user_id>",
    "followed_by": "<user_id>"
}
```

**JSON Received:**
```json
{
    "id": "<connection_id>",
    "follower": "<follower_user_id>",
    "followed_by": "<followed_by_user_id>",
    "created_at": "<timestamp>",
    "current_status": true
}
```
### 22. Get Connections

**Description:** API to retrieve all existing connections for the authenticated user. This endpoint lists all connections, detailing each connection's information including both user profiles.

**Endpoint:** `/connections/`

**Method:** GET

**Authentication Required:** Yes

**Permissions:** User must be authenticated to view their connections.

**JSON to be Sent:** N/A (This endpoint does not require a JSON payload)

**Successful Response:**
The API returns a list of connections, each including the detailed profiles of the follower and followed_by users, the creation date, and the current status of the connection.
```json
[
    {
        "id": "<connection_id>",
        "follower": {
            "id": "<follower_user_id>",
            "username": "<username>",
            "email": "<email>"
        },
        "followed_by": {
            "id": "<followed_by_user_id>",
            "username": "<username>",
            "email": "<email>"
        },
        "created_at": "<timestamp>",
        "current_status": "<status>"
    },
    ...
]
```

### 23. Get Connection by ID

**Description:** API to retrieve details of a specific connection by its ID. This endpoint provides detailed information about both connected users along with the connection status and creation timestamp.

**Endpoint:** `/connections/<int:connection_id>/`

**Method:** GET

**Authentication Required:** Yes

**Permissions:** User must be authenticated and should ideally be one of the users in the connection to access this information.

**JSON to be Sent:** N/A (This endpoint does not require a JSON payload)

**Successful Response:**
The API returns detailed information about the specific connection including the profiles of the involved users.
```json
{
    "id": "<connection_id>",
    "follower": {
        "id": "<follower_user_id>",
        "username": "<username>",
        "email": "<email>"
    },
    "followed_by": {
        "id": "<followed_by_user_id>",
        "username": "<username>",
        "email": "<email>"
    },
    "created_at": "<timestamp>",
    "current_status": "<status>"
}
```

## 24. Delete Connection

**Description:** API to delete a specific connection by its ID. This endpoint allows users to remove a connection, effectively disabling any interactions that depend on this connection status.

**Endpoint:** `/connections/<int:connection_id>/delete/`

**Method:** DELETE

**Authentication Required:** Yes

**Permissions:** User must be authenticated and should ideally have the rights to modify this connection, either as one of the users in the connection or as an admin.

**JSON to be Sent:** N/A (This endpoint does not require a JSON payload)

**Successful Response:**
```json
{
    "message": "Connection deleted successfully"
}
```

## 25. List and Create Stories

**Description:** API to either retrieve all stories or create a new story, depending on the HTTP method used. This dual-function endpoint supports viewing all available stories in a summarized format and adding new stories as per user submissions.

**Endpoint:** `/stories/`

**Method:** GET for listing stories, POST for creating a new story.

**Authentication Required:** Yes

**Permissions:** All authenticated users can retrieve stories, but only users with specific roles or permissions (e.g., actors or storytellers) can create stories.

**JSON to be Sent for POST:**
```json
{
    "story_text": "Your story text here",
    "photos": ["url1", "url2"]  // Optional: URLs of photos associated with the story
}
```
**Successful Response for GET:**

```json
[
    {
        "id": 1,
        "idp_info": {
            "id": 123,
            "username": "user123",
            "email": "user@example.com"
        },
        "story_text": "An interesting event...",
        "shared_at": "2022-01-01T12:00:00Z",
        "created_at": "2022-01-01T12:00:00Z",
        "photos": ["http://example.com/photo1.jpg", "http://example.com/photo2.jpg"],
        "comments": [
            {
                "id": 1,
                "text": "Great story!",
                "author_id": 123,
                "created_at": "2022-01-02T12:00:00Z"
            }
        ]
    }
]
```
**Successful Response for POST:**
```json
{
    "id": 2,
    "story_text": "Your newly submitted story text",
    "idp": 456,
    "photos": [],
    "comments": []
}
```

## 26. Update and Delete Story

**Description:** API to update or delete a specific story, depending on the HTTP method used. This endpoint allows for modifying or removing an existing story based on its unique identifier.

**Endpoint:** `/stories/<pk>/`

**Method:** PUT for updating a story, DELETE for deleting a story.

**Authentication Required:** Yes

**Permissions:** Only the owner of the story or users with specific roles (e.g., administrators) can update or delete the story.

**JSON to be Sent for PUT:**
```json
{
    "story_text": "Updated story text here",
    "photos": ["updated_url1", "updated_url2"]  // Optional: Updated URLs of photos associated with the story
}
```
**Successful Response for PUT:**
```json
{
    "message": "Story updated successfully"
}

```
**Successful Response for DELETE:**
```json
{
    "message": "Story deleted successfully"
}

```

## 27. Retrieve Story by ID

**Description:** API to fetch a single story by its unique identifier. It returns the story details along with information about the IDP (Identity Provider) associated with the story, photos, and comments.

**Endpoint:** `/stories/<story_id>/`

**Method:** GET

**Authentication Required:** No

**Permissions:** None required, but this can be adjusted to include authentication if sensitive data is involved.

**Successful Response:**
```json
{
    "id": "story_id",
    "idp_info": {
        "id": "user_id",
        "username": "username",
        "email": "user@example.com"
    },
    "story_text": "Here is the story text...",
    "shared_at": "date_time",
    "created_at": "date_time",
    "photos": [
        "photo_url1",
        "photo_url2"
    ],
    "comments": [
        {
            "comment_id": 1,
            "user_id": 2,
            "text": "Great story!",
            "created_at": "date_time"
        }
    ]
}
```
## 28. Upload Images

**Description:** API to upload multiple images associated with a specific story. Users can upload several images at once which are then linked to the given story ID.

**Endpoint:** `/stories/<story_id>/upload-images/`

**Method:** POST

**Authentication Required:** Yes

**Permissions:** Must be authenticated to upload images.

**Payload:**
- `images`: A list of image files to be uploaded.

**Successful Response:**
```json
[
    {
        "image_url": "url_to_uploaded_image",
        "created_at": "timestamp",
        "status": "Active",
        "story_id": "related_story_id"
    }
]
```
## 29. Get Story by ID

**Description:** API to retrieve a specific story along with associated information such as the IDP details, story text, shared date, and uploaded photos.

**Endpoint:** `/stories/<story_id>/`

**Method:** GET

**Authentication Required:** No

**Parameters:**
- `story_id`: The ID of the story to retrieve.

**JSON Response:**
```json
{
    "id": "story_id",
    "idp_info": {
        "id": "idp_user_id",
        "username": "idp_username",
        "email": "idp_email"
    },
    "story_text": "story_text",
    "shared_at": "shared_timestamp",
    "created_at": "created_timestamp",
    "photos": [
        "photo_url_1",
        "photo_url_2",
        "photo_url_3"
    ],
    "comments": [
        {
            "id": "comment_id",
            "user": "commenter_username",
            "comment_text": "comment_text",
            "commented_at": "commented_timestamp"
        },
        {
            ...
        }
    ]
}
```
## 30. Upload Images for Story

**Description:** API to upload images associated with a story.

**Endpoint:** `/upload_images/<story_id>/`

**Method:** POST

**Authentication Required:** Yes

**Parameters:**
- `story_id`: The ID of the story to which the images will be uploaded.

**Request Body:** FormData containing one or multiple image files with the key `images`.

**JSON Response:**
```json
[
    {
        "id": "photo_id",
        "image_url": "image_url",
        "created_at": "created_timestamp",
        "deleted_at": null,
        "status": "Active",
        "story": "story_id"
    },
    {
        ...
    }
]
```
## 31. Create Comment

**Description:** API to create a comment for a story.

**Endpoint:** `/comments/`

**Method:** POST

**Authentication Required:** Yes

**Request Body:**
```json
{
    "post": "story_id",
    "comment_text": "Your comment text here"
}
```
**Json Response:**
```json
{
    "id": "comment_id",
    "user": "user_id",
    "post": "story_id",
    "comment_text": "Your comment text here",
    "commented_at": "created_timestamp",
    "created_at": "created_timestamp",
    "deleted_at": null,
    "status": "active"
}
```
## 32. Get Comment by ID

**Description:** API to retrieve a comment by its ID.

**Endpoint:** `/comments/<comment_id>/`

**Method:** GET

**Authentication Required:** Yes

**URL Parameters:**
- `comment_id` (integer): The ID of the comment to retrieve.

**JSON Response:**
```json
{
    "id": "comment_id",
    "user": "user_id",
    "post": "story_id",
    "comment_text": "Comment text here",
    "commented_at": "commented_timestamp",
    "created_at": "created_timestamp",
    "deleted_at": null,
    "status": "active"
}
```

## 33. Update Comment

**Description:** API to update a comment.

**Endpoint:** `/comments/<comment_id>/update/`

**Method:** PUT

**Authentication Required:** Yes

**URL Parameters:**
- `comment_id` (integer): The ID of the comment to update.

**JSON Payload:**
```json
{
    "comment_text": "Updated comment text"
}
```
**JSON Response:**
```json
{
    "id": "comment_id",
    "user": "user_id",
    "post": "story_id",
    "comment_text": "Updated comment text",
    "commented_at": "updated_timestamp",
    "created_at": "original_created_timestamp",
    "deleted_at": null,
    "status": "active"
}
```
## 34. Delete Comment

**Description:** API to delete a comment.

**Endpoint:** `/comments/<comment_id>/delete/`

**Method:** DELETE

**Authentication Required:** Yes

**URL Parameters:**
- `comment_id` (integer): The ID of the comment to delete.

**JSON Response:**
```json
{
    "message": "Comment deleted successfully"
}
```

## 35. Create Complain

**Description:** API to create a complain.

**Endpoint:** `/complains/`

**Method:** POST

**Authentication Required:** Yes

**JSON to be Sent:**
```json
{
    "complained_to": <user_id>,
    "description": "Description of the complaint"
}
```

**JSON Response:**
```json
{
    "id": 1,
    "complained_by": {
        "username": "user1",
        "email": "user1@example.com"
    },
    "complained_to": {
        "username": "user2",
        "email": "user2@example.com"
    },
    "description": "Description of the complaint",
    "created_at": "2024-05-21T12:00:00Z",
    "deleted_at": null,
    "status": "Active"
}
```

## 36. Get All Complains

**Description:** API to retrieve all complaints.

**Endpoint:** `/complains/all/`

**Method:** GET

**Authentication Required:** Yes

**JSON Response Example:**
```json
[
    {
        "id": 1,
        "complained_by": {
            "username": "user1",
            "email": "user1@example.com"
        },
        "complained_to": {
            "username": "user2",
            "email": "user2@example.com"
        },
        "description": "Description of the complaint",
        "created_at": "2024-05-21T12:00:00Z",
        "deleted_at": null,
        "status": "Active"
    },
    {
        "id": 2,
        "complained_by": {
            "username": "user3",
            "email": "user3@example.com"
        },
        "complained_to": {
            "username": "user4",
            "email": "user4@example.com"
        },
        "description": "Another complaint description",
        "created_at": "2024-05-22T10:00:00Z",
        "deleted_at": null,
        "status": "Active"
    }
]
```

## 37. Get Complain by ID

**Description:** API to retrieve a complaint by its ID.

**Endpoint:** `/complains/<complain_id>/`

**Method:** GET

**Authentication Required:** Yes

**URL Parameter:** 
- `complain_id`: ID of the complaint to retrieve.

**JSON Response Example (Success):**
```json
{
    "id": 1,
    "complained_by": {
        "username": "user1",
        "email": "user1@example.com"
    },
    "complained_to": {
        "username": "user2",
        "email": "user2@example.com"
    },
    "description": "Description of the complaint",
    "created_at": "2024-05-21T12:00:00Z",
    "deleted_at": null,
    "status": "Active"
}
```

## 38. Update Complain

**Description:** API to update an existing complaint.

**Endpoint:** `/complains/<complain_id>/update/`

**Method:** PUT

**Authentication Required:** Yes

**URL Parameter:** 
- `complain_id`: ID of the complaint to update.

**JSON to be Sent:**
```json
{
    "description": "Updated description of the complaint",
    "status": "Resolved"
}
```
**JSON Response:**

```json
{
    "id": 1,
    "complained_by": {
        "username": "user1",
        "email": "user1@example.com"
    },
    "complained_to": {
        "username": "user2",
        "email": "user2@example.com"
    },
    "description": "Updated description of the complaint",
    "created_at": "2024-05-21T12:00:00Z",
    "deleted_at": null,
    "status": "Resolved"
}
```

## 39. Delete Complain

**Description:** API to delete an existing complaint.

**Endpoint:** `/complains/<complain_id>/delete/`

**Method:** DELETE

**Authentication Required:** Yes

**URL Parameter:** 
- `complain_id`: ID of the complaint to delete.

**JSON Response Example (Success):**
```json
{
    "message": "Complain deleted successfully"
}
```

## 40. Get All Reports

**Description:** API to retrieve all reports in the system.

**Endpoint:** `/reports/all/`

**Method:** GET

**Authentication Required:** Yes

**JSON Response Example (Success):**
```json
[
    {
        "id": 1,
        "reported_by": {
            "id": 1,
            "username": "reported_by_username",
            "email": "reported_by_email@example.com"
        },
        "reported_to": {
            "id": 2,
            "username": "reported_to_username",
            "email": "reported_to_email@example.com"
        },
        "description": "Description of the report.",
        "created_at": "2024-05-21T12:00:00Z"
    },
    {
        "id": 2,
        "reported_by": {
            "id": 3,
            "username": "reported_by_username",
            "email": "reported_by_email@example.com"
        },
        "reported_to": {
            "id": 1,
            "username": "reported_to_username",
            "email": "reported_to_email@example.com"
        },
        "description": "Description of the report.",
        "created_at": "2024-05-21T12:05:00Z"
    }
]
```

## 41. Get Report By ID

**Description:** This endpoint retrieves a report by its unique ID.

**Endpoint:** `/reports/{report_id}/`

**Method:** GET

**Authentication Required:** Yes

### Parameters

- `report_id`: The unique identifier of the report.

**Success Response:**

- **Code:** 200 OK
- **Content:** 
  ```json
  {
      "id": 1,
      "reported_by": {
          "id": 1,
          "username": "reported_by_username",
          "email": "reported_by_email@example.com"
      },
      "reported_to": {
          "id": 2,
          "username": "reported_to_username",
          "email": "reported_to_email@example.com"
      },
      "description": "Description of the report.",
      "created_at": "2024-05-21T12:00:00Z"
  }
``

## 42. Update Report

**Description:** This endpoint updates an existing report.

**Endpoint:** `/reports/{report_id}/`

**Method:** PUT

**Authentication Required:** Yes

### Parameters

- `report_id`: The unique identifier of the report to be updated.

**Request Body:**

- `description` (optional): Updated description of the report.

**Success Response:**

- **Code:** 200 OK
- **Content:** 
  ```json
  {
      "id": 1,
      "reported_by": {
          "id": 1,
          "username": "reported_by_username",
          "email": "reported_by_email@example.com"
      },
      "reported_to": {
          "id": 2,
          "username": "reported_to_username",
          "email": "reported_to_email@example.com"
      },
      "description": "Updated description of the report.",
      "created_at": "2024-05-21T12:00:00Z"
  }
``

## 43. Delete Report

**Description:** This endpoint deletes an existing report.

**Endpoint:** `/reports/{report_id}/`

**Method:** DELETE

**Authentication Required:** Yes

### Parameters

- `report_id`: The unique identifier of the report to be deleted.

**Success Response:**

- **Code:** 200 OK
- **Content:** 
  ```json
  {
      "message": "Report deleted successfully"
  }
``
## 44. Get Connected Stories

**Description:** This endpoint retrieves stories from users followed by the current user.

**Endpoint:** `/connected_stories/`

**Method:** GET

**Authentication Required:** Yes

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    [
        {
            "id": 1,
            "idp_info": {
                "id": 1,
                "username": "example_user",
                "email": "example@example.com"
            },
            "story_text": "This is a sample story text.",
            "shared_at": "2024-05-21T12:30:00Z",
            "created_at": "2024-05-20T10:00:00Z",
            "photos": [
                "https://example.com/photo1.jpg",
                "https://example.com/photo2.jpg"
            ],
            "comments": [
                {
                    "id": 1,
                    "user": {
                        "id": 2,
                        "username": "commenter",
                        "email": "commenter@example.com"
                    },
                    "text": "Great story!",
                    "created_at": "2024-05-21T13:00:00Z"
                },
                {
                    "id": 2,
                    "user": {
                        "id": 3,
                        "username": "another_commenter",
                        "email": "another_commenter@example.com"
                    },
                    "text": "I enjoyed reading this.",
                    "created_at": "2024-05-21T13:15:00Z"
                }
            ]
        },
        {
            "id": 2,
            "idp_info": {
                "id": 2,
                "username": "another_user",
                "email": "another@example.com"
            },
            "story_text": "Another sample story.",
            "shared_at": "2024-05-22T09:45:00Z",
            "created_at": "2024-05-22T08:00:00Z",
            "photos": [],
            "comments": []
        }
    ]
    ```
- **Error Response:**

  - **Code:** 401 UNAUTHORIZED
  - **Content:** 
    ```json
    {
        "detail": "Authentication credentials were not provided."
    }
    ```
## 45. Search Users

**Description:** This endpoint allows searching for users based on various criteria such as first name, last name, email, or phone number.

**Endpoint:** `/search_users/`

**Method:** GET

**Authentication Required:** Yes

### Query Parameters

- `first_name`: First name of the user (optional)
- `last_name`: Last name of the user (optional)
- `email`: Email address of the user (optional)
- `phone_number`: Phone number of the user (optional)

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    [
        {
            "id": 1,
            "first_name": "John",
            "last_name": "Doe",
            "email": "john.doe@example.com",
            "actor_profile": {
                "location": "New York",
                "phone_number": "1234567890"
            },
            "profile_image": "https://example.com/profile_image.jpg"
        },
        {
            "id": 2,
            "first_name": "Alice",
            "last_name": "Smith",
            "email": "alice.smith@example.com",
            "actor_profile": {
                "location": "Los Angeles",
                "phone_number": "9876543210"
            },
            "profile_image": "https://example.com/profile_image.jpg"
        }
    ]
    ```
- **Error Response:**

  - **Code:** 401 UNAUTHORIZED
  - **Content:** 
    ```json
    {
        "detail": "Authentication credentials were not provided."
    }
    ```
## 46. Create Resource

**Description:** This endpoint allows creating a new resource.

**Endpoint:** `/create_resource/`

**Method:** POST

**Authentication Required:** Yes

### Request Body

- `name` (required): Name of the resource.
- `description` (optional): Description of the resource.
- `provider_id` (required): ID of the user who is providing the resource.
- `provided_to_id` (required): ID of the user to whom the resource is provided.

### Response

- **Success Response:**

  - **Code:** 201 CREATED
  - **Content:** 
    ```json
    {
        "id": 1,
        "name": "Resource Name",
        "description": "Resource Description",
        "provider": {
            "id": 1,
            "username": "provider_username",
            "email": "provider@example.com"
        },
        "provided_to": {
            "id": 2,
            "username": "receiver_username",
            "email": "receiver@example.com"
        }
    }
    ```
- **Error Response:**

  - **Code:** 400 BAD REQUEST
  - **Content:** 
    ```json
    {
        "error": "Invalid request body"
    }
    ```

## 47. Get Resource

**Description:** This endpoint retrieves information about a specific resource by its ID.

**Endpoint:** `/get_resource/<resource_id>/`

**Method:** GET

**Authentication Required:** Yes

### URL Parameters

- `resource_id` (required): The ID of the resource to retrieve.

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    {
        "id": 1,
        "name": "Resource Name",
        "description": "Resource Description",
        "provider": {
            "id": 1,
            "username": "provider_username",
            "email": "provider@example.com"
        },
        "provided_to": {
            "id": 2,
            "username": "receiver_username",
            "email": "receiver@example.com"
        }
    }
    ```
- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Resource not found"
    }
    ```

## 48. Get All Resources

**Description:** This endpoint retrieves information about all available resources.

**Endpoint:** `/get_all_resources/`

**Method:** GET

**Authentication Required:** Yes

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    [
        {
            "id": 1,
            "name": "Resource Name 1",
            "description": "Resource Description 1",
            "provider": {
                "id": 1,
                "username": "provider_username",
                "email": "provider@example.com"
            },
            "provided_to": {
                "id": 2,
                "username": "receiver_username",
                "email": "receiver@example.com"
            }
        },
        {
            "id": 2,
            "name": "Resource Name 2",
            "description": "Resource Description 2",
            "provider": {
                "id": 3,
                "username": "provider2_username",
                "email": "provider2@example.com"
            },
            "provided_to": {
                "id": 4,
                "username": "receiver2_username",
                "email": "receiver2@example.com"
            }
        }
    ]
    ```
- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "No resources found"
    }
    ```

## 49. Update Resource

**Description:** This endpoint updates an existing resource.

**Endpoint:** `/update_resource/<resource_id>/`

**Method:** PUT

**Authentication Required:** Yes

### Request

- **Body:**
  - Provide the fields to be updated in the resource.

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    {
        "id": 1,
        "name": "Updated Resource Name",
        "description": "Updated Resource Description",
        "provider": {
            "id": 1,
            "username": "provider_username",
            "email": "provider@example.com"
        },
        "provided_to": {
            "id": 2,
            "username": "receiver_username",
            "email": "receiver@example.com"
        }
    }
    ```
- **Error Response:**

  - **Code:** 400 BAD REQUEST
  - **Content:** 
    ```json
    {
        "message": "Invalid data provided"
    }
    ```
  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Resource not found"
    }
    ```
## 50. Delete Resource

**Description:** This endpoint deletes an existing resource.

**Endpoint:** `/delete_resource/<resource_id>/`

**Method:** DELETE

**Authentication Required:** Yes

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    {
        "message": "Resource deleted successfully"
    }
    ```
- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Resource not found"
    }
    ```

## 51. Approve Resource

**Description:** This endpoint approves a resource, marking it as approved for use.

**Endpoint:** `/approve_resource/<resource_id>/`

**Method:** PUT

**Authentication Required:** Yes

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    {
        "message": "Resource approved successfully"
    }
    ```
- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Resource not found"
    }
    ```

## 52. Get Resources by User

**Description:** This endpoint retrieves all resources provided by or provided to a specific user.

**Endpoint:** `/get_resources_by_user/<user_id>/`

**Method:** GET

**Authentication Required:** Yes

### Parameters

- `user_id` (integer): The unique identifier of the user whose resources are to be retrieved.

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    {
        "provided_resources": [
            {
                "id": 1,
                "name": "Resource Name",
                "description": "Resource Description",
                "provider": {
                    "id": 1,
                    "username": "provider_username",
                    "email": "provider_email@example.com"
                },
                "provided_to": {
                    "id": 2,
                    "username": "recipient_username",
                    "email": "recipient_email@example.com"
                }
            },
            ...
        ],
        "received_resources": [
            {
                "id": 3,
                "name": "Resource Name",
                "description": "Resource Description",
                "provider": {
                    "id": 2,
                    "username": "provider_username",
                    "email": "provider_email@example.com"
                },
                "provided_to": {
                    "id": 1,
                    "username": "recipient_username",
                    "email": "recipient_email@example.com"
                }
            },
            ...
        ]
    }
    ```
- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "User not found"
    }
    ```

## 53. Approve Resource

**Description:** This endpoint approves a resource.

**Endpoint:** `/approve_resource/<resource_id>/`

**Method:** PUT

**Authentication Required:** Yes

### Parameters

- `resource_id` (integer): The unique identifier of the resource to be approved.

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    {
        "message": "Resource approved successfully"
    }
    ```
- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Resource not found"
    }
    ```
## 54. Get Resources by User

**Description:** This endpoint retrieves resources provided by and provided to a specific user.

**Endpoint:** `/get_resources_by_user/<user_id>/`

**Method:** GET

**Authentication Required:** Yes

### Parameters

- `user_id` (integer): The unique identifier of the user.

### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    {
        "provided_resources": [
            {
                "id": 1,
                "name": "Resource 1",
                "provider": {
                    "id": 1,
                    "username": "provider1",
                    "email": "provider1@example.com"
                },
                "provided_to": {
                    "id": 2,
                    "username": "user2",
                    "email": "user2@example.com"
                }
            }
        ],
        "received_resources": [
            {
                "id": 2,
                "name": "Resource 2",
                "provider": {
                    "id": 2,
                    "username": "provider2",
                    "email": "provider2@example.com"
                },
                "provided_to": {
                    "id": 1,
                    "username": "user1",
                    "email": "user1@example.com"
                }
            }
        ]
    }
    ```
- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "User not found"
    }
    ```


### 55. Create Announcement

**Description:** This endpoint allows authenticated users to create announcements.

**Endpoint:** `/create_announcement/`

**Method:** POST

**Authentication Required:** Yes

#### Request Body

- `created_by` (integer): The ID of the user who creates the announcement.

#### Response

- **Success Response:**

  - **Code:** 201 CREATED
  - **Content:** JSON object representing the created announcement.

- **Error Response:**

  - **Code:** 400 BAD REQUEST
  - **Content:** 
    ```json
    {
        "error": "created_by field is required"
    }
    ```
    OR
    ```json
    {
        "error": "Invalid created_by user"
    }
    ```

### 56. Get All Announcements

**Description:** This endpoint retrieves all announcements.

**Endpoint:** `/get_all_announcements/`

**Method:** GET

**Authentication Required:** Yes

#### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** JSON array containing serialized announcements.

### 57. Get Announcement by ID

**Description:** This endpoint retrieves a specific announcement by its ID.

**Endpoint:** `/get_announcement_by_id/<pk>/`

**Method:** GET

**Authentication Required:** Yes

#### Parameters

- `pk` (integer): The ID of the announcement.

#### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** JSON object representing the announcement.

- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Announcement not found"
    }
    ```

### 58. Get Announcements by Created By

**Description:** This endpoint retrieves announcements created by a specific user.

**Endpoint:** `/get_announcements_by_created_by/<id>/`

**Method:** GET

**Authentication Required:** Yes

#### Parameters

- `id` (integer): The ID of the user who created the announcements.

#### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** JSON array containing serialized announcements.

- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "User not found"
    }
    ```

### 59. Update Announcement

**Description:** This endpoint allows authenticated users to update an existing announcement.

**Endpoint:** `/update_announcement/<announcement_id>/`

**Method:** PUT

**Authentication Required:** Yes

#### Parameters

- `announcement_id` (integer): The ID of the announcement to be updated.

#### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** JSON object representing the updated announcement.

- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Announcement not found"
    }
    ```

### 60. Delete Announcement

**Description:** This endpoint allows authenticated users to delete an existing announcement.

**Endpoint:** `/delete_announcement/<announcement_id>/`

**Method:** DELETE

**Authentication Required:** Yes

#### Parameters

- `announcement_id` (integer): The ID of the announcement to be deleted.

#### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    {
        "message": "Announcement deleted successfully"
    }
    ```

- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Announcement not found"
    }
    ```

## Sharing Management

### 61. Create Sharing

**Description:** This endpoint allows authenticated users to create sharing.

**Endpoint:** `/create_sharing/`

**Method:** POST

**Authentication Required:** Yes

#### Request Body

- Request body fields depend on the structure of the sharing data.

#### Response

- **Success Response:**

  - **Code:** 201 CREATED
  - **Content:** JSON object representing the created sharing.

- **Error Response:**

  - **Code:** 400 BAD REQUEST
  - **Content:** Serialized errors.

### 62. Get All Sharings

**Description:** This endpoint retrieves all sharings.

**Endpoint:** `/get_all_sharings/`

**Method:** GET

**Authentication Required:** Yes

#### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** JSON array containing serialized sharings.

### 63. Get Sharing by ID

**Description:** This endpoint retrieves a specific sharing by its ID.

**Endpoint:** `/get_sharing_by_id/<sharing_id>/`

**Method:** GET

**Authentication Required:** Yes

#### Parameters

- `sharing_id` (integer): The ID of the sharing.

#### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** JSON object representing the sharing.

- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Sharing not found"
    }
    ```

### 64. Update Sharing

**Description:** This endpoint allows authenticated users to update an existing sharing.

**Endpoint:** `/update_sharing/<sharing_id>/`

**Method:** PUT

**Authentication Required:** Yes

#### Parameters

- `sharing_id` (integer): The ID of the sharing to be updated.

#### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** JSON object representing the updated sharing.

- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Sharing not found"
    }
    ```

### 65. Delete Sharing

**Description:** This endpoint allows authenticated users to delete an existing sharing.

**Endpoint:** `/delete_sharing/<sharing_id>/`

**Method:** DELETE

**Authentication Required:** Yes

#### Parameters

- `sharing_id` (integer): The ID of the sharing to be deleted.

#### Response

- **Success Response:**

  - **Code:** 200 OK
  - **Content:** 
    ```json
    {
        "message": "Sharing deleted successfully"
    }
    ```

- **Error Response:**

  - **Code:** 404 NOT FOUND
  - **Content:** 
    ```json
    {
        "message": "Sharing not found"
    }
    ```
