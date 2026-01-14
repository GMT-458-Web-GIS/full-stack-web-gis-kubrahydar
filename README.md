
````md
# 🌍 Full Stack Web GIS – Final Project

## 📘 Course Information
- **Course:** GMT 458 – Web GIS
- **Assignment:** Final Assignment – Full Stack Web GIS
- **Student:** Hatice Kübra Hydar


---

## 🧩 Project Overview

This project is a **Full Stack Web GIS application** developed as part of the GMT 458 – Web GIS course.

The application combines **spatial data processing**, **user authentication**, and **game-based interaction** in a real-world client–server architecture.

### Technologies Used
- **Backend:** Node.js (Express)
- **Frontend:** HTML, CSS, Vanilla JavaScript
- **Database:** PostgreSQL + PostGIS
- **Authentication:** JWT (JSON Web Token) + bcrypt
- **Deployment:** AWS EC2 (Ubuntu)
- **Process Management:** PM2

---

## 🌐 Live Deployment

🔗 **Live Application URL:**  
http://16.170.203.136:4000

The project is deployed as a **fully integrated full-stack application** on **AWS EC2**.

Both the **frontend and backend are hosted on the same EC2 instance** and served from a single origin.

---

## ☁️ Deployment Architecture (AWS EC2)

### 🔹 Backend & Frontend (Single Server Deployment)

- The backend is built with **Express.js**
- The frontend is a **static web application**
- Frontend files (`index.html`, `script.js`, `styles.css`) are served via:
  ```js
  app.use(express.static("public"))
````

* The root route (`/`) delivers the frontend entry point

This deployment approach:

* Eliminates CORS issues
* Simplifies configuration
* Reflects a production-style setup

The backend process is managed using **PM2** to ensure reliability and uptime.

---

## 🔐 Authentication & Authorization

Authentication is implemented using **JWT** and **bcrypt**:

* Passwords are securely hashed with bcrypt
* Users authenticate via login/signup endpoints
* A JWT token is issued upon successful login
* Protected endpoints require a valid Bearer token
* Token verification is handled via middleware

---

## 👥 Role-Based Access Control (RBAC)

The system implements **Role-Based Access Control** with three user roles:

### 🛡️ Admin

* Full access to all resources
* Can perform all CRUD operations

### 🎮 Player

* Can create, update, and delete their own spatial data
* Ownership rules are enforced

### 👀 Viewer

* Read-only access
* Can only access GET endpoints

Ownership is tracked using an `owner_id` field and enforced during update and delete operations.

---

## 📍 Spatial Data Management (PostGIS)

The application supports full **CRUD operations** on a spatial **Point layer**.

### Spatial Layer Details

* Geometry type: **Point**
* SRID: **4326**
* Stored using PostGIS geometry types

### Supported Endpoints

* `GET /points` – Retrieve spatial features
* `POST /points` – Create new points
* `PUT /points/:id` – Update existing points
* `DELETE /points/:id` – Delete points

Advanced filtering is supported:

* Bounding box queries
* Ownership-based filtering

---

## 🧮 Non-Spatial Resource – Scores

In addition to spatial data, the API exposes a **non-spatial resource** (`scores`):

* Full CRUD operations
* Each score is associated with a user
* Role-based and ownership-based access control enforced

This demonstrates handling **attribute-based data** alongside spatial data.

---

## ⚡ Performance Monitoring (Spatial Indexing)

A **GiST spatial index** is applied to the geometry column to improve query performance.

### Experiment Summary

* Queries executed with and without spatial indexing
* Execution plans analyzed using `EXPLAIN ANALYZE`
* Indexed queries show significantly reduced execution time

This experiment highlights the importance of spatial indexing in GIS applications.

---

## 🧪 Performance Testing

Performance testing was conducted to evaluate system behavior under load:

* Concurrent user simulation
* Response time monitoring
* Stability and scalability evaluation

Results indicate that the backend remains stable under increased load.

---

## 📁 Project Structure

```
full-stack-web-gis/
│
├── backend/                      # Node.js + Express backend
│   ├── src/
│   │   ├── middleware/           # Auth & RBAC middleware
│   │   ├── routes/               # API routes
│   │   ├── db.js                 # PostgreSQL/PostGIS connection
│   │   └── index.js              # Application entry point
│   │
│   ├── public/                   # Frontend (served by Express)
│   │   ├── index.html
│   │   ├── script.js
│   │   └── styles.css
│   │
│   └── package.json
│
├── sql/                          # Database scripts
│   ├── schema.sql
│   └── indexes.sql
│
├── README.md
└── webgis-final.zip
```

---
---

## ✅ Implemented Assignment Components

| Requirement                               | Weight | Status |
| ----------------------------------------- | ------ | ------ |
| Managing source code on GitHub            | 10%    | ✅      |
| Managing different user types (RBAC)      | 20%    | ✅      |
| Authentication (JWT + bcrypt)             | 15%    | ✅      |
| CRUD operations on spatial data           | 15%    | ✅      |
| API development (spatial + non-spatial)   | 25%    | ✅      |
| Performance monitoring (spatial indexing) | 25%    | ✅      |
| Performance testing                       | 25%    | ✅      |

---

## 🏁 Conclusion

This project successfully delivers a **fully functional Full Stack Web GIS application** deployed on **AWS EC2**.

It demonstrates:

* Secure authentication
* Role-based authorization
* Spatial data management with PostGIS
* Performance optimization
* Real-world deployment practices

The system satisfies all selected requirements of the **Web GIS Final Assignment**.

```

---
