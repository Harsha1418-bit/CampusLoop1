# CampusLoop - Setup Guide

## 🚀 Quick Start Guide

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (v5 or higher)
- npm or yarn package manager

---

## 📦 Backend Setup

### 1. Navigate to Backend Directory
```bash
cd backend
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Environment Variables
Create a `.env` file in the `backend` directory:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database
MONGODB_URI=mongodb://localhost:27017/campusloop

# JWT Secret
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
JWT_EXPIRE=7d

# Cloudinary Configuration (Optional - for image uploads)
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email Configuration (Optional - for password reset)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASSWORD=your_app_password

# Frontend URL
FRONTEND_URL=http://localhost:3000
```

### 4. Start MongoDB
Make sure MongoDB is running on your system:
```bash
# Windows
net start MongoDB

# macOS/Linux
sudo systemctl start mongod
```

### 5. Run Backend Server
```bash
# Development mode with auto-reload
npm run dev

# Production mode
npm start
```

Backend will run on: **http://localhost:5000**

---

## 🎨 Frontend Setup

### 1. Navigate to Frontend Directory
```bash
cd frontend
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Environment Variables (Optional)
Create a `.env` file in the `frontend` directory:

```env
REACT_APP_API_URL=http://localhost:5000/api
```

### 4. Run Frontend Application
```bash
npm start
```

Frontend will run on: **http://localhost:3000**

---

## 🔧 Initial Setup

### 1. Initialize Default Clubs
After starting the backend, you can initialize the default SNIST clubs:

**Method 1: Using API (Postman/Thunder Client)**
```
POST http://localhost:5000/api/clubs/initialize
Headers:
  Authorization: Bearer <admin_or_developer_token>
```

**Method 2: Using MongoDB Compass**
Import the clubs manually or wait for admin to create them through the UI.

### 2. Create Default Developer Account
You can create a developer account through the signup page or directly in MongoDB:

```javascript
{
  "name": "Dev Admin",
  "username": "devadmin",
  "email": "dev@campusloop.edu",
  "password": "campus@123", // Will be hashed automatically
  "developerRole": "Full Stack",
  "role": "developer",
  "isActive": true
}
```

---

## 👥 User Roles & Access

### Student Portal
- **Features**: Club membership, DSA challenges, attendance, marks, events
- **Signup Fields**: Name, Roll Number, Email, Phone, Department, Year, Section, DOB, Gender, Clubs

### Faculty Portal
- **Features**: Class management, announcements, attendance marking, marks upload
- **Signup Fields**: Name, Faculty ID, Email, Phone, Designation, Department, Qualification, Experience

### Admin Portal
- **Features**: User management, event approvals, analytics, global announcements
- **Signup Fields**: Name, Admin ID, Email, Phone, Designation, Department

### Developer Portal
- **Features**: System management, bug tracking, API monitoring, deployments
- **Signup Fields**: Name, Developer ID, Email, Developer Role
- **Default Credentials**: 
  - Username: `devadmin`
  - Password: `campus@123`

---

## 🧪 Testing the Application

### 1. Test Backend API
```bash
# Health check
curl http://localhost:5000/api/health

# Get all clubs
curl http://localhost:5000/api/clubs
```

### 2. Test Frontend
1. Open browser: http://localhost:3000
2. Click "Sign Up" and create an account
3. Login with your credentials
4. Explore the dashboard

---

## 📱 Features Checklist

### Authentication
- [x] JWT-based authentication
- [x] Role-based access control (Student, Faculty, Admin, Developer)
- [x] Password hashing with bcrypt
- [x] Forgot password functionality
- [x] Profile photo upload

### Student Features
- [x] Club selection during signup
- [x] Multiple club membership
- [x] DSA daily challenges
- [x] Streak & XP tracking
- [x] Leaderboard system
- [x] Badges & achievements
- [x] Announcements view
- [x] Event calendar

### Faculty Features
- [x] Class schedule management
- [x] Post announcements
- [x] Attendance marking
- [x] Marks upload
- [x] Student performance reports
- [x] Query session management

### Admin Features
- [x] User management (CRUD)
- [x] Event approval system
- [x] Global announcements
- [x] Analytics dashboard
- [x] Department statistics
- [x] System health monitoring

### Developer Features
- [x] User management
- [x] Bug tracking system
- [x] API health monitoring
- [x] System metrics dashboard
- [x] Deployment controls
- [x] Database management

---

## 🎨 UI/UX Features

- [x] Picto theme-inspired design
- [x] Dark mode support
- [x] Responsive design (mobile & desktop)
- [x] Smooth animations
- [x] Modern gradient colors
- [x] Accessible UI components
- [x] Loading states
- [x] Error handling

---

## 🐛 Troubleshooting

### Backend Issues

**MongoDB Connection Error**
```
Solution: Make sure MongoDB is running and the connection string is correct
```

**Port Already in Use**
```
Solution: Change PORT in .env file or kill the process using port 5000
```

### Frontend Issues

**Cannot Connect to API**
```
Solution: Ensure backend is running and REACT_APP_API_URL is correct
```

**Tailwind CSS Not Working**
```
Solution: Run 'npm install' again and restart the dev server
```

---

## 📚 API Documentation

### Authentication Endpoints
- `POST /api/auth/signup` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user
- `POST /api/auth/forgot-password` - Request password reset
- `PUT /api/auth/reset-password/:token` - Reset password

### Club Endpoints
- `GET /api/clubs` - Get all clubs
- `GET /api/clubs/:id` - Get single club
- `POST /api/clubs` - Create club (Admin/Faculty)
- `POST /api/clubs/:id/join` - Join club (Student)
- `DELETE /api/clubs/:id/leave` - Leave club (Student)
- `PUT /api/clubs/:id` - Update club (Admin/Faculty)
- `DELETE /api/clubs/:id` - Delete club (Admin)
- `POST /api/clubs/initialize` - Initialize default clubs (Admin/Developer)

---

## 🚀 Deployment

### Backend Deployment (Heroku/Railway/Render)
1. Push code to GitHub
2. Connect repository to hosting platform
3. Set environment variables
4. Deploy

### Frontend Deployment (Vercel/Netlify)
1. Push code to GitHub
2. Connect repository to hosting platform
3. Set build command: `npm run build`
4. Set publish directory: `build`
5. Deploy

### Database (MongoDB Atlas)
1. Create free cluster on MongoDB Atlas
2. Get connection string
3. Update MONGODB_URI in backend .env

---

## 📞 Support

For issues or questions:
- Email: support@campusloop.edu
- GitHub Issues: [Create an issue]
- Documentation: [Read the docs]

---

## 📄 License

MIT License - feel free to use this project for your hackathon or educational purposes.

---

**Built with ❤️ for SNIST Campus Community**
