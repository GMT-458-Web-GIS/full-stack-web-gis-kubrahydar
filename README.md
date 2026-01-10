

````md
# 🌍 Full Stack Web GIS – Final Project

## 📘 Course Information
- **Course:** GMT 458 – Web GIS
- **Assignment:** Final Assignment – Full Stack Web GIS
- **Submission:** webgis-final.zip

---

## 🧩 Project Overview
This project is a **Full Stack Web GIS application** developed using:

- **Backend:** Node.js (Express)
- **Database:** PostgreSQL + PostGIS
- **Authentication:** JWT-based authentication
- **Architecture:** Client–Server (decoupled)

The system provides authenticated access to spatial and non-spatial data through RESTful APIs.

---

## 🌐 Live Deployment

The project is deployed using a **split architecture**.

### 🔹 Backend (AWS EC2)
The backend API is deployed on an **AWS EC2** instance and managed using **PM2**.

- **Health Check:**  
  http://16.170.203.136:4000/health

- **Authentication Endpoints:**  
  - `POST` http://16.170.203.136:4000/api/auth/login  
  - `POST` http://16.170.203.136:4000/api/auth/signup  

> Note: Accessing `http://16.170.203.136:4000/` directly may return  
> `Cannot GET /` — this is expected since the backend only serves API endpoints.

---

### 🔹 Frontend (GitHub Pages)
The frontend is a static web application hosted on **GitHub Pages**.

- **Repository:**  
  https://github.com/GMT-458-Web-GIS/full-stack-web-gis-kubrahydar

- **API Base URL:**  
  `http://16.170.203.136:4000`


## 📁 Project Structure

The project follows a clear **client–server separation**, with all backend logic organized under a modular **Express.js** architecture.

full-stack-web-gis/
│
├── server/                         # Node.js + Express backend
│   ├── src/
│   │   ├── config/                 # Environment variables & DB configuration
│   │   │   └── db.js               # PostgreSQL / PostGIS connection pool
│   │   │
│   │   ├── middleware/             # Global middleware layer
│   │   │   ├── auth.js             # JWT authentication (token verification)
│   │   │   └── role.js             # Role-based access control (RBAC)
│   │   │
│   │   ├── routes/                 # API route definitions
│   │   │   ├── points.js           # Spatial resource (Point layer CRUD)
│   │   │   └── scores.js           # Non-spatial resource CRUD
│   │   │
│   │   ├── controllers/            # Request handling logic
│   │   │   ├── pointsController.js # Create / Read / Update / Delete points
│   │   │   └── scoresController.js # CRUD logic for scores
│   │   │
│   │   ├── utils/                  # Helper utilities
│   │   │   └── geo.js              # Geometry creation (GeoJSON / PostGIS)
│   │   │
│   │   └── index.js                # Application entry point
│   │
│   └── package.json                # Backend dependencies
│
├── sql/                            # Database scripts
│   ├── schema.sql                  # Table definitions (users, points, scores)
│   └── indexes.sql                 # Spatial index (GiST) definitions
│
├── README.md                       # Project documentation
└── webgis-final.zip                # Final submission archive
````

## 🧩 Backend Architecture Overview

The backend is built using **Node.js and Express** and follows a layered architecture:

* 🔀 **Routes** define the API endpoints
* 🧠 **Controllers** implement business logic
* 🛡️ **Middleware** enforces authentication and authorization
* 🗄️ **Database layer** manages spatial and non-spatial data using PostgreSQL/PostGIS

This structure improves **maintainability, scalability, and clarity**.


## 🔐 Authentication

Authentication is implemented using **JWT (JSON Web Token)** and **bcrypt**.

* Passwords are securely stored using bcrypt hashing.
* Users authenticate via a login endpoint.
* A JWT token is issued upon successful authentication.
* Protected endpoints require a valid Bearer token.
* Token verification is handled at the middleware level.


## 👥 Managing Different User Types

The system implements **Role-Based Access Control (RBAC)** with three distinct user roles:

* 🛡️ **Admin**

  * Full access to all resources
  * Can perform all CRUD operations

* 🎮 **Player**

  * Can create, update, and delete their own spatial data
  * Ownership rules are enforced

* 👀 **Viewer**

  * Read-only access
  * Can only access GET endpoints

Ownership is tracked using an `owner_id` field and enforced during update and delete operations.


## 📍 CRUD Operations on Spatial Data

The system supports **full CRUD operations** on a geographical **Point layer**.

### Spatial Layer Details

* Geometry type: `Point`
* Spatial reference system: `SRID 4326`
* Stored using PostGIS geometry types

### Supported Operations

* **GET /points** – Retrieve spatial features
* **POST /points** – Create new points
* **PUT /points/:id** – Update existing points
* **DELETE /points/:id** – Delete points

Filtering mechanisms (e.g. bounding box and ownership-based filtering) are supported.


## 🧮 Non-Spatial Resource (Scores)

In addition to spatial data, the API exposes a **non-spatial resource** (`scores`).

* Full CRUD operations are supported.
* Each score is associated with a user.
* Role-based and ownership-based access rules are enforced.

This resource demonstrates handling of attribute-based data alongside spatial data.


## ⚡ Performance Monitoring (Spatial Indexing)

To evaluate spatial query performance, a **GiST spatial index** is applied to the geometry column.

### Experiment Summary

* Queries were executed with and without a spatial index.
* Execution plans were analyzed using `EXPLAIN ANALYZE`.
* Indexed queries showed significantly reduced execution time compared to sequential scans.

This experiment highlights the importance of spatial indexing in GIS applications.


## 🧪 Performance Testing

Performance testing was conducted to evaluate system behavior under load:

* Load testing simulates concurrent users.
* Response time variation is observed.
* Results confirm backend stability and scalability.

## 📦 Submission Format

The project is submitted as:

**`webgis-final.zip`**

This archive includes:

* Backend source code
* SQL scripts
* Configuration files
* This README document

The project is also maintained in a GitHub repository with the required commit history.


## ✅ Implemented Assignment Components

| Assignment Requirement                               | Weight | Status |
| ---------------------------------------------------- | ------ | ------ |
| Managing source code on GitHub                       | 10%    | ✅      |
| Managing different user types (RBAC)                 | 20%    | ✅      |
| Authentication (JWT + bcrypt)                        | 15%    | ✅      |
| CRUD operations on a geographical point layer        | 15%    | ✅      |
| API development (spatial + non-spatial resources)    | 25%    | ✅      |
| Performance monitoring (spatial indexing experiment) | 25%    | ✅      |
| Performance testing (load & stress testing)          | 25%    | ✅      |


## 🏁 Conclusion

This project successfully implements a **Full Stack Web GIS backend system** that satisfies all selected requirements of the Web GIS Final Assignment.

The system demonstrates secure authentication, role-based authorization, spatial data management, performance optimization, and clean backend architecture.
```
