# Secure User Authentication Backend (Prodigy FS-01)

A robust and secure backend authentication system built with Node.js, Express, and MongoDB. This project implements industry-standard security practices to protect user data.

## 🚀 Features

- **User Registration**: Create a new account with hashed passwords.
- **User Login**: Secure authentication with JWT (JSON Web Tokens).
- **Password Hashing**: Uses `bcrypt` for secure password storage.
- **Token-based Auth**: Stateless authentication using JWT stored in HTTP-only cookies.
- **Security Middleware**:
  - `helmet`: Sets various HTTP headers for security.
  - `express-mongo-sanitize`: Prevents NoSQL injection attacks.
  - `hpp`: Prevents HTTP Parameter Pollution.
  - `express-rate-limit`: Rate limiting to prevent brute-force attacks.
  - `cors`: Enables Cross-Origin Resource Sharing.

## 🛠️ Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT (JsonWebToken)
- **Security**: Bcrypt, Helmet, Express-rate-limit

## 📋 Prerequisites

- Node.js (v14+)
- pnpm (or npm/yarn)
- MongoDB Atlas account or local MongoDB instance

## ⚙️ Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone <your-repo-url>
   cd PRODIGY_FS_01
   ```

2. **Install dependencies**:
   ```bash
   pnpm install
   ```

3. **Configure Environment Variables**:
   Create a `.env` file in the root directory and add the following:
   ```env
   PORT=5000
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_super_secret_key
   JWT_EXPIRE=30d
   ```

4. **Run the application**:
   - For development: `pnpm run dev`
   - For production: `pnpm start`

## 🛣️ API Endpoints

### Auth Routes (`/api/auth`)

| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| POST | `/register` | Register a new user | Public |
| POST | `/login` | Login user & get token | Public |
| GET | `/logout` | Logout user & clear cookie| Private |
| GET | `/me` | Get current user's profile | Private |

## 🧪 Testing with Postman/Thunder Client

### Registration
- **URL**: `http://localhost:5000/api/auth/register`
- **Method**: `POST`
- **Body (JSON)**:
  ```json
  {
      "username": "johndoe",
      "email": "john@example.com",
      "password": "password123"
  }
  ```

### Login
- **URL**: `http://localhost:5000/api/auth/login`
- **Method**: `POST`
- **Body (JSON)**:
  ```json
  {
      "email": "john@example.com",
      "password": "password123"
  }
  ```

## 🛡️ Security Features Implemented
- **NoSQL Injection Protection**: Sanitizes user-supplied data to prevent malicious queries.
- **Rate Limiting**: Limits requests to 100 per 10 minutes per IP.
- **Secure Headers**: Implements security headers via Helmet.
- **HTTP Parameter Pollution**: Prevents attacks through redundant query parameters.
- **Cookies**: Uses `httpOnly` cookies for storing JWT to prevent XSS.

## 📄 License
This project is licensed under the ISC License.
