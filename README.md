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

### **Entity Relationships Overview**
- **User → Property**: One-to-Many (host can have multiple properties).  
- **User → Booking**: One-to-Many (guest can have multiple bookings).  
- **Property → Booking**: One-to-Many (property can have multiple bookings).  
- **Property → Review**: One-to-Many (property can have multiple reviews).  
- **Booking → Payment**: One-to-Many (a booking can have multiple payments).  
- **User → Review**: One-to-Many (guest can leave multiple reviews).

## Feature Breakdown

### 1. User Management

Users can register, log in, and manage their profiles. This feature ensures that both guests and hosts have secure, personalized accounts, enabling smooth authentication and authorization across the platform.

### 2. Property Management

Develop features for Hosts to list their properties with details such as title, description, location, price per night, and availability. This feature provides the core functionality for making properties discoverable to potential guests.

### 3. Booking System

Create a booking mechanism for users to search for available properties and make bookings for specific dates. This feature manages reservation conflicts, tracks booking statuses, and ensures guests and hosts have reliable scheduling.

### 4. Reviews & Ratings

Guests can leave reviews and ratings for properties they’ve stayed at. This feature builds trust within the platform by helping future guests make informed decisions based on previous experiences.

### 5. Payment Processing

Guests can securely pay for their bookings through the platform. This feature integrates payment workflows, ensuring transactions are tracked and linked to bookings, providing transparency and reliability.

### 6. Data Optimisation
The feature ensures that there is an efficient data retrieval and storage through database optimisation.

## API Security

Ensuring strong security practices is critical for the Airbnb Clone project since the backend APIs handle sensitive information such as user credentials, booking details, and payment transactions. The following key security measures will be implemented:

### 1. Authentication

We will use secure authentication mechanisms (e.g., JWT or OAuth2) to verify the identity of users before granting access to the system. This ensures that only legitimate users can access protected resources.

**Why it matters:** Prevents unauthorized access to user accounts, protecting personal data and maintaining trust.

### 2. Authorization

Role-based access control will be applied to distinguish between guests, hosts, and administrators. Each role will have specific permissions to ensure that users can only perform actions allowed to them.

**Why it matters:** Prevents users from performing restricted operations, such as one guest modifying another guest’s bookings.

### 3. Rate Limiting

API rate limiting will be implemented to control the number of requests a client can make in a given timeframe. This measure helps protect against brute-force attacks and abuse of the system.

**Why it matters:** Ensures stability of the application, prevents denial-of-service attacks, and protects backend resources.

### 4. Data Encryption

Sensitive information, such as passwords and payment details, will be encrypted both in transit (via HTTPS) and at rest (using strong encryption algorithms).

**Why it matters:** Protects confidential user data and prevents interception or exposure of sensitive information.

### 5. Input Validation & Sanitization

All API inputs will be validated and sanitized to prevent common attacks such as SQL injection, cross-site scripting (XSS), and request forgery.

**Why it matters:** Prevents malicious users from exploiting the system through poorly validated inputs, ensuring the integrity of the application.

## CI/CD Pipeline

Continuous Integration (CI) and Continuous Deployment (CD) pipelines will be used such that (for CI) every change to the codebase is automatically tested and validated, reducing the chances of bugs being introduced. CD automates the deployment process, ensuring that updates are delivered to production environments reliably and efficiently.

For this project, the CI/CD pipeline will help us:
- Automate testing to maintain code quality and stability.
- Deploy new features faster without compromising reliability.
- Ensure a consistent development workflow across the team.

**Tools we may use:**
- **GitHub Actions**: For automating builds, testing, and deployments directly from GitHub.
- **Ansible**: for managing configurations, deployments, and orchestration, using playbooks. 
- **Docker**: To ensure a consistent environment across development, testing, and production.
- **AWS or Heroku**: For hosting and deploying the application.


