<div align="center">

<img src="https://kunievents.netlify.app/logo.png" alt="Karnavati University Logo" width="100"/>

# 🎓 KU Events — Karnavati University Events Management System

**A full-stack web application to discover, register, and manage university events.**

[![Node.js](https://img.shields.io/badge/Node.js-v18+-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express.js](https://img.shields.io/badge/Express.js-5.x-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.x-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License](https://img.shields.io/badge/License-Educational-blue?style=for-the-badge)](#license)

<br/>

> *"Where Creativity Meets Innovation"* — Explore the vibrant life at Karnavati University through curated events, festivals, and academic symposiums.

<br/>

[🚀 Features](#-features) · [🛠️ Tech Stack](#️-tech-stack) · [⚙️ Installation](#️-local-setup--installation) · [📡 API Docs](#-api-endpoints) · [📁 Project Structure](#-project-structure) · [🔮 Future Plans](#-future-improvements)

</div>

---

## 📸 Preview

| Section | Description |
|---|---|
| 🏠 **Hero** | Animated landing section with live stats (50+ events, 10,000+ students, 5 colleges) |
| 🎉 **Events** | Browse, filter, and search all university events |
| 🗓️ **Calendar** | Calendar view of upcoming events |
| ✨ **Highlights** | Past event highlights section |
| 👤 **Profile** | User profile with session management |
| 📬 **Newsletter** | Subscribe for event updates |
| 📞 **Contact** | University contact section |

---

## ✨ Features

### 👤 Authentication
- **User Registration** — Create a new account with email and password
- **User Login** — Secure login with credential verification
- **Session Management** — User session stored via `localStorage`
- **Logout** — Clear session and return to guest mode

### 🎉 Events
- **Browse Events** — View all events fetched live from the database
- **Filter & Search** — Find events by category or keyword
- **Event Registration** — Register for any event as a logged-in user

### 👥 User Profile
- View logged-in user details in a modal
- Logout directly from the profile panel

### 📬 Newsletter
- Subscribe with your email to get notified about upcoming events

### 🎨 UI/UX Highlights
- Responsive design — works on desktop, tablet, and mobile
- Hamburger menu for mobile navigation
- Smooth animations and scroll effects
- Animated hero statistics counter
- Google Fonts (`Playfair Display` + `DM Sans`) and Font Awesome icons

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | HTML5, CSS3, Vanilla JavaScript |
| **Backend** | Node.js, Express.js v5 |
| **Database** | MySQL 8 (via `mysql2` driver) |
| **Fonts & Icons** | Google Fonts, Font Awesome 6 |
| **Middleware** | `cors`, `body-parser` |

---

## 📁 Project Structure

```
kuevents/
│
├── backend/
│   ├── server.js          # Express server entry point (port 5000)
│   ├── db.js              # MySQL connection setup
│   └── routes/
│       ├── auth.js        # /api/auth → register & login
│       ├── events.js      # /api/events → fetch all events
│       ├── register.js    # /api/register → event registration
│       └── newsletter.js  # /api/newsletter → email subscription
│
├── frontend/
│   ├── index.html         # Main single-page application
│   ├── style.css          # All styles and responsive design
│   └── script.js          # Frontend logic, API calls, DOM manipulation
│
├── package.json           # Project metadata and dependencies
├── .gitignore
└── README.md
```

---

## ⚙️ Local Setup & Installation

Follow these steps to run the project on your local machine.

### ✅ Prerequisites

Make sure the following are installed on your system:

- [Node.js](https://nodejs.org/) (v18 or higher)
- [npm](https://www.npmjs.com/) (comes with Node.js)
- [MySQL](https://www.mysql.com/) (v8 or higher)
- A code editor like [VS Code](https://code.visualstudio.com/)
- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension for VS Code (for frontend)

---

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-username/kuevents.git
cd kuevents
```

---

### 2️⃣ Install Backend Dependencies

```bash
npm install
```

This will install all required packages: `express`, `mysql2`, `cors`, and `body-parser`.

---

### 3️⃣ Set Up MySQL Database

Open your MySQL client (MySQL Workbench, TablePlus, or terminal) and run the following:

```sql
-- Step 1: Create the database
CREATE DATABASE ku_events;
USE ku_events;

-- Step 2: Create the users table
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  email VARCHAR(255) NOT NULL UNIQUE,
  password VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Step 3: Create the events table
CREATE TABLE events (
  id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  description TEXT,
  date DATE,
  location VARCHAR(255),
  category VARCHAR(100),
  image_url VARCHAR(500),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Step 4: Create the registrations table
CREATE TABLE registrations (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT NOT NULL,
  event_id INT NOT NULL,
  registered_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES users(id),
  FOREIGN KEY (event_id) REFERENCES events(id)
);

-- Step 5: Create the newsletter table
CREATE TABLE newsletter (
  id INT AUTO_INCREMENT PRIMARY KEY,
  email VARCHAR(255) NOT NULL UNIQUE,
  subscribed_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Step 6: (Optional) Insert sample events
INSERT INTO events (title, description, date, location, category) VALUES
('TechFest 2026', 'Annual technology festival with hackathon, robotics, and AI showcases.', '2026-05-15', 'Main Auditorium', 'Tech'),
('Cultural Night', 'A vibrant evening of music, dance, and drama performances.', '2026-05-20', 'Open Air Theatre', 'Cultural'),
('Research Symposium', 'Present and explore cutting-edge academic research from all departments.', '2026-06-01', 'Seminar Hall A', 'Academic');
```

---

### 4️⃣ Configure Database Credentials

Open `backend/db.js` and update the credentials to match your local MySQL setup:

```js
const db = mysql.createConnection({
  host: "localhost",
  user: "root",           // your MySQL username
  password: "your_password",  // your MySQL password
  database: "ku_events"
});
```

> ⚠️ **Security Note:** Never commit real credentials to GitHub. Use a `.env` file and `dotenv` package for production.

---

### 5️⃣ Start the Backend Server

```bash
node backend/server.js
```

You should see:

```
Server running on port 5000 🚀
MySQL Connected ✅
```

The API is now live at: **`http://localhost:5000`**

---

### 6️⃣ Launch the Frontend

Open the `frontend/` folder in VS Code, right-click on `index.html`, and select **"Open with Live Server"**.

The app will open in your browser at: **`http://127.0.0.1:5500/frontend/index.html`**

> 💡 Make sure Live Server is running **at the same time** as the backend so API calls work correctly.

---

## 📡 API Endpoints

Base URL: `http://localhost:5000`

### 🔐 Auth — `/api/auth`

| Method | Endpoint | Description | Body |
|---|---|---|---|
| `POST` | `/api/auth/register` | Register a new user | `{ email, password }` |
| `POST` | `/api/auth/login` | Login with credentials | `{ email, password }` |

**Example — Register:**
```json
POST /api/auth/register
{
  "email": "student@karnavati.edu.in",
  "password": "securepassword"
}
```

**Example — Login Response:**
```json
{
  "id": 1,
  "email": "student@karnavati.edu.in"
}
```

---

### 🎉 Events — `/api/events`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/events` | Fetch all events from the database |

---

### 📝 Event Registration — `/api/register`

| Method | Endpoint | Description | Body |
|---|---|---|---|
| `POST` | `/api/register` | Register a user for an event | `{ user_id, event_id }` |
| `GET` | `/api/register/:userId` | Get all events a user registered for | — |

---

### 📬 Newsletter — `/api/newsletter`

| Method | Endpoint | Description | Body |
|---|---|---|---|
| `POST` | `/api/newsletter` | Subscribe an email to the newsletter | `{ email }` |

---

## 🔁 User Flow

```
1. Open the app → Landing page with hero section
2. Click "Register" → Fill email + password → Account created
3. Click "Login" → Enter credentials → Session saved in localStorage
4. Browse Events → Filter by category or search by name
5. Click "Register" on an event → Confirmation stored in DB
6. Click Profile icon → View account details
7. Click Logout → Session cleared, back to guest mode
8. Subscribe via Newsletter → Email saved to DB
```

---

## 🔮 Future Improvements

- [ ] 🔐 **JWT Authentication** — Replace plain credentials with token-based auth
- [ ] 🛡️ **Password Hashing** — Use `bcrypt` for secure password storage
- [ ] 🔒 **Environment Variables** — Move credentials to `.env` using `dotenv`
- [ ] 🧑‍💼 **Admin Panel** — Dashboard for event creation, editing, and deletion
- [ ] 💺 **Seat Tracking** — Display available seats and close registration when full
- [ ] 📧 **Email Notifications** — Send confirmation emails on registration
- [ ] ☁️ **Cloud Deployment** — Deploy to GCP, Render, or Railway
- [ ] 🧪 **Unit Tests** — Add backend tests with `Jest` or `Mocha`

---

## 👨‍💻 Author

**RAHIL** & **YUG**

> Built with ❤️ for Karnavati University

---

## 📄 License

This project is developed for **educational purposes** as part of a university project.  
Feel free to use, modify, and learn from it.

---

<div align="center">

⭐ If you found this project helpful, give it a star on GitHub!

</div>
