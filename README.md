# CampusLoop - Unified Campus Management Platform

**Tagline:** "One Loop for All Campus Needs"

## 🎯 Overview

CampusLoop is a comprehensive campus management and engagement platform with separate portals for:
- 👨‍🎓 Students
- 👩‍🏫 Faculty/Teachers
- 🧑‍💼 Administrators
- 💻 Developers/SDC

## 🚀 Tech Stack

**Backend:**
- PHP 7.4+ with PDO
- MySQL/MariaDB Database
- JWT Authentication (Custom implementation)
- Apache Web Server
- RESTful API Architecture

**Frontend:**
- React.js
- Tailwind CSS (Picto Theme)
- Axios
- React Router

## 🏗️ Project Structure

```
CampusLoop/
├── frontend/          # React.js with Tailwind CSS
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── context/
│   │   └── App.js
│   └── package.json
│
└── backend/           # PHP + MySQL Backend
    ├── config/        # Database & app config
    ├── controllers/   # API logic
    ├── models/        # Data models
    ├── utils/         # JWT & helpers
    ├── database/      # SQL schema
    ├── .htaccess      # URL rewriting
    └── index.php      # Main router
```

## 🚀 Quick Start

### 1. Setup Database
```bash
cd backend
php setup.php
```

### 2. Start XAMPP
- Start Apache
- Start MySQL

### 3. Test Backend
Open: `http://localhost/CampusIoop/backend/api/health`

### 4. Start Frontend
```bash
cd frontend
npm install
npm start
```

Open: `http://localhost:3000`

## 🔐 Default Developer Credentials
- Username: `devadmin`
- Password: `campus@123`

## 📚 Documentation
- **[QUICK_START.md](QUICK_START.md)** - 5-minute setup guide
- **[MIGRATION_GUIDE.md](MIGRATION_GUIDE.md)** - PHP migration details
- **[backend/README.md](backend/README.md)** - API documentation

## 📋 Features

### Student Portal
- Club membership selection during signup
- DSA daily challenges with streak tracking
- Attendance & marks (ERP integration)
- Event calendar & announcements
- Leaderboard & badges

### Faculty Portal
- Class schedule management
- Post announcements
- Attendance verification
- Upload marks/assessments
- Student performance reports

### Admin Portal
- User role management
- Global announcements
- Event approval system
- Analytics dashboard
- Communication panel

### Developer Portal
- User management (CRUD operations)
- Bug reports & feature requests
- API health monitoring
- Deployment controls
- System logs & metrics

## 📄 License
MIT License
