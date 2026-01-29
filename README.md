# go-rest-api

A **simple REST API written in Go (Gin framework)** for managing events, users, and registrations.
This project demonstrates basic CRUD operations, database connectivity, and structured routes.

---

## 📌 Features

- RESTful API with standard HTTP verbs (GET, POST, PUT, DELETE)
- Gin framework for routing and request handling
- SQLite (or other DB) for persistent storage
- Models for users, events, and registrations
- Basic input validation & error handling
- Clean and minimal folder structure

---

## 📦 Getting Started

### 🛠 Prerequisites

You’ll need:

- Go (1.20+ recommended)
- Git
- (Optionally) a REST client like VS Code Rest Client, Postman, curl

---

### ⬇️ Clone the Repo

```bash
git clone https://github.com/michael-emmanuel/go-rest-api.git
cd go-rest-api
```

---

### 📁 Project Structure

```
.
├── api-test
├── db
├── middlewares
├── models
├── routes
├── utils
├── main.go
├── go.mod
├── go.sum
└── api.db  (local SQLite database)
```

- `models/`: Database models and related logic
- `routes/`: API route handlers
- `db/`: Database connection and setup
- `utils/`: Helpers (e.g., password hashing)
- `main.go`: Entry point that starts the server

---

## ⚙️ Configuration

By default, the project uses a SQLite database file called `api.db`.
If you want to switch to another database later, update the DB connection logic in `db/db.go`.

---

## 🚀 Run the API

From the root directory:

```bash
go run main.go
```

The server will start on:

```
http://localhost:8080
```

---

## 🧪 API Endpoints

### 🗓 **Events**

| Method | Endpoint      | Description        |
| ------ | ------------- | ------------------ |
| GET    | `/events`     | List all events    |
| GET    | `/events/:id` | Get a single event |
| POST   | `/events`     | Create a new event |
| PUT    | `/events/:id` | Update an event    |
| DELETE | `/events/:id` | Delete an event    |

---

### 👤 **Users** (depends on your models)

| Method | Endpoint       | Description       |
| ------ | -------------- | ----------------- |
| POST   | `/users/login` | Authenticate user |
| POST   | `/users`       | Create new user   |

---

### 📅 **Registrations**

| Method | Endpoint             | Description                 |
| ------ | -------------------- | --------------------------- |
| POST   | `/registrations`     | Register a user to an event |
| GET    | `/registrations`     | List registrations          |
| GET    | `/registrations/:id` | Get a specific registration |

---

## 🛠 Example REST Client Requests

### Create Event

```
POST http://localhost:8080/events
Content-Type: application/json

{
  "name": "Test Event",
  "description": "This is a test event",
  "location": "Somewhere",
  "dateTime": "2025-01-01T15:30:00Z"
}
```

---

### Update Event

```
PUT http://localhost:8080/events/1
Content-Type: application/json

{
  "name": "Updated test event",
  "description": "Updated test event",
  "location": "Test location (updated)",
  "dateTime": "2025-01-01T15:30:00Z"
}
```

---

### User Login

```
POST http://localhost:8080/users/login
Content-Type: application/json

{
  "email": "test@example.com",
  "password": "password123"
}
```

---

## 📌 Notes

- This repo uses **Gin** as the HTTP server and router.
- It does include JWT or session auth by default.
- Database errors at startup intentionally `panic` because the app cannot run without its schema.

---

## 📈 Next Improvements (Optional)

- Add migrations (instead of raw table creation)
- Add tests & CI
- Add OpenAPI/Swagger documentation

---

## 📜 License

This project is provided as-is under MIT License.
