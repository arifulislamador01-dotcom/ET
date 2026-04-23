# 🛠️ ET Platform - Setup & Installation Guide

**Complete step-by-step guide to set up and run ET Smart Learning Platform**

---

## 📋 System Requirements

### Minimum Requirements
- **OS:** Windows 10, macOS 10.15+, or Ubuntu 20.04+
- **RAM:** 4GB minimum, 8GB recommended
- **Storage:** 2GB free space
- **Internet:** Required for initial setup

### Required Software
- **Node.js:** v14.0.0 or higher
- **npm:** v6.0.0 or higher
- **MongoDB:** v4.4 or higher
- **Git:** Latest version
- **Code Editor:** VS Code, WebStorm, or similar

---

## 🚀 Step-by-Step Installation

### Step 1: Prerequisites Installation

#### Windows
```bash
# Download and install Node.js from https://nodejs.org/
# Download and install MongoDB from https://www.mongodb.com/try/download/community
# Download and install Git from https://git-scm.com/download/win
```

#### macOS
```bash
# Using Homebrew
brew install node
brew install mongodb-community
brew install git
```

#### Ubuntu/Linux
```bash
# Node.js
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# MongoDB
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
sudo apt-get install -y mongodb-org
```

### Step 2: Verify Installation

```bash
# Check Node version
node --version
# Should output v14.0.0 or higher

# Check npm version
npm --version
# Should output v6.0.0 or higher

# Check MongoDB
mongod --version
# Should output version information
```

### Step 3: Clone Repository

```bash
# Clone the project
git clone https://github.com/yourusername/et-platform.git
cd ET_Platform

# List files
ls -la
```

### Step 4: Backend Setup

```bash
# Navigate to backend
cd backend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Edit .env file with your configuration
# Windows: notepad .env
# macOS/Linux: nano .env
```

**Update .env file:**
```env
PORT=5000
NODE_ENV=development
MONGODB_URI=mongodb://localhost:27017/et-platform
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
JWT_EXPIRE=7d
MAX_FILE_SIZE=52428800
APP_NAME=ET Platform
APP_URL=http://localhost:3000
```

### Step 5: Start MongoDB

**Windows:**
```bash
# MongoDB should auto-start on Windows
# Or manually start:
mongod
```

**macOS:**
```bash
# Using Homebrew
brew services start mongodb-community
```

**Linux:**
```bash
# Start MongoDB service
sudo systemctl start mongod
```

### Step 6: Start Backend Server

```bash
# From backend directory
npm run dev
# Or for production: npm start

# Expected output:
# ╔════════════════════════════════════════╗
# ║   ET SMART LEARNING PLATFORM - LIVE    ║
# ║          Server Running on Port 5000    ║
# ╚════════════════════════════════════════╝
```

### Step 7: Frontend Setup (New Terminal)

```bash
# Navigate to frontend
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev

# Expected output:
# ➜  Local:   http://localhost:3000/
# ➜  press h to show help
```

### Step 8: Access Application

Open your browser and navigate to:
```
http://localhost:3000
```

---

## 🔑 First Time Login

**Demo Account Credentials:**
- **Board Roll:** 747228
- **Registration:** 15022711 56/2223
- **Password:** Create your own during registration

---

## ⚙️ Configuration Options

### Backend (.env)

| Variable | Description | Example |
|----------|-------------|---------|
| PORT | Server port | 5000 |
| NODE_ENV | Environment | development/production |
| MONGODB_URI | MongoDB connection | mongodb://localhost:27017/et-platform |
| JWT_SECRET | JWT signing key | your_secret_key |
| JWT_EXPIRE | Token expiration | 7d |
| APP_URL | Frontend URL | http://localhost:3000 |

### Frontend (.env) - Optional

Create `frontend/.env` if needed:
```env
VITE_API_URL=http://localhost:5000/api
VITE_SOCKET_URL=http://localhost:5000
```

---

## 📊 Database Initialization

### Create Admin User

Connect to MongoDB:
```bash
mongosh
```

```javascript
use et-platform

db.users.insertOne({
  name: "Admin User",
  email: "admin@etplatform.com",
  roll: "00001",
  registration: "ADMIN001",
  password: "$2a$10$...", // bcrypt hash of your password
  role: "admin",
  semester: 7,
  department: "Electrical Technology",
  isActive: true,
  createdAt: new Date(),
  updatedAt: new Date()
})
```

### Seed Sample Data

```bash
# Create seed.js in backend directory with sample data
node seed.js
```

---

## 🐛 Troubleshooting

### Issue: MongoDB Connection Error
```
Error: connect ECONNREFUSED 127.0.0.1:27017
```

**Solution:**
```bash
# Check if MongoDB is running
mongosh  # Should connect successfully

# Restart MongoDB
# Windows: net start MongoDB
# macOS: brew services restart mongodb-community
# Linux: sudo systemctl restart mongod
```

### Issue: Port Already in Use
```
Error: listen EADDRINUSE :::5000
```

**Solution:**
```bash
# Kill the process using the port
# Windows: netstat -ano | findstr :5000
# macOS/Linux: lsof -i :5000
# Kill process: kill -9 <PID>

# Or use different port in .env
PORT=5001
```

### Issue: Module Not Found
```
Error: Cannot find module 'express'
```

**Solution:**
```bash
# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
```

### Issue: CORS Error
```
Access to XMLHttpRequest blocked by CORS policy
```

**Solution:**
```
1. Update APP_URL in backend .env to match frontend URL
2. Ensure CORS is enabled in server.js
3. Check that axios requests include proper headers
```

### Issue: JWT Verification Failed
```
Error: jwt malformed
```

**Solution:**
```
1. Check token is being sent correctly (Bearer token)
2. Verify JWT_SECRET in .env matches
3. Check token expiration time
```

---

## 📝 Build for Production

### Frontend Build

```bash
cd frontend
npm run build
# Creates optimized dist/ folder
# Upload dist/ contents to hosting service
```

### Backend Deployment

```bash
# Using Heroku
heroku login
heroku create et-platform
git push heroku main

# Using Railway
railway login
railway init
railway up
```

---

## 🔒 Security Checklist

- [ ] Change JWT_SECRET in production
- [ ] Use strong MongoDB password
- [ ] Enable HTTPS in production
- [ ] Set secure CORS origins
- [ ] Use environment variables for sensitive data
- [ ] Enable rate limiting
- [ ] Add request validation
- [ ] Implement CSRF protection
- [ ] Regular security updates
- [ ] Monitor API logs

---

## 📚 Additional Resources

### Documentation
- [Node.js Docs](https://nodejs.org/docs/)
- [MongoDB Manual](https://docs.mongodb.com/manual/)
- [Express.js Guide](https://expressjs.com/)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)

### Video Tutorials
- [MERN Stack Tutorial](https://www.youtube.com/results?search_query=mern+stack)
- [MongoDB Tutorial](https://www.youtube.com/results?search_query=mongodb)
- [Tailwind CSS](https://www.youtube.com/results?search_query=tailwind+css)

### Community
- [Stack Overflow](https://stackoverflow.com/)
- [GitHub Discussions](https://github.com/discussions)
- [MongoDB Community](https://community.mongodb.com/)

---

## ✅ Verification Checklist

After installation, verify:

- [ ] Node.js installed (`node --version`)
- [ ] npm installed (`npm --version`)
- [ ] MongoDB running (`mongosh`)
- [ ] Backend running on http://localhost:5000
- [ ] Frontend running on http://localhost:3000
- [ ] Can access API endpoints
- [ ] Can login with demo credentials
- [ ] Database connection working
- [ ] No console errors

---

## 🆘 Need Help?

1. **Check console errors** - Look at browser console and terminal
2. **Review .env file** - Ensure all variables are set correctly
3. **Restart services** - Kill and restart Node.js and MongoDB
4. **Clear cache** - Delete node_modules and reinstall
5. **Check ports** - Ensure ports 3000 and 5000 are available

---

**Last Updated:** 2024
**Version:** 1.0.0
