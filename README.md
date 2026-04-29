# Airdrobe

Airdrobe is a modern, scalable web application built with **Django** that revolutionizes how communities and friend groups manage and share their clothing. Acting as a digital "cloud wardrobe," it allows users to catalog their clothing items, organize them into collections, and lend/borrow items seamlessly with built-in role-based access control.

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-5.1.6-092E20.svg)](https://www.djangoproject.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-336791.svg)](https://www.postgresql.org/)
[![AWS S3](https://img.shields.io/badge/AWS_S3-Storage-FF9900.svg)](https://aws.amazon.com/s3/)

---

## Key Features

- **Secure Authentication (OAuth)**: Integrated Google OAuth using `django-allauth` for seamless and secure user onboarding and login.
- **Role-Based Access Control (RBAC)**: Two distinct user roles:
  - **Librarians (Admins)**: Manage catalog items, approve lending requests, and oversee platform activity.
  - **Patrons (Users)**: Browse collections, request to borrow items, and manage their custom profiles.
- **Collection Management**: Group items into public or private collections. Private collections support an invite-only system where patrons can request access.
- **Lending & Borrowing Workflow**: Fully functional lending system with statuses (`PENDING`, `APPROVED`, `REJECTED`, `RETURNED`) allowing tracking of requested and borrowed items.
- **☁️ Cloud Storage Integration**: Direct integration with **AWS S3** using `boto3` for high-performance storage and serving of user profile pictures and clothing item images.
- **Rating & Review System**: Users can leave ratings and text reviews for items they've borrowed, providing community feedback.

## Technology Stack

- **Backend**: Python, Django 5.1
- **Database**: PostgreSQL (via `psycopg3` & `psycopg2-binary`)
- **Cloud Storage**: AWS S3 (via `django-storages`, `boto3`)
- **Authentication**: `django-allauth` (Google OAuth)
- **Deployment & Hosting**: Heroku ready (`django-heroku`, `gunicorn`, `whitenoise`)
- **Frontend**: HTML5, CSS3, JavaScript (Django Templates)

## Core Data Models

- **Users**: Custom User model extended into `Librarian` and `Patron` profiles.
- **Items & Categories**: Clothing items with details like size, condition, category, and S3 image links.
- **Collections**: Logical groupings of items, supporting privacy toggles and allowlists.
- **Lendings & Invites**: Transactional models tracking the state of borrow requests and private collection access requests.
- **Ratings**: 1-5 star rating system with user comments.

---

## Getting Started

To run this project locally, follow these steps:

### Prerequisites
- Python 3.10+
- PostgreSQL
- AWS Account (for S3 bucket)
- Google Cloud Console (for OAuth credentials)

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/Airdrobe.git
cd Airdrobe
```

### 2. Set up a virtual environment
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows use: .venv\Scripts\activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Environment Variables
Create a `.env` file in the root directory and configure the following variables:
```env
SECRET_KEY=your_django_secret_key
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1

# Database Configuration
DB_NAME=airdrobe_db
DB_USER=postgres
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=5432

# AWS S3 Configuration
AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key
AWS_STORAGE_BUCKET_NAME=your_bucket_name
AWS_S3_REGION_NAME=your_region
```

### 5. Database Setup
```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Run the Development Server
```bash
python manage.py runserver
```
Visit `http://localhost:8000` in your browser.

---

## Future Enhancements

- **Real-time Notifications**: Notify users when their borrow requests are approved or when items are due.
- **Advanced Search & Filtering**: Allow users to filter items by size, condition, and availability.
- **Payment Integration**: Add payment processing for late fees or premium collections.

---
