# User Management System

## 📌 Overview
This project ***not yet*** is a **User Management System** built with **HTML, CSS, Bootstrap, PHP, Java, and MySQL**. It provides user authentication using **JWT and OAuth (Google, Facebook, GitHub, etc.)** and different access levels for users and admins. Users can manage their personal information, while admins can manage all users and track modifications.

## 🚀 Features
### ✅ Authentication
- JWT-based authentication
- OAuth authentication with Google (expandable to Facebook, GitHub, etc.)
- User login & registration
- Logout functionality
- Password reset (optional, can be added)

### ✅ User Dashboard
- Fetch & display user information in an elegant table
- Modify or delete personal information

### ✅ Admin Dashboard
- Fetch & display all users' information
- Track user modifications in a **log system**
- Delete users

### ✅ Security & Performance
- **JWT Middleware** to protect sensitive routes
- **AJAX integration** for seamless user experience
- **Environment variables (`.env`)** for sensitive credentials

---

## 📂 Project Structure
```
/user-management-system
│── /config
│   ├── database.php          # Database connection
│── /auth
│   ├── login.php             # JWT & OAuth login
│   ├── register.php          # User registration
│   ├── logout.php            # Logout
│── /dashboard
│   ├── user-dashboard.php    # User's personal data
│   ├── admin-dashboard.php   # Admin panel
│── /api
│   ├── auth.php              # Authentication API (JWT handling)
│   ├── user.php              # User CRUD operations
│── /assets
│   ├── styles.css            # Custom CSS
│   ├── script.js             # JavaScript (AJAX, UI interactions)
│── index.php                 # Home/Login Page
│── .htaccess                 # URL rewriting for clean routes
│── README.md                 # Project documentation
```

---

## 🛠️ Installation & Setup
### 1️⃣ Clone the repository
```bash
git clone https://github.com/aboualine/user-management-system.git
cd user-management-system
```

### 2️⃣ Install Dependencies
Make sure you have **PHP, MySQL**, and **Composer** installed.
```bash
composer install
```

### 3️⃣ Set Up Environment Variables
Create a `.env` file in the root directory and add your credentials:
```
DB_HOST=localhost
DB_NAME=user_management
DB_USER=root
DB_PASS=password
JWT_SECRET=your_jwt_secret
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
```

### 4️⃣ Set Up Database
Import the `database.sql` file into MySQL.
```sql
CREATE DATABASE user_management;
USE user_management;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    password VARCHAR(255),
    role ENUM('user', 'admin') DEFAULT 'user',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE logs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    action VARCHAR(255),
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
```

### 5️⃣ Start the Server
```bash
php -S localhost:8000
```
Then visit `http://localhost:8000` in your browser.

---

## 🔑 Authentication API Endpoints
| Method | Endpoint          | Description |
|--------|------------------|-------------|
| `POST` | `/api/auth.php`  | Login & JWT Authentication |
| `POST` | `/auth/register.php` | Register a new user |
| `GET`  | `/auth/logout.php`   | Logout user |
| `GET`  | `/api/user.php`  | Fetch user info |
| `POST` | `/api/user.php`  | Update user info |
| `DELETE` | `/api/user.php` | Delete user |

---

## 📜 Logs & Admin Monitoring
- The `logs` table tracks all user modifications.
- Admins can view logs in `admin-dashboard.php`.
- Users **cannot** delete logs, only admins can.

---

## 🎨 Frontend Enhancements
- Bootstrap for a **modern UI**
- **AJAX integration** for real-time updates
- Custom CSS in `/assets/styles.css`

---

## 🛡 Security Measures
- **JWT Token Validation**: Prevents unauthorized access.
- **Prepared Statements**: Prevents SQL Injection.
- **Rate-Limiting**: Prevents brute force attacks (to be added).
- **HTTPS Only Cookies**: Ensures secure authentication.

---

## 🚀 Future Improvements
- Add **Facebook & GitHub OAuth** authentication
- Implement **Two-Factor Authentication (2FA)**
- Add **Email Verification** for new users

---


## 📄 License
MIT License - Use this project freely!

