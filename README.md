<div align="center">

# 🎟️ EventoEMS — Event Management & Digital Ticketing Platform

An end-to-end full-stack event management and digital ticketing solution designed to streamline event scheduling, attendee registration, and QR-based ticket verification.

[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Vite](https://img.shields.io/badge/Vite-Bundler-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)

---

### **Developed by [Mohit Kumar](mailto:mohitkumar947275@gmail.com)**

</div>

## 📌 Overview

**EventoEMS** is a modern MERN stack web application built to eliminate the hassle of physical ticket distribution and fragmented event scheduling. Whether managing campus symposiums, workshops, concerts, or conferences, the platform provides organizers with full control over event creation and ticket quotas while providing attendees with an intuitive discovery interface, calendar scheduling, and instant QR-powered digital ticket issuance.

---

## ✨ Key Features

- **🔐 Secure Authentication & Session Management:**
  - JWT (JSON Web Tokens) with secure HTTP-only cookies.
  - Salted password hashing via `bcryptjs`.
  - Persistent login state managed via React Context API (`UserContext`).

- **📅 Interactive Event Discovery & Monthly Calendar:**
  - Real-time search and date filtering for active/upcoming events.
  - Interactive full-month calendar view powered by `date-fns` for easy visual scheduling.
  - Social engagement counters (event likes & attendee counters).

- **🎟️ End-to-End Ticketing & QR Code Automation:**
  - Automated dynamic QR code generation for confirmed bookings.
  - QR codes encode verified ticket ID, attendee name, and event details for on-site scanning.
  - Centralized **Digital Ticket Wallet** (`/wallet`) allowing users to view, verify, and cancel bookings.

- **🛠️ Comprehensive Organizer Dashboard:**
  - Create and publish events with custom banner uploads using `Multer`.
  - Configurable ticket pricing (Free / Paid), location, date, time, and participant capacity limits.

- **💳 Smooth Multi-Step Checkout:**
  - Dedicated Order Summary and Payment Summary workflows ensuring clear pricing and attendee confirmation before ticket generation.

---

## 🛠️ Tech Stack

### **Frontend**
- **Library / Framework:** React 18 (Vite)
- **Styling:** Tailwind CSS, PostCSS
- **Routing:** React Router v6
- **State Management:** React Context API
- **Date Handling:** `date-fns`
- **Icons & QR:** `react-icons`, `qrcode`
- **HTTP Client:** Axios (with cookie credentials enabled)

### **Backend**
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB Atlas / Local MongoDB with Mongoose ODM
- **Authentication:** JSON Web Tokens (`jsonwebtoken`), `bcryptjs`, `cookie-parser`
- **File Uploads:** Multer (multipart/form-data for event media)
- **CORS:** Configured for cross-origin credentials with Vite dev server

---

## 📂 Project Structure

```text
EventoEMS/
├── api/                          # Express & Node.js Backend
│   ├── models/                   # Mongoose Database Models
│   │   ├── Ticket.js             # Ticket & QR Schema
│   │   └── User.js               # User Schema
│   ├── uploads/                  # Uploaded Event Images & Banners
│   ├── .env                      # Backend Environment Variables
│   ├── index.js                  # Express Server & REST API Routes
│   └── package.json
│
├── client/                       # React & Vite Frontend
│   ├── src/
│   │   ├── assets/               # Static Logos & Graphic Assets
│   │   ├── pages/                # Application Page Components
│   │   │   ├── AddEvent.jsx      # Event Creation Page
│   │   │   ├── CalendarView.jsx  # Interactive Monthly Calendar
│   │   │   ├── EventPage.jsx     # Event Details & Overview
│   │   │   ├── IndexPage.jsx     # Homepage & Event Listing Feed
│   │   │   ├── LoginPage.jsx     # User Sign-In
│   │   │   ├── RegisterPage.jsx  # User Registration
│   │   │   ├── OrderSummary.jsx  # Booking Confirmation
│   │   │   ├── PaymentSummary.jsx# Payment Flow & QR Issuance
│   │   │   ├── TicketPage.jsx    # User Ticket Wallet
│   │   │   └── Header.jsx        # Navigation & Live Search
│   │   ├── UserContext.jsx       # Global Auth Context Provider
│   │   ├── App.jsx               # Routes Definition
│   │   └── main.jsx
│   ├── tailwind.config.js
│   ├── vite.config.js
│   └── package.json
└── README.md
```

---

## 🚀 Getting Started

Follow these instructions to set up and run the project locally.

### Prerequisites
- [Node.js](https://nodejs.org/) (v16.x or higher)
- [npm](https://www.npmjs.com/) (v8.x or higher)
- [MongoDB](https://www.mongodb.com/) (Local instance or MongoDB Atlas connection URI)

---

### 1. Clone the Repository
```bash
git clone https://github.com/mohit-kumar-28/EventoEMS.git
cd EventoEMS
```

---

### 2. Backend Setup (`/api`)

1. Open a terminal and navigate to the `api` directory:
   ```bash
   cd api
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Configure the environment variables in `api/.env`:
   ```env
   PORT=4000
   MONGO_URL=mongodb+srv://<username>:<password>@cluster0.mongodb.net/eventoems
   ```
4. Start the backend server:
   ```bash
   npm start
   ```
   *(Server will start on `http://localhost:4000`)*

---

### 3. Frontend Setup (`/client`)

1. Open a separate terminal and navigate to the `client` directory:
   ```bash
   cd client
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Launch the Vite development server:
   ```bash
   npm run dev
   ```
   *(Client will be accessible at `http://localhost:5173`)*

---

## 🔌 API Endpoints Reference

| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :---: |
| `POST` | `/register` | Register a new user | ❌ |
| `POST` | `/login` | Authenticate user & issue JWT cookie | ❌ |
| `GET` | `/profile` | Fetch authenticated user details | ✅ |
| `POST` | `/logout` | Invalidate session cookie | ✅ |
| `POST` | `/createEvent` | Create new event with image upload | ✅ |
| `GET` | `/events` / `/createEvent` | List all available events | ❌ |
| `GET` | `/event/:id` | Get specific event details | ❌ |
| `POST` | `/event/:eventId` | Like / upvote an event | ❌ |
| `POST` | `/tickets` | Generate and store booked ticket with QR | ✅ |
| `GET` | `/tickets/user/:userId` | Get all tickets booked by a user | ✅ |
| `DELETE`| `/tickets/:id` | Cancel / remove a ticket pass | ✅ |

---

## 👨‍💻 Author

**Mohit Kumar**  
- **Email:** [mohitkumar947275@gmail.com](mailto:mohitkumar947275@gmail.com)  
- **Role:** Full-Stack Developer & UI Architect  