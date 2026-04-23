# 🚀 ET (Electrical Technology) Smart Learning Platform

**Smart Learning for Future Engineers**

A comprehensive web application for Electrical Technology students at **Faridpur Polytechnic Institute** with real-time features, progress tracking, and interactive learning tools.

---

## 📋 Project Overview

**Developer:** Ridoy Hossen Arif | 7th Semester | Faridpur Polytechnic Institute

**Demo Student Data:**
- **Name:** MD ARIFUL ISLAM
- **Roll:** 747228
- **Registration:** 15022711 56/2223
- **Semester:** 7th

---

## 🎯 Key Features

### ✨ Core Features
- **Smart Dashboard** - Real-time greeting, current class info, daily hadith
- **Subject Management** - Track all 7 subjects with progress bars
- **Quiz System** - Level-based MCQ challenges with leaderboard
- **Real-time Chat** - Student-Teacher direct messaging with Socket.io
- **Progress Tracking** - Quiz marks, attendance, assignments, syllabus progress
- **Resource Center** - Download notes, circuit diagrams, formulas
- **Teacher Directory** - WhatsApp integration for direct contact
- **Dark/Light Theme** - User preference persistence

### 🔐 Security
- JWT-based authentication
- Role-based access control (Student, Teacher, Admin)
- Password hashing with bcryptjs

### 📱 Responsive Design
- Mobile-first approach
- Works on all devices (320px - 4K)
- Smooth animations with Framer Motion
- Glassmorphism UI design

---

## 🛠️ Tech Stack

### Frontend
- **React.js** - UI library
- **Tailwind CSS** - Utility-first CSS framework
- **Framer Motion** - Animations
- **Recharts** - Data visualization
- **Axios** - HTTP client
- **Socket.io-client** - Real-time communication

### Backend
- **Node.js + Express.js** - Server framework
- **MongoDB** - NoSQL database
- **JWT** - Authentication
- **Socket.io** - WebSocket library
- **Multer** - File uploads
- **PDF Parse** - PDF processing

---

## 📁 Project Structure

```
ET_Platform/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   ├── ProtectedRoute.jsx
│   │   │   └── ...
│   │   ├── pages/
│   │   │   ├── LoginPage.jsx
│   │   │   ├── DashboardPage.jsx
│   │   │   ├── SubjectsPage.jsx
│   │   │   ├── QuizPage.jsx
│   │   │   ├── ChatPage.jsx
│   │   │   ├── ResourcesPage.jsx
│   │   │   ├── TeachersPage.jsx
│   │   │   ├── ProfilePage.jsx
│   │   │   └── AdminPanel.jsx
│   │   ├── context/
│   │   │   ├── authStore.js
│   │   │   ├── themeStore.js
│   │   │   └── dataStore.js
│   │   ├── hooks/
│   │   │   ├── useAuth.js
│   │   │   ├── useSocket.js
│   │   │   └── useAPI.js
│   │   ├── utils/
│   │   │   ├── api.js
│   │   │   ├── validators.js
│   │   │   └── helpers.js
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   ├── tailwind.config.js
│   ├── vite.config.js
│   └── index.html
│
├── backend/
│   ├── models/
│   │   ├── User.js
│   │   ├── Subject.js
│   │   ├── Progress.js
│   │   ├── Message.js
│   │   └── Notification.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── userController.js
│   │   ├── progressController.js
│   │   ├── messageController.js
│   │   └── notificationController.js
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── userRoutes.js
│   │   ├── progressRoutes.js
│   │   ├── messageRoutes.js
│   │   └── notificationRoutes.js
│   ├── middleware/
│   │   ├── auth.js
│   │   ├── errorHandler.js
│   │   └── validation.js
│   ├── services/
│   │   ├── mailService.js
│   │   ├── pdfService.js
│   │   └── uploadService.js
│   ├── server.js
│   ├── package.json
│   └── .env.example
│
├── README.md
├── SETUP.md
├── API_DOCUMENTATION.md
└── .gitignore
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js v14+ and npm
- MongoDB (local or Atlas)
- Git

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Runs on `http://localhost:3000`

### Backend Setup

```bash
cd backend
npm install

# Create .env file
cp .env.example .env

# Update .env with your configuration
# MONGODB_URI=mongodb://localhost:27017/et-platform
# JWT_SECRET=your_secret_key

npm run dev
```

Runs on `http://localhost:5000`

---

## 📝 Login Credentials (Demo)

**Student Account:**
- Board Roll: `747228`
- Registration: `15022711 56/2223`
- Password: Set during registration

---

## 📚 Subjects (7th Semester)

| Code  | Name | Credit | Teacher |
|-------|------|--------|---------|
| 25831 | Business Communication | 2 | Sohel Molla |
| 25853 | Innovation & Entrepreneurship | 2 | Nafida Akter |
| 26771 | AC Machine-II | 3 | Md. Monirul Hosen |
| 26772 | T & D of Electrical Power-II | 3 | Tawhida Rahman |
| 26773 | Switch Gear and Protection | 3 | Rasihul Islam |
| 26774 | Electrical Project-III | 6 | Razzak Karim |
| 26875 | Automation & PLC | 3 | Tawhidur Rahma |

---

## 🔌 API Endpoints

### Authentication
```
POST   /api/auth/register       - Register new user
POST   /api/auth/login          - Login user
GET    /api/auth/me             - Get current user
POST   /api/auth/logout         - Logout
```

### Users
```
GET    /api/users/profile       - Get user profile
PUT    /api/users/profile       - Update profile
GET    /api/users/all           - Get all users (admin)
GET    /api/users/teachers      - Get all teachers
GET    /api/users/students      - Get all students
DELETE /api/users/:id           - Delete user (admin)
```

### Progress
```
GET    /api/progress/student             - Get student progress
GET    /api/progress/subject/:subjectId  - Get subject progress
PUT    /api/progress/update              - Update progress
GET    /api/progress/class/:subjectId    - Get class progress
```

---

## 🎨 UI Components

### Color Scheme
- **Primary:** #0ea5e9 (Sky Blue)
- **Secondary:** #a855f7 (Purple)
- **Success:** #10b981 (Green)
- **Warning:** #f59e0b (Amber)
- **Danger:** #ef4444 (Red)

### Design System
- Glassmorphism with backdrop blur
- Smooth transitions (300ms)
- Shadow hierarchy
- Responsive grid system
- Loading skeletons

---

## 🔐 Authentication Flow

1. Student enters **Board Roll** and **Registration Number**
2. System validates against database
3. JWT token generated and stored in localStorage
4. Token sent with each API request in Authorization header
5. Backend validates token middleware
6. Role-based access control applied

---

## 🗄️ Database Schema

### Users Collection
```javascript
{
  _id: ObjectId,
  name: String,
  email: String,
  phone: String,
  roll: String (unique),
  registration: String (unique),
  password: String (hashed),
  role: String (student/teacher/admin),
  semester: Number,
  shift: Number,
  department: String,
  profilePhoto: String,
  gpa: Number,
  batch: String,
  isActive: Boolean,
  createdAt: Date,
  updatedAt: Date
}
```

### Progress Collection
```javascript
{
  _id: ObjectId,
  student: ObjectId (ref: User),
  subject: ObjectId (ref: Subject),
  quizMarks: [{
    attempt: Number,
    marks: Number,
    date: Date
  }],
  assignmentStatus: String,
  attendancePercentage: Number,
  midSyllabusProgress: Number,
  totalMarks: Number,
  lastUpdated: Date,
  createdAt: Date,
  updatedAt: Date
}
```

---

## 🚀 Deployment

### Frontend (Netlify/Vercel)
```bash
npm run build
# Deploy dist folder
```

### Backend (Heroku/Railway)
```bash
git push heroku main
# Or use Railway/Render deployment
```

---

## 📦 Features Roadmap

- [ ] Video lecture integration (YouTube)
- [ ] PDF notes download with progress tracking
- [ ] AI-powered learning assistant
- [ ] Notification system (email/push)
- [ ] Mobile app (React Native)
- [ ] Offline mode (PWA)
- [ ] Advanced analytics dashboard
- [ ] Plagiarism detection for assignments
- [ ] Certificate generation
- [ ] Payment integration for premium features

---

## 🤝 Contributing

This is an educational project. Contributions are welcome!

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 👨‍💼 Developer Information

**Ridoy Hossen Arif**
- 7th Semester, Electrical Technology
- Faridpur Polytechnic Institute, Bangladesh
- Email: ridoy.hossen@poly.edu.bd
- Phone: +880 1XXX XXXXXX

---

## 🙏 Acknowledgments

- Faridpur Polytechnic Institute
- Electrical Technology Department
- All teachers and students for inspiration
- Open-source community

---

## 📧 Support

For support, email `support@etplatform.com` or open an issue on GitHub.

---

**Made with ❤️ by Ridoy Hossen Arif**

*Last Updated: 2024*
