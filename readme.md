# Day 70 - Task Manager Backend (v1.0.0)

A RESTful API built with Node.js, Express, and MongoDB (Mongoose) to manage tasks. This update transitions the application from using an in-memory array to a persistent MongoDB Atlas cloud database.

---

## 🚀 Features
* **Full CRUD Operations**: Create, Read, Update, and Delete tasks.
* **Database Persistence**: Connected to MongoDB Atlas via Mongoose.
* **Data Validation**: Schema-enforced validation with status enums (`not-started`, `in-progress`, `completed`).
* **Environment Security**: Sensitive keys and ports hidden using `dotenv`.

---

## 📁 Project Structure
```text
├── config/
│   └── dbconnection.config.js  # Database connection setup
├── controllers/
│   └── tasks.controller.js     # Request handlers (CRUD logic)
├── models/
│   └── tasks.model.js          # Mongoose schema and model definition
├── routes/
│   └── task.route.js           # API route mapping
├── .env                        # Environment variables (Ignored by Git)
├── .gitignore                  # Git ignore file
├── main.js                     # Application entry point
├── package.json                # Project metadata and dependencies
└── README.md                   # Project documentation
```

---

## 🛠️ Tech Stack & Dependencies
* **Runtime Environment**: Node.js
* **Framework**: Express.js (v5.2.1)
* **ODM (Database)**: Mongoose (v9.7.2)
* **Environment Management**: Dotenv (v17.4.2)
* **Development Tool**: Nodemon (v3.1.14)

---

## ⚙️ Prerequisites & Setup

### 1. Environment Configuration
Create a `.env` file in the root directory and configure your ports and MongoDB URI strings:

```env
port = your id
dbport = mongodb://localhost:your nbr/my-db
atlasport = mongodb+srv://<username>:<password>@cluster.mongodb.net/your-db-name?appName=b43-db
```

### 2. Installation
Install the project dependencies using npm:
```bash
npm install
```

### 3. Run the Server
Start the development server with hot-reloading enabled:
```bash
npm run dev
```

---

## 🛣️ API Endpoints

All routes are prefixed with `/tasks`.

| Method | Endpoint | Description | Request Body (JSON) |
| :--- | :--- | :--- | :--- |
| **GET** | `/tasks` | Fetch all tasks | *None* |
| **POST** | `/tasks` | Create a new task | `{ "title": "String", "description": "String", "status": "not-started" \| "in-progress" \| "completed" }` |
| **PUT** | `/tasks/:id` | Update an existing task by ID | `{ "title": "Updated Title", "status": "completed" }` |
| **DELETE** | `/tasks/:id` | Delete a task by ID | *None* |

### Sample JSON Request Body for POST:
```json
{
  "title": "Complete Day 70 Update1",
  "description": "Connect backend server to MongoDB Atlas and verify CRUD routes.",
  "status": "in-progress"
}
```

---

## ⚠️ Notes for Update 1
* **Database Migration**: The older array-based local data storage setup in `tasks.model.js` has been commented out and completely replaced with Mongoose schemas.
* **Error Handling**: Database operations are wrapped inside `try-catch` blocks returning generic `500` server messages to the client to ensure server stability.
