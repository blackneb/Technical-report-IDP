# IDPHCS

IDPHCS This project leverages Django Rest Framework for robust API management and Django WebSocket for real-time Chat communication.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

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

## Usage

### Running the API

Start the Django development server as shown above. The API will be available at `http://127.0.0.1:8000/`.

### WebSocket Communication

To use WebSocket features, ensure your frontend client is configured to connect to the WebSocket endpoint provided by the server. For example:

```javascript
const socket = new WebSocket('ws://127.0.0.1:8000/ws/some_endpoint/');
socket.onmessage = function(event) {
    console.log('Message from server ', event.data);
};

## API Endpoints

Here is a list of available GET API endpoints:

| Method | Endpoint                            | Description                         |
|--------|-------------------------------------|-------------------------------------|
| GET    | /auth/profile/                       | Retrieve user profile               |
| GET    | /auth/users/                         | Retrieve a list of users            |
| GET    | /auth/users/search/                  | Search for a user                   |
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
