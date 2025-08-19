# Airbnb Clone Project

## Project Overview
The **Airbnb Clone Backend** is a real-world simulation of a booking platform similar to Airbnb.  
This project focuses on building a robust, scalable, and secure backend using Django and Django REST Framework (DRF), providing hands-on experience in API development, database design, authentication, and deployment workflows.

## Project Goals
- Build a backend API that handles user authentication, property listings, bookings, payments, and reviews.
- Implement a secure and efficient JWT authentication system.
- Design a relational database schema that supports bookings, availability checks, and user roles (guest/host).
- Prepare the project for deployment using Docker and integrate a basic CI/CD pipeline.
- Develop professional skills in documentation, testing, and collaborative workflows using Git and GitHub.

## Tech Stack
- **Backend Framework:** Django + Django REST Framework (DRF)  
- **Database:** PostgreSQL / MySQL  
- **Authentication:** JWT (via `djangorestframework-simplejwt`)  
- **Deployment:** Docker, Gunicorn, Nginx  
- **CI/CD:** GitHub Actions  
- **Optional:** GraphQL for advanced API queries

## Team Roles
- **Backend Developer:** responsible for implementing the API endpoints, database schemas, and business logic
- **Database Administrator:** manages the database design, indexing & optimisation
- **DevOps Engineer:** handles the deployment, monitoring, and scaling of digital services
- **QA Engineer:** ensures the backend functionalities are thoroughyly tested and meets the quality standards

## Technology Stack
- **Django:** A high-level Python web framework used for building the RESTful API.
- **Django REST Framework:** Provides tools for creating and managing RESTful APIs.
- **PostgreSQL:** A powerful relational database used for data storage.
- **GraphQL:** Allows for flexible and efficient querying of data.
- **Celery:** For handling asynchronous tasks such as sending notifications or processing payments.
- **Redis:** Used for caching and session management.
- **Docker:** Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines:** Automated pipelines for testing and deploying code changes.

## Database Design
The Airbnb Clone backend relies on a relational database to manage users, properties, bookings, reviews, and payments. Below are the key entities and their relationships:

### 1. Users
**Fields:**
- `id` (Primary Key)
- `username`
- `email`
- `is_host` (boolean)

**Relationships:**
- A user can be a host with multiple properties.
- A user can be a guest making multiple bookings.
- A user can leave multiple reviews.

---

### 2. Properties
**Fields:**
- `id` (Primary Key)
- `title`
- `description`
- `location` (city, country)
- `price_per_night`
- `host_id` (Foreign Key → Users)

**Relationships:**
- Each property belongs to one host.
- A property can have multiple bookings.
- A property can have multiple reviews.

---

### 3. Bookings
**Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key → Users)
- `property_id` (Foreign Key → Properties)
- `start_date`
- `end_date`
- `status` (confirmed, cancelled, pending)

**Relationships:**
- Each booking belongs to one guest.
- Each booking is for one property.

---

### 4. Reviews
**Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key → Users)
- `property_id` (Foreign Key → Properties)
- `rating` (1–5)
- `comment`
- `created_at`

**Relationships:**
- Each review is written by one guest.
- Each review belongs to one property.

---

### 5. Payments
**Fields:**
- `id` (Primary Key)
- `booking_id` (Foreign Key → Bookings)
- `amount`
- `payment_date`
- `status` (completed, failed, pending)

**Relationships:**
- Each payment is linked to one booking.
- A booking can have one or multiple payment attempts.

---

### **Entity Relationships Overview**
- **User → Property**: One-to-Many (host can have multiple properties).  
- **User → Booking**: One-to-Many (guest can have multiple bookings).  
- **Property → Booking**: One-to-Many (property can have multiple bookings).  
- **Property → Review**: One-to-Many (property can have multiple reviews).  
- **Booking → Payment**: One-to-Many (a booking can have multiple payments).  
- **User → Review**: One-to-Many (guest can leave multiple reviews).

