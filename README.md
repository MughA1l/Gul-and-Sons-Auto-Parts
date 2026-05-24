# 🚗 Gull & Sons Auto Parts - E-Commerce Platform

A full-stack web application for buying and selling automotive parts with real-time chat, admin dashboard, and advanced e-commerce features.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Environment Variables](#environment-variables)
- [Contributing](#contributing)
- [License](#license)

---

## ✨ Features

### 🛍️ Customer Features
- Browse and search automotive parts
- Filter by categories and brands
- Add products to cart and wishlist
- Secure checkout process
- Real-time chat support with admin
- Order tracking and history
- User profile management

### 👨‍💼 Admin Features
- Dashboard with analytics and sales metrics
- Manage products, categories, and brands
- View and manage customer orders
- Customer communication via chat
- Order status updates
- Real-time admin notifications
- Top selling products tracking

### 🔐 Security & Performance
- JWT authentication with refresh tokens
- Password encryption with bcryptjs
- Rate limiting on API endpoints
- Request validation and sanitization
- CORS enabled
- MongoDB for reliable data storage
- Socket.io for real-time communication

---

## 🛠️ Tech Stack

### Frontend
- **React 18** - UI library
- **Vite** - Build tool
- **Redux Toolkit** - State management
- **React Router v6** - Client-side routing
- **Axios** - HTTP client
- **Socket.io Client** - Real-time chat
- **Framer Motion** - Animations
- **React Hook Form** - Form management
- **React Hot Toast** - Notifications
- **Victory Charts** - Analytics charts
- **Lucide Icons** - UI icons

### Backend
- **Node.js & Express** - Server framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Authentication
- **bcryptjs** - Password hashing
- **Socket.io** - Real-time communication
- **Multer** - File uploads
- **Nodemailer** - Email service
- **PDFKit** - Invoice generation
- **Morgan** - HTTP logging

---

## 📁 Project Structure

```
Ibrahim Project/
├── backend/
│   ├── src/
│   │   ├── config/          # Database configuration
│   │   ├── controllers/     # Route handlers
│   │   ├── middlewares/     # Custom middlewares
│   │   ├── models/          # MongoDB schemas
│   │   ├── routes/          # API routes
│   │   ├── services/        # Business logic
│   │   └── utils/           # Helper functions
│   ├── uploads/             # File storage
│   ├── server.js            # Express server
│   ├── package.json
│   └── .env
│
├── frontend/
│   ├── src/
│   │   ├── api/             # API endpoints
│   │   ├── components/      # Reusable components
│   │   ├── pages/           # Page components
│   │   ├── store/           # Redux store
│   │   ├── context/         # Theme context
│   │   └── utils/           # Helper functions
│   ├── public/              # Static files
│   ├── package.json
│   ├── vite.config.js
│   └── index.html
│
└── README.md                # This file
```

---

## 🚀 Installation

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or Atlas)
- Git

### Backend Setup

```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install

# Create .env file locally and keep it private
# The repository ignores .env files by default

# Start the server
npm run dev    # Development with nodemon
npm start      # Production mode

# Seed the database (optional)
npm run seed
```

### Frontend Setup

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

---

## 💻 Usage

1. **Start Backend Server**
   ```bash
   cd backend
   npm run dev
   ```
   Server runs on `http://localhost:5000`

2. **Start Frontend Server**
   ```bash
   cd frontend
   npm run dev
   ```
   App runs on `http://localhost:5173`

3. **Access the Application**
   - Customer: `http://localhost:5173`
   - Admin Dashboard: `http://localhost:5173/admin` (admin login required)

---

## 📡 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `POST /api/auth/refresh` - Refresh access token
- `POST /api/auth/forgot-password` - Request password reset
- `POST /api/auth/reset-password` - Reset password with OTP
- `GET /api/auth/me` - Get current user (Protected)

### Products
- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get product details
- `GET /api/products/featured` - Get featured products
- `GET /api/products/top-selling` - Get top selling products

### Cart
- `GET /api/cart` - Get user cart
- `POST /api/cart` - Add item to cart
- `PUT /api/cart/:itemId` - Update cart item quantity
- `DELETE /api/cart/:itemId` - Remove item from cart

### Orders
- `POST /api/orders` - Create new order
- `GET /api/orders` - Get user orders
- `GET /api/orders/:id` - Get order details

### Chat
- `GET /api/chat/messages` - Get chat messages
- `POST /api/chat/messages` - Send message

### Admin Routes (Protected)
- `GET /api/admin/orders` - Get all orders
- `GET /api/admin/analytics/*` - Analytics data
- `GET /api/admin/customers` - Get all customers

---

## 🔧 Environment Variables

### Backend (.env)
```
PORT=5000
NODE_ENV=development
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
JWT_REFRESH_SECRET=your_refresh_secret
JWT_EXPIRE=15m
JWT_REFRESH_EXPIRE=7d
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password
CLIENT_URL=http://localhost:5173
UPLOAD_PATH=./uploads
MAX_FILE_SIZE=5242880
```

### Frontend (.env)
```
VITE_API_URL=http://localhost:5000
```

---

## 🌐 Vercel Deployment

This repository contains both apps in one monorepo:
- `frontend/` for the React app
- `backend/` for the API

### Deploy Frontend on Vercel
1. Import this GitHub repo into Vercel.
2. Set `Root Directory` to `frontend`.
3. Set these values:
   - `Build Command`: `npm run build`
   - `Output Directory`: `dist`
   - `Install Command`: `npm install`
4. Add env var:
   - `VITE_API_URL=https://your-backend-domain.vercel.app`
5. Redeploy.

### Deploy Backend on Vercel
1. Create a second Vercel project from the same GitHub repo.
2. Set `Root Directory` to `backend`.
3. Set these values:
   - `Build Command`: `npm run build`
   - `Output Directory`: leave default for the Node function setup
   - `Install Command`: `npm install`
4. Add env vars:
   - `MONGO_URI`
   - `JWT_SECRET`
   - `CLIENT_URL=https://your-frontend-domain.vercel.app`
5. Redeploy.

### Important
- Frontend and backend should be two separate Vercel projects.
- After changing env vars, use `Clear cache and redeploy`.
- If the backend returns `500`, check Vercel function logs first.

---

## 📞 Contact

- WhatsApp support: `+923263133136`
- Instagram: https://www.instagram.com/gullautoparts.pk?igsh=ODA5c25vb2V4ZXVx
- Facebook: https://www.facebook.com/share/18fsjsHVuk/
- YouTube: https://youtube.com/@gullandsonsautoparts?si=47XXV_xx466NHFn7

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 👨‍💻 Author

**Ibrahim Project** - Auto Parts E-Commerce Platform

## 📞 Support

For support, email your-email@example.com or open an issue in the repository.

---

**⭐ If you found this project helpful, please consider giving it a star on GitHub!**

