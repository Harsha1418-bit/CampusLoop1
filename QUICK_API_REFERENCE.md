# 🚀 Quick API Reference Guide

## 🔐 Authentication
All protected endpoints require JWT token:
```
Authorization: Bearer YOUR_JWT_TOKEN
```

---

## 📚 Student Portal APIs

### **Challenges**
```
GET  /api/challenges/daily          - Get today's challenge
POST /api/challenges/run            - Run code
GET  /api/challenges/submissions    - Get my submissions
```

**Example: Run Code**
```json
POST /api/challenges/run
{
  "challenge_id": 1,
  "code": "def two_sum(nums, target):\n    ...",
  "language": "python",
  "input": "[2,7,11,15]\n9"
}
```

### **Attendance**
```
GET /api/student/attendance - Get attendance with percentage
```

**Response:**
```json
{
  "success": true,
  "data": {
    "subjects": [
      {
        "subject_name": "Data Structures",
        "total_classes": 20,
        "present_count": 18,
        "percentage": 90.00
      }
    ],
    "overall": {
      "total_classes": 60,
      "present_count": 54,
      "percentage": 90.00
    }
  }
}
```

### **Marks**
```
GET /api/student/marks - Get marks and GPA
```

**Response:**
```json
{
  "success": true,
  "data": {
    "marks": [
      {
        "subject_name": "Data Structures",
        "marks_obtained": 85,
        "total_marks": 100,
        "grade": "A",
        "exam_type": "Internal"
      }
    ],
    "gpa": 8.5
  }
}
```

### **Leaderboard**
```
GET /api/leaderboard - Get top students
```

---

## 👩‍🏫 Teacher Portal APIs

### **Upload Marks**
```
POST /api/teacher/marks/upload
```

**Request:**
```json
{
  "marks": [
    {
      "student_id": 1,
      "subject_id": 1,
      "marks_obtained": 85,
      "total_marks": 100,
      "grade": "A",
      "exam_type": "Internal",
      "exam_date": "2024-11-09"
    }
  ]
}
```

### **Mark Attendance**
```
POST /api/teacher/attendance/mark
```

**Request:**
```json
{
  "subject_id": 1,
  "date": "2024-11-09",
  "attendance": [
    {
      "student_id": 1,
      "status": "Present"
    },
    {
      "student_id": 2,
      "status": "Absent"
    }
  ]
}
```

### **Create Test**
```
POST /api/teacher/tests/create
```

**Request:**
```json
{
  "title": "Mid-Term Exam",
  "description": "Data Structures Mid-Term",
  "subject_id": 1,
  "test_date": "2024-11-15",
  "duration": 120,
  "total_marks": 100
}
```

### **Get Reports**
```
GET /api/teacher/reports - Get class performance
```

### **Get Queries**
```
GET /api/teacher/queries              - Get student queries
PUT /api/teacher/queries/:id/accept   - Accept a query
```

---

## 🧑‍💼 Admin Portal APIs

### **Event Approvals**
```
GET /api/admin/events/pending         - Get pending events
GET /api/admin/events/approved        - Get approved events
PUT /api/admin/events/:id/approve     - Approve event
PUT /api/admin/events/:id/revoke      - Revoke approval
```

**Example: Approve Event**
```
PUT /api/admin/events/5/approve
```

### **Analytics**
```
GET /api/admin/analytics - Get complete analytics
```

**Response:**
```json
{
  "success": true,
  "data": {
    "total_students": 500,
    "total_faculty": 50,
    "total_clubs": 15,
    "avg_attendance": 85.5,
    "avg_gpa": 7.8,
    "club_participation": [...],
    "attendance_trends": [...]
  }
}
```

### **Announcements**
```
POST /api/admin/announcements - Create global announcement
```

**Request:**
```json
{
  "title": "Holiday Notice",
  "content": "Campus will be closed on Nov 15th",
  "type": "General",
  "priority": "High"
}
```

### **Reports**
```
GET /api/admin/reports - Get department reports
```

---

## 💬 Chat APIs

### **Get Conversations**
```
GET /api/chat/conversations - Get all conversations
```

### **Get Messages**
```
GET /api/chat/messages?user_id=5 - Get messages with user
```

### **Send Message**
```
POST /api/chat/send
```

**Request:**
```json
{
  "receiver_id": 5,
  "message": "Hello, I have a question about the assignment."
}
```

### **Get Faculty List** (for students)
```
GET /api/chat/faculty - Get list of faculty to chat with
```

---

## 🔔 Notification APIs

### **Get Notifications**
```
GET /api/notifications - Get my notifications
```

### **Mark as Read**
```
PUT /api/notifications/:id/read
```

### **Create Notification** (admin only)
```
POST /api/notifications
```

**Request:**
```json
{
  "title": "New Assignment",
  "message": "Check the portal for new assignment",
  "type": "info",
  "role": "student"
}
```

---

## 🧪 Testing with cURL

### **Get Notifications**
```bash
curl -H "Authorization: Bearer YOUR_TOKEN" \
  http://localhost/CampusIoop/backend/api/notifications
```

### **Get Attendance**
```bash
curl -H "Authorization: Bearer YOUR_TOKEN" \
  http://localhost/CampusIoop/backend/api/student/attendance
```

### **Upload Marks**
```bash
curl -X POST \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"marks":[{"student_id":1,"subject_id":1,"marks_obtained":85,"total_marks":100,"grade":"A"}]}' \
  http://localhost/CampusIoop/backend/api/teacher/marks/upload
```

### **Approve Event**
```bash
curl -X PUT \
  -H "Authorization: Bearer YOUR_TOKEN" \
  http://localhost/CampusIoop/backend/api/admin/events/5/approve
```

---

## 📊 Response Codes

| Code | Meaning |
|------|---------|
| 200 | Success |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Server Error |

---

## 🎯 Quick Start

1. **Run database migration:**
   ```bash
   mysql -u root -p campusloop < backend/database/additional_features.sql
   ```

2. **Restart Apache**

3. **Test health check:**
   ```bash
   curl http://localhost/CampusIoop/backend/api/health
   ```

4. **Login and get token:**
   ```bash
   curl -X POST \
     -H "Content-Type: application/json" \
     -d '{"username":"student1","password":"password","role":"student"}' \
     http://localhost/CampusIoop/backend/api/auth/login
   ```

5. **Use token in subsequent requests:**
   ```bash
   curl -H "Authorization: Bearer YOUR_TOKEN" \
     http://localhost/CampusIoop/backend/api/notifications
   ```

---

## 🔗 Base URL

```
http://localhost/CampusIoop/backend/api
```

---

## ✅ All Endpoints Summary

**Total: 30+ Endpoints**

- ✅ 3 Challenge endpoints
- ✅ 3 Notification endpoints  
- ✅ 3 Student endpoints
- ✅ 6 Teacher endpoints
- ✅ 7 Admin endpoints
- ✅ 4 Chat endpoints
- ✅ Plus all existing Club Portal endpoints

**Backend is fully functional and ready to use!** 🎉
