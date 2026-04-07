# 🎓 Karnavati University Events Portal

A premium, full-stack event management system designed for **Karnavati University**. This platform allows students to discover upcoming campus events, register for workshops, manage their profiles, and stay updated through a modern, responsive interface.

---

## ✨ Features

* **🔐 User Authentication**: Secure registration and login system for students.
* **📅 Event Discovery**: Dynamic event grid with live search and category filtering (Tech, Cultural, Sports, Workshops).
* **📝 One-Click Registration**: Authenticated users can instantly register for specific campus events.
* **📧 Newsletter Integration**: Built-in subscription system to keep students informed about campus highlights.
* **🗓️ Interactive Calendar**: A visual modal to track monthly university schedules.
* **📱 Responsive UI**: Optimized for all devices—desktop, tablet, and mobile—using a modern, professional aesthetic.

---

## 🛠️ Tech Stack

* **Frontend**: HTML5, CSS3 (Custom Variables), and Vanilla JavaScript (ES6+).
* **Backend**: Node.js and Express.js.
* **Database**: MySQL.
* **Typography**: Playfair Display & DM Sans via Google Fonts.

---

## 📂 Project Structure

```text
├── backend/
│   ├── routes/
│   │   ├── auth.js        # Registration & Login logic
│   │   ├── events.js      # Fetching event listings from DB
│   │   ├── newsletter.js  # Newsletter subscription logic
│   │   └── register.js    # Event registration logic
│   ├── db.js              # MySQL Connection configuration
│   └── server.js          # Express server entry point (Port 5000)
├── frontend/
│   ├── index.html         # Main User Interface
│   ├── style.css          # Premium styling & animations
│   └── script.js          # Frontend logic & API integration
