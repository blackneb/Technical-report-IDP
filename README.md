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

Here is a list of available API endpoints:

| Method | Endpoint                  | Description                       |
|--------|---------------------------|-----------------------------------|
| GET    | /api/users/               | Retrieve a list of users          |
| POST   | /api/users/               | Create a new user                 |
| GET    | /api/users/{id}/          | Retrieve a specific user by ID    |
| PUT    | /api/users/{id}/          | Update a specific user by ID      |
| DELETE | /api/users/{id}/          | Delete a specific user by ID      |
| GET    | /api/health_records/      | Retrieve a list of health records |
| POST   | /api/health_records/      | Create a new health record        |
| GET    | /api/health_records/{id}/ | Retrieve a specific health record |
| PUT    | /api/health_records/{id}/ | Update a specific health record   |
| DELETE | /api/health_records/{id}/ | Delete a specific health record   |
