# Employee Attendance System

A comprehensive web-based employee attendance management system built with PHP, MySQL, HTML, CSS, and JavaScript. This system provides role-based access for administrators and employees to manage and track attendance records.

## Features

### 🔐 Authentication & Authorization
- User registration and login system
- Role-based access control (Admin/Employee)
- Secure password hashing
- Session management

### 👥 Admin Features
- View and manage all employees
- Delete employee accounts
- View comprehensive attendance records
- Monitor all check-in/check-out activities

### 📊 Employee Features
- Personal attendance tracking
- Check-in and check-out functionality
- View personal attendance history
- Responsive dashboard interface

### 🎨 User Interface
- Modern, responsive design
- Professional color scheme
- Mobile-friendly layout
- Intuitive navigation
- Icon integration with Remix Icons

## Technology Stack

- **Backend**: PHP 7.4+
- **Database**: MySQL 5.7+
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Icons**: Remix Icons
- **Authentication**: PHP Sessions
- **Security**: Password hashing, SQL prepared statements

## Installation & Setup

### Prerequisites
- PHP 7.4 or higher
- MySQL 5.7 or higher
- Web server (Apache/Nginx)
- Modern web browser

### Database Setup
1. Create a MySQL database named `employee_attendance`
2. Run the SQL script to create tables and insert default admin user:
   \`\`\`sql
   -- Default admin credentials
   Email: admin@gmail.com
   Password: admin
   \`\`\`

### Configuration
1. Update database connection settings in `includes/config.php`:
   \`\`\`php
   $host = "localhost";
   $dbname = "employee_attendance";
   $username = "your_username";
   $password = "your_password";
   \`\`\`

### File Structure
\`\`\`
project/
├── includes/
│   ├── config.php          # Database configuration
│   ├── functions.php       # Helper functions
│   ├── header.php         # Common header
│   └── footer.php         # Common footer
├── css/
│   └── styles.css         # Main stylesheet
├── js/
│   ├── auth.js           # Authentication logic
│   ├── admin.js          # Admin dashboard
│   ├── employee.js       # Employee dashboard
│   └── common.js         # Shared functionality
├── index.php             # Landing page
├── login.php             # Login page
├── register.php          # Registration page
├── dashboard.php         # Main dashboard
├── admin_dashboard.php   # Admin interface
└── logout.php            # Logout handler
\`\`\`

## Usage

### For Administrators
1. Login with admin credentials
2. Access the admin dashboard to:
   - View all registered employees
   - Delete employee accounts
   - Monitor attendance records
   - Track check-in/check-out times

### For Employees
1. Register a new account or login
2. Use the employee dashboard to:
   - Check in at the start of work
   - Check out at the end of work
   - View personal attendance history

## API Endpoints (if applicable)

### Authentication
- `POST /login.php` - User login
- `POST /register.php` - User registration
- `GET /logout.php` - User logout

### Attendance
- `POST /dashboard.php` - Check in/out
- `GET /dashboard.php` - View attendance records

## Database Schema

### Users Table
\`\`\`sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    role ENUM('admin', 'employee') NOT NULL DEFAULT 'employee',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
\`\`\`

### Attendance Table
\`\`\`sql
CREATE TABLE attendance (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    date DATE NOT NULL,
    check_in TIME NOT NULL,
    check_out TIME NULL DEFAULT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
\`\`\`

## Security Features

- **Password Security**: All passwords are hashed using PHP's `password_hash()`
- **SQL Injection Prevention**: Prepared statements used for all database queries
- **Session Management**: Secure session handling for user authentication
- **Input Validation**: Server-side validation and sanitization
- **Role-based Access**: Proper authorization checks for admin functions

## Configuration

### Environment Variables
Create a `.env` file in the root directory:
\`\`\`env
DB_HOST=localhost
DB_NAME=employee_attendance
DB_USER=your_username
DB_PASS=your_password
\`\`\`

### Web Server Configuration

#### Apache (.htaccess)
```apache
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php [QSA,L]
