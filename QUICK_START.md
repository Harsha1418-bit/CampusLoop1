# 🚀 CampusLoop - Quick Start Guide

## ⚡ Get Running in 5 Minutes!

### Prerequisites
- ✅ XAMPP installed
- ✅ Node.js installed (for frontend)

---

## 📋 Step-by-Step Setup

### 1️⃣ Start XAMPP (30 seconds)

1. Open **XAMPP Control Panel**
2. Click **Start** next to Apache
3. Click **Start** next to MySQL
4. Wait for green indicators

### 2️⃣ Setup Database (1 minute)

Open terminal in backend folder:
```bash
cd C:\xampp\htdocs\CampusIoop\backend
php setup.php
```

You should see:
```
=== CampusLoop Database Setup ===

✓ Connected to MySQL
✓ Database 'campusloop' created/verified
✓ Database schema created successfully
✓ Default developer account created
  Username: devadmin
  Password: campus@123

=== Setup Complete! ===
```

### 3️⃣ Test Backend API (30 seconds)

Open browser: `http://localhost/CampusIoop/backend/api/health`

Should see:
```json
{
  "success": true,
  "message": "API is running",
  "data": {
    "status": "OK",
    "timestamp": 1699524000
  }
}
```

✅ **Backend is working!**

### 4️⃣ Start Frontend (2 minutes)

Open **new terminal** in frontend folder:
```bash
cd C:\xampp\htdocs\CampusIoop\frontend

# Install dependencies (first time only)
npm install

# Start development server
npm start
```

Browser will automatically open: `http://localhost:3000`

✅ **Frontend is running!**

### 5️⃣ Initialize Clubs (1 minute)

1. Go to: `http://localhost:3000`
2. Click **Login**
3. Select **Developer** role
4. Enter credentials:
   - Username: `devadmin`
   - Password: `campus@123`
5. Click **Login**

Now use Postman or browser console to initialize clubs:
```javascript
fetch('http://localhost/CampusIoop/backend/api/clubs/initialize', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer ' + localStorage.getItem('token')
  }
})
.then(r => r.json())
.then(console.log)
```

✅ **All Done!**

---

## 🎯 What You Can Do Now

### As Developer
- ✅ View system metrics
- ✅ Manage all users
- ✅ Monitor API health
- ✅ Track bugs

### Create Test Accounts

#### Student Account
1. Logout
2. Click **Sign Up**
3. Select **Student**
4. Fill form:
   - Name: Test Student
   - Roll No: 21311A0501
   - Email: student@test.com
   - Password: test123
   - Department: CSE
   - Year: 3rd Year
   - Section: A
   - DOB: 2003-01-01
   - Gender: Male
5. Select clubs (IEEE, Coding Club, etc.)
6. Click **Sign Up**

#### Faculty Account
1. Logout
2. Click **Sign Up**
3. Select **Faculty**
4. Fill form with faculty details
5. Click **Sign Up**

#### Admin Account
1. Logout
2. Click **Sign Up**
3. Select **Admin**
4. Fill form with admin details
5. Click **Sign Up**

---

## 🔍 Verify Everything Works

### ✅ Backend Checklist
- [ ] Apache running (green in XAMPP)
- [ ] MySQL running (green in XAMPP)
- [ ] Health endpoint responds
- [ ] Database 'campusloop' exists
- [ ] Default clubs created

### ✅ Frontend Checklist
- [ ] React app running on port 3000
- [ ] Landing page loads
- [ ] Login page works
- [ ] Signup page works
- [ ] Can create accounts

---

## 🌐 URLs to Remember

| Service | URL |
|---------|-----|
| Frontend | http://localhost:3000 |
| Backend API | http://localhost/CampusIoop/backend/api |
| Health Check | http://localhost/CampusIoop/backend/api/health |
| phpMyAdmin | http://localhost/phpmyadmin |
| Database | campusloop |

---

## 🔑 Default Credentials

| Role | Username | Password |
|------|----------|----------|
| Developer | devadmin | campus@123 |

---

## 🛠️ Common Issues & Fixes

### ❌ "Cannot connect to backend"
**Fix**: Make sure Apache is running in XAMPP

### ❌ "Database connection failed"
**Fix**: Make sure MySQL is running in XAMPP

### ❌ "404 Not Found" on API calls
**Fix**: 
1. Open `C:\xampp\apache\conf\httpd.conf`
2. Find `LoadModule rewrite_module` and uncomment it
3. Find `AllowOverride None` and change to `AllowOverride All`
4. Restart Apache

### ❌ "Port 3000 already in use"
**Fix**: Kill the process or use different port:
```bash
PORT=3001 npm start
```

### ❌ Frontend shows old API URL
**Fix**: 
1. Stop frontend (Ctrl+C)
2. Clear browser cache
3. Start frontend again: `npm start`

---

## 📱 Test the Application

### Test Login Flow
1. Go to http://localhost:3000
2. Click **Login**
3. Select role: **Developer**
4. Username: `devadmin`
5. Password: `campus@123`
6. Click **Login**
7. Should redirect to Developer Dashboard

### Test Signup Flow
1. Click **Sign Up**
2. Select role: **Student**
3. Fill all required fields
4. Select clubs
5. Click **Sign Up**
6. Should redirect to Student Dashboard

### Test Club Features
1. Login as Student
2. View joined clubs
3. See club events
4. Check DSA challenges

---

## 🎉 Success!

If you can:
- ✅ Login with developer account
- ✅ See the dashboard
- ✅ View clubs list
- ✅ Create new accounts

**You're all set! The application is working perfectly!**

---

## 📚 Next Steps

1. **Explore Features**: Try all 4 role dashboards
2. **Create Test Data**: Add students, faculty, admins
3. **Test Clubs**: Join/leave clubs as student
4. **Customize**: Modify colors, add features
5. **Deploy**: Move to production server

---

## 💡 Pro Tips

- Use **phpMyAdmin** to view database directly
- Check **Apache error logs** if issues occur: `C:\xampp\apache\logs\error.log`
- Use **Browser DevTools** (F12) to debug frontend
- Keep **XAMPP Control Panel** open to monitor services

---

## 📞 Need Help?

1. Check `MIGRATION_GUIDE.md` for detailed info
2. Check `backend/README.md` for API docs
3. Check `SETUP_GUIDE.md` for full setup
4. Check browser console for errors
5. Check Apache error logs

---

**Happy Coding! 🚀**
