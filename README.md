# Pensionat Booking Frontend

User interface for the Pensionat Booking System, built with Next.js and React.

The application allows customers to browse available rooms, create and manage bookings, register, log in and manage their account. It communicates directly with the Booking Service and Customer Service through REST API requests.

---

## Related Repositories

**Booking Backend:** [pensionat-booking-backend](https://github.com/igor-gomes-academic/pensionat-booking-backend)

**Customer Service:** [pensionat-customer-service](https://github.com/igor-gomes-academic/pensionat-customer-service)

---

## Architecture Overview

```text
User
  │
  ▼
Frontend
  ├── Booking and room requests ──► Booking Service
  │
  └── Registration, login and account requests ──► Customer Service
```

The Frontend provides the user interface and does not access either service database directly.

- The Frontend handles pages, forms and user interactions
- The Booking Service manages rooms and bookings
- The Customer Service manages customer accounts

---

## Technologies

- Next.js 16
- React 19
- JavaScript
- CSS
- Fetch API
- REST APIs
- Node.js 22
- Docker
- Docker Compose

---

## Project Structure

The Frontend is organized into pages and reusable components:

- **Home page:** Displays rooms and provides availability searches
- **Bookings page:** Creates bookings for selected customers and rooms
- **Account page:** Displays and manages customer information and bookings
- **Login page:** Authenticates customers through the Customer Service
- **Registration page:** Creates customer accounts through the Customer Service
- **Components:** Provide reusable navigation, room, banner and footer elements
- **Styling:** Defines the layout and visual presentation
- **API communication:** Sends requests to the Booking Service and Customer Service

---

## Functionality

The Frontend supports:

1. Viewing rooms and their information
2. Searching for available rooms by date interval
3. Registering customer accounts
4. Logging in and logging out
5. Creating bookings
6. Viewing bookings associated with the logged-in customer
7. Updating bookings
8. Cancelling bookings
9. Viewing customer account information
10. Updating customer account information
11. Deleting customer accounts
12. Displaying confirmation and error messages returned by the services

---

## Application Responsibilities

- The Frontend collects user input and sends REST API requests
- The logged-in customer information is used to associate actions with the correct customer ID
- Available rooms are displayed according to the selected booking dates
- Extra bed selection is displayed only for double rooms
- Account and booking actions are presented through the customer account page
- Business rules and database operations are validated by the backend services

---

## API Communication

The Frontend sends room and booking requests to the Booking Service on port `8080`.

The Booking Service API is used for:

- Retrieving rooms
- Searching room availability
- Creating and updating bookings
- Cancelling bookings
- Retrieving bookings associated with the logged-in customer

The Frontend sends customer and authentication requests to the Customer Service on port `8081`.

The Customer Service API is used for:

- Registering customers
- Logging in
- Updating customer information
- Deleting customer accounts

The two backend services communicate with each other when a booking is created or a customer account deletion is requested.

---

## Production Build

The Frontend uses a multi-stage Dockerfile that separates dependency installation, application build and runtime execution.

Next.js standalone output is enabled so the production image contains only the files and dependencies required at runtime. Build tools, source files and development dependencies are not included in the final image.

The container runs as a non-root user and exposes the application on port `3000`.

The `.dockerignore` file excludes local, development and generated files from the Docker build context.

---

## Running the Complete System with Docker Compose

The shared Docker Compose environment and setup instructions are maintained in the Customer Service repository:

[pensionat-customer-service: Running the Complete System with Docker Compose](https://github.com/igor-gomes-academic/pensionat-customer-service#running-the-complete-system-with-docker-compose)

Follow those instructions to configure and start the Frontend, Booking Service, Customer Service and both MySQL databases.

---

## Team

- Patric Westman
- Daniel Lyytikäinen
- Niklas Dahlström
- Igor Gomes
