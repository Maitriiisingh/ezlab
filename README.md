# Secure File Sharing System

A secure file-sharing system between Operations Users and Client Users built with Flask.

## Features

- **User Authentication**:

  - Client User Signup with Email Verification
  - Login for both Client and Operations Users
  - JWT-based Authentication

- **File Operations**:

  - Upload Files (Operations Users only)
  - List Files (Client Users only)
  - Download Files with Secure URLs (Client Users only)

- **Security**:
  - Encrypted Download URLs
  - File Type Validation (only pptx, docx, xlsx allowed)
  - Role-based Access Control

## Setup and Installation

### Prerequisites

- Python 3.8+
- pip

### Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd secure-file-sharing
```

2. Create a virtual environment:

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Create a `.env` file in the root directory with the following variables:

```
SECRET_KEY=your_secret_key
JWT_SECRET_KEY=your_jwt_secret_key
SQLALCHEMY_DATABASE_URI=sqlite:///fileshare.db
MAIL_SERVER=smtp.example.com
MAIL_PORT=587
MAIL_USERNAME=your_email@example.com
MAIL_PASSWORD=your_email_password(16 bit)
MAIL_USE_TLS=True
MAIL_DEFAULT_SENDER=your_email@example.com
BASE_URL=http://localhost:5000
```

### Running the Application

1. Start the Flask application:

```bash
python run.py
```

2. The application will be available at `http://localhost:5000`

## API Endpoints

### Authentication

- `POST /signup` - Register a new client user
- `GET /verify-email/<token>` - Verify email address
- `POST /login` - Login for both client and operations users
- `POST /create-ops-user` - Create an operations user (requires admin key)

### File Operations

- `POST /upload-file` - Upload a file (Operations users only)
- `GET /list-files` - List all uploaded files (Client users only)
- `GET /download-file/<file_id>` - Get a secure download link (Client users only)
- `GET /download-file/<token>` - Download a file using a secure token

## Running Tests

Run the tests using pytest:

```bash
pytest
```

## Deployment

For production deployment:

1. Use a production WSGI server like Gunicorn:

```bash
pip install gunicorn
gunicorn -w 4 "app:create_app()"
```

2. Set up a reverse proxy with Nginx or Apache

3. Use environment variables for configuration instead of `.env` file

4. Consider using a managed database service instead of SQLite

5. Set up proper logging and monitoring

Postman screenshots

<img width="995" alt="Screenshot 2025-07-02 at 2 34 06 PM" src="https://github.com/user-attachments/assets/1c9064d5-6d0d-4a41-9d5f-74f52567d8c7" />
<img width="998" alt="Screenshot 2025-07-02 at 2 08 00 PM" src="https://github.com/user-attachments/assets/e7702e7b-e541-47a3-81c1-74bbec8ddacd" /><img width="1150" alt="Screenshot 2025-07-02 at 2 12 46 PM" src="https://github.com/user-attachments/assets/0dbc4eae-4827-4594-b424-53580432af9f" />
<img width="1002" alt="Screenshot 2025-07-02 at 2 11 03 PM" src="https://github.com/user-attachments/assets/e2c6aae8-ee38-455c-a6e6-89d8de3bb3f7" />
<img width="999" alt="Screenshot 2025-07-02 at 2 09 25 PM" src="https://github.com/user-attachments/assets/9c5d63fa-6027-4298-a373-0b15bc16b64a" />




