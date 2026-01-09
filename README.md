📁 Project Structure
The project follows a clear client–server separation, with all backend logic organized under a modular Express.js architecture.
full-stack-web-gis/
│
├── server/                         # Node.js + Express backend
│   │
│   ├── src/
│   │   │
│   │   ├── config/                 # Environment variables & DB configuration
│   │   │   ├── db.js               # PostgreSQL / PostGIS connection pool
│   │   │
│   │   ├── middleware/             # Global middleware layer
│   │   │   ├── auth.js             # JWT authentication (token verification)
│   │   │   ├── role.js             # Role-based access control (RBAC)
│   │   │
│   │   ├── routes/                 # API route definitions
│   │   │   ├── points.js           # Spatial resource (Point layer CRUD)
│   │   │   ├── scores.js           # Non-spatial resource CRUD
│   │   │
│   │   ├── controllers/            # Request handling logic
│   │   │   ├── pointsController.js # Create / Read / Update / Delete points
│   │   │   ├── scoresController.js # CRUD logic for scores
│   │   │
│   │   ├── utils/                  # Helper utilities
│   │   │   ├── geo.js              # Geometry creation (GeoJSON / PostGIS)
│   │   │
│   │   └── index.js                # Application entry point
│   │
│   └── package.json                # Backend dependencies
│
├── sql/                            # Database scripts
│   ├── schema.sql                  # Table definitions (users, points, scores)
│   ├── indexes.sql                 # Spatial index (GiST) definitions
│
├── README.md                       # Project documentation
└── webgis-final.zip                # Final submission archive
________________________________________
🧩 Backend Architecture Overview
The backend is built using Node.js and Express and follows a layered architecture:
•	Routes define the API endpoints.
•	Controllers implement business logic.
•	Middleware enforces authentication and authorization.
•	Database layer manages spatial and non-spatial data using PostgreSQL/PostGIS.
This structure improves maintainability, scalability, and clarity.
________________________________________
🔐 Authentication & Authorization Implementation
Where it is implemented
•	JWT verification:
server/src/middleware/auth.js
•	Role-based access control:
server/src/middleware/role.js
How it works
•	Users authenticate via /demo-login.
•	Passwords are securely stored using bcrypt hashing.
•	On successful login, a JWT token is generated.
•	The token is required for all protected endpoints.
•	User roles (admin, player, viewer) are validated via middleware before route execution.

👥 Managing Different User Types
User roles and access rules are enforced at the backend level.
Where roles are enforced
•	Middleware layer (role.js)
•	Route-level protection (routes/points.js, routes/scores.js)
Role behavior
•	Admin: Full system access
•	Player: Can create and manage own spatial data
•	Viewer: Read-only access
Ownership is tracked using an owner_id field stored with each resource.

📍 Spatial Data Management (CRUD Operations)
Where spatial logic is handled
•	Routes: server/src/routes/points.js
•	Controller: server/src/controllers/pointsController.js
•	Geometry utilities: server/src/utils/geo.js
How it is implemented
•	Spatial data is stored as PostGIS geometry (Point, SRID 4326).
•	CRUD operations are exposed via RESTful endpoints.
•	Filtering is supported using query parameters (e.g. bounding box, ownership).

🧮 Non-Spatial Resource (Scores)
The project also includes a non-spatial resource to meet API development requirements.
Where it is implemented
•	Routes: server/src/routes/scores.js
•	Controller: server/src/controllers/scoresController.js
Purpose
•	Demonstrates handling of attribute-based data.
•	Enforces ownership and role-based restrictions.
•	Complements the spatial API with non-spatial logic.

⚡ Performance Monitoring & Spatial Indexing
Where performance optimization is defined
•	SQL scripts: sql/indexes.sql
How performance was evaluated
•	Spatial queries were executed with and without a GiST spatial index.
•	Execution plans were analyzed using EXPLAIN ANALYZE.
•	Indexed queries showed significantly improved performance compared to sequential scans.

🧪 API Testing
All API endpoints were tested using Postman:
•	Authentication flow
•	JWT-protected requests
•	Role-based access control
•	Full CRUD operations for both resources
This validates the correctness and robustness of the backend API.

📦 Submission Format
The project is submitted as:
webgis-final.zip
The archive contains:
•	Full backend source code
•	SQL scripts
•	Configuration files
•	This README document
Additionally, the project is managed via GitHub with the required commit history.

✅ Summary
This project implements a complete Full Stack Web GIS backend with:
•	Secure authentication
•	Role-based authorization
•	Spatial CRUD operations
•	Performance optimization using spatial indexing
•	Clean and modular backend architecture
All requirements listed in the Web GIS Final Assignment are addressed and documented.

✅ Implemented Assignment Components
The following table lists only the components implemented in this project, directly aligned with the Web GIS Final Assignment requirements.
Assignment Requirement	Weight	Status
Managing source code on GitHub	10%	✅
Managing different user types (RBAC)	20%	✅
Authentication (JWT + bcrypt)	15%	✅
CRUD operations on a geographical point layer	15%	✅
API development (spatial + non-spatial resources)	25%	✅
Performance monitoring (spatial indexing experiment)	25%	✅
Performance testing (load & stress testing)	25%	✅

✔ Summary
All listed components above are fully implemented and documented in this project in accordance with the Web GIS Final Assignment description.
