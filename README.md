# 🚲 Smart Bike & Vehicle Rental Platform

A modern, full-stack web application for renting and listing bikes, scooters, and motorcycles. Built with the **MERN** stack (MongoDB, Express, React 19, Node.js), **Tailwind CSS**, **Socket.io**, **Razorpay**, and **Groq AI**.

---

## ✨ Features

### 👤 User (Renter) Features
- **User Authentication**: Secure signup and login with JWT and email OTP verification.
- **Smart Location & Map Search**: Explore available vehicles nearby using interactive **Leaflet** maps and OpenStreetMap geolocation search.
- **Vehicle Catalog & Filtering**: Browse bikes by category, location, pricing, and date availability.
- **Seamless Booking Flow**: Select rental date/time ranges with automatic price calculations.
- **Online Payment Integration**: Secure payment processing with **Razorpay**.
- **Real-Time Live Chat**: Direct 1-on-1 socket-powered messaging with vehicle owners.
- **AI Rental Assistant**: Integrated AI chatbot powered by **Groq** for vehicle recommendations, platform guides, and instant queries.
- **User Dashboard**: Manage active and past bookings, view payment status, and chat history.

### 🔑 Owner Features
- **Fleet & Listing Management**: Add, update, or remove vehicles with high-resolution image uploads via **Cloudinary**.
- **Interactive Location Pinning**: Geocode vehicle pickup locations directly on the map.
- **Booking Approvals**: View, accept, reject, or mark bookings as completed.
- **Owner Dashboard**: Monitor total listings, rental requests, earnings, and customer messages.

---

## 🛠️ Tech Stack

### **Frontend**
- **Framework**: [React 19](https://react.dev/) + [Vite](https://vitejs.dev/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/) + [Lucide React Icons](https://lucide.dev/)
- **Routing**: `react-router-dom` (v7)
- **Maps**: `leaflet` & `react-leaflet` (OpenStreetMap)
- **Real-time Engine**: `socket.io-client`
- **HTTP Client**: `axios`
- **Date Utilities**: `date-fns` & `react-datepicker`

### **Backend**
- **Runtime**: [Node.js](https://nodejs.org/) & [Express.js](https://expressjs.com/)
- **Database**: [MongoDB Atlas](https://www.mongodb.com/atlas) with [Mongoose](https://mongoosejs.com/)
- **Authentication**: `jsonwebtoken` (JWT) & `bcryptjs`
- **File Storage**: [Cloudinary](https://cloudinary.com/) (via `multer`)
- **Payments**: [Razorpay API](https://razorpay.com/)
- **Real-time Chat**: `socket.io`
- **Email Services**: `nodemailer` (OTP generation & notifications)
- **AI Integration**: Groq API (Llama LLM models)

---

## 📂 Project Structure

```text
Bike_rental_Project/
├── client/                       # React Frontend Application
│   ├── public/                   # Static public assets
│   ├── src/
│   │   ├── assets/               # Local images and icons
│   │   ├── components/           # Reusable UI Components
│   │   │   ├── AIChatBot.jsx     # AI Virtual Assistant widget
│   │   │   ├── Navbar.jsx        # Navigation Header
│   │   │   ├── OwnerChat.jsx     # Owner real-time chat window
│   │   │   ├── UserChat.jsx      # Customer real-time chat window
│   │   │   ├── VehicleMap.jsx    # Interactive Leaflet Map view
│   │   │   └── SmartLocationSearch.jsx # Address auto-complete search
│   │   ├── pages/                # Main Application Views
│   │   │   ├── Home.jsx          # Landing page
│   │   │   ├── Login.jsx         # Auth Login page
│   │   │   ├── Register.jsx      # User/Owner Registration with OTP
│   │   │   ├── VehicleListing.jsx# Browse & search bikes
│   │   │   ├── VehicleDetail.jsx # Detailed bike view & booking form
│   │   │   ├── UserDashboard.jsx # Renter booking history & messages
│   │   │   └── OwnerDashboard.jsx# Vehicle listing & request management
│   │   ├── App.jsx               # App routes setup
│   │   └── main.jsx              # React app entry point
│   ├── .env                      # Frontend environment variables
│   ├── package.json              # Frontend dependencies
│   └── vite.config.js            # Vite build configuration
│
└── server/                       # Express Node.js API Backend
    ├── config/                   # Configuration files (DB connection, Cloudinary)
    ├── controllers/              # Business logic for endpoints
    │   ├── aiController.js       # Groq AI chatbot logic
    │   ├── authController.js     # User registration, login, OTP
    │   ├── bookingController.js  # Booking status and history
    │   ├── chatController.js     # Message history retrieval
    │   ├── paymentController.js  # Razorpay order generation & verification
    │   └── vehicleController.js  # Vehicle CRUD operations & search filters
    ├── middleware/               # Middleware (Auth verification, Multer upload)
    ├── models/                   # Mongoose DB Schemas
    │   ├── Booking.js
    │   ├── ChatRoom.js
    │   ├── Message.js
    │   ├── OTP.js
    │   ├── Owner.js
    │   ├── Payment.js
    │   ├── Review.js
    │   ├── User.js
    │   └── Vehicle.js
    ├── routes/                   # API Routes endpoints
    ├── utils/                    # Helper scripts (Email dispatchers)
    ├── server.js                 # HTTP & WebSockets Server entry point
    ├── .env                      # Backend environment variables
    └── package.json              # Backend dependencies
```

---

## ⚡ Getting Started

### 📋 Prerequisites
Make sure you have the following installed on your machine:
- [Node.js](https://nodejs.org/) (v18.x or higher)
- [npm](https://www.npmjs.com/) (v9.x or higher)
- [MongoDB Database](https://www.mongodb.com/) (Local instance or MongoDB Atlas URI)

---

### ⚙️ Environment Configuration

#### 1. Backend Environment Setup (`server/.env`)
Create a `.env` file inside the `server/` directory with the following variables:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key

# Cloudinary Setup (Image Uploads)
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

# Razorpay Integration
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret

# Email Configuration (Nodemailer for OTP)
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_email_app_password

# AI Chatbot Setup
GROQ_API_KEY=your_groq_api_key
```

#### 2. Frontend Environment Setup (`client/.env`)
Create a `.env` file inside the `client/` directory with the following variables:

```env
VITE_RAZORPAY_KEY_ID=your_razorpay_key_id
```

---

## 🚀 Running the Project

### 1. Start the Backend Server
```bash
cd server
npm install
node server.js
```
*The server will run on `http://localhost:5000`.*

---

### 2. Start the Frontend Application
In a new terminal window:

```bash
cd client
npm install
npm run dev
```
*The React app will be accessible at `http://localhost:5173`.*

---

## 🔌 API Endpoints Summary

| Module | Route | Method | Description |
| :--- | :--- | :--- | :--- |
| **Auth** | `/api/auth/register` | `POST` | Register user & send OTP |
| **Auth** | `/api/auth/verify-otp` | `POST` | Verify email OTP & create account |
| **Auth** | `/api/auth/login` | `POST` | Authenticate user & receive JWT |
| **Vehicles** | `/api/vehicles` | `GET` | Get all vehicles with optional filters |
| **Vehicles** | `/api/vehicles/:id` | `GET` | Get single vehicle details |
| **Vehicles** | `/api/vehicles` | `POST` | Add a new vehicle (Owner only, image upload) |
| **Bookings** | `/api/bookings` | `POST` | Create a new rental booking request |
| **Bookings** | `/api/bookings/user` | `GET` | Get current user's booking history |
| **Payments** | `/api/payments/create-order` | `POST` | Create Razorpay payment order |
| **Payments** | `/api/payments/verify` | `POST` | Verify Razorpay payment signature |
| **Chats** | `/api/chats/history/:roomId`| `GET` | Fetch room message history |
| **AI** | `/api/ai/chat` | `POST` | Ask AI Assistant questions |

---

## 🤝 Contributing

Contributions are welcome! Feel free to fork this repository, submit issues, or open pull requests to enhance the functionality.

---

## 📄 License

This project is licensed under the **ISC License**.
