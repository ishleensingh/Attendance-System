# Employee Attendance System

A simple web-based attendance tracking system for educational purposes. Built with PHP, MySQL, HTML, CSS, and JavaScript.

## What it does

- Employees can register and log in
- Check in/out with one click
- View attendance history
- Admin can manage employees and view all records

## How to run it

### You need:
- XAMPP or WAMP (includes Apache, PHP, MySQL)
- Any web browser

### Setup steps:

1. **Install XAMPP**
   - Download from [xampp.org](https://www.apachefriends.org/)
   - Install and start Apache + MySQL

2. **Setup the project**
   - Copy all files to `xampp/htdocs/attendance-system/`
   - Open phpMyAdmin (http://localhost/phpmyadmin)
   - Create database named `employee_attendance`
   - Import the SQL file to create tables

3. **Run the app**
   - Go to `http://localhost/attendance-system/`
   - Use default admin login: admin@gmail.com / admin

## File structure

```
attendance-system/
├── login.php           # Login page
├── register.php        # Employee registration  
├── dashboard.php       # Employee dashboard
├── admin_dashboard.php # Admin panel
├── css/styles.css      # All styling
├── js/                 # JavaScript files
└── includes/           # PHP functions and config
```

## Default login

**Admin account:**
- Email: admin@gmail.com
- Password: admin

## Features

**For employees:**
- Register new account
- Check in when arriving
- Check out when leaving
- See your attendance history

**For admin:**
- View all employees
- Delete employee accounts
- See everyone's attendance records

## Learning goals

This project demonstrates:
- PHP basics (forms, sessions, database)
- MySQL database design
- User authentication
- CRUD operations
- Responsive web design
- JavaScript DOM manipulation

---

*This is an educational project - not for production use!*
