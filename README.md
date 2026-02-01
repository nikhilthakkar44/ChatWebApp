# ChatWebApp - Real-Time Chat Application

A full-stack chat application built with Node.js/Express backend and React frontend, featuring real-time messaging, user authentication, and chat management.

## 📋 Project Structure

```
ChatWebApp/
├── backend/
│   ├── config/
│   │   ├── db.js                 # MongoDB connection
│   │   └── generateToken.js      # JWT token generation
│   ├── controllers/
│   │   ├── userControllers.js    # User auth logic
│   │   ├── chatControllers.js    # Chat management
│   │   └── messageControllers.js # Message handling
│   ├── models/
│   │   ├── userModel.js
│   │   ├── chatModel.js
│   │   └── messageModel.js
│   ├── routes/
│   │   ├── userRoutes.js
│   │   ├── chatRoutes.js
│   │   └── messageRoutes.js
│   ├── middleware/
│   │   ├── authMiddleware.js
│   │   └── errorMiddleware.js
│   └── server.js                 # Main server file
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── Pages/
│   │   ├── Context/
│   │   ├── config/
│   │   └── App.js
│   └── package.json
├── .env                          # Environment variables
├── .gitignore
└── package.json
```

## 🚀 Prerequisites

- **Node.js** (v14 or higher)
- **npm** (v6 or higher)
- **Git Bash** (for Windows users)
- **MongoDB URI** (from MongoDB Atlas)
- **Cloudinary Account** (for image uploads)

## 📦 Installation & Setup

### 1. Clone Repository
```bash
git clone https://github.com/nikhilthakkar44/ChatWebApp.git
cd ChatWebApp/ChatText
```

### 2. Setup Environment Variables

Create a `.env` file in the root `ChatText` directory with:

```env
JWT_SECRET=your_jwt_secret_key_here
MONGO_URI=mongodb+srv://username:password@cluster0.xxxxx.mongodb.net/?appName=Cluster0
```

**Note:** The `.env` file must be in `ChatText/` directory (where `server.js` is located), not in the root workspace.

### 3. Backend Setup

Navigate to the root directory and install dependencies:

```bash
cd ChatText
npm ci
```

Run backend server:

```bash
npm run start
```

Backend will run on `http://localhost:5000`

### 4. Frontend Setup

In a new terminal, navigate to frontend:

```bash
cd ChatText/frontend
```

Clean install (if first time or having issues):

```bash
rm -rf node_modules package-lock.json
npm cache clean --force
```

Install dependencies with legacy peer deps flag:

```bash
npm install --legacy-peer-deps
```

Run frontend development server:

```bash
npm start
```

Frontend will run on `http://localhost:3000`

---

## 🔧 Troubleshooting

### Frontend Build Issues

If you encounter module errors, try these steps in order:

**Clear cache and reinstall:**
```bash
rm -rf node_modules package-lock.json
npm cache clean --force
npm install --legacy-peer-deps
```

**React Scripts compatibility issue:**
```bash
npm install react-scripts@5.0.1 --save --legacy-peer-deps
npm install ajv@6.12.6 ajv-keywords@3.5.2 --save-dev --legacy-peer-deps
npm install --legacy-peer-deps
```

**Chakra UI components:**
```bash
npm install @chakra-ui/react@2.8.2 @emotion/react @emotion/styled framer-motion --legacy-peer-deps
npm install @chakra-ui/layout @chakra-ui/skeleton @chakra-ui/toast @chakra-ui/button @chakra-ui/avatar @chakra-ui/menu @chakra-ui/tooltip --legacy-peer-deps
```

### PowerShell Execution Policy (Windows)

If npm commands fail in PowerShell with execution policy error:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Then use **Git Bash** instead:
```bash
# Use Git Bash terminal for all npm commands
```

### MongoDB Connection Error

If you see: `Error: The 'uri' parameter to 'openUri()' must be a string, got "undefined"`

- Ensure `.env` file is in the `ChatText/` root directory
- Verify `MONGO_URI` is set correctly
- Restart the backend server

### 401 Unauthorized API Error

- Clear browser localStorage: `localStorage.clear()`
- Log in again to get a fresh token
- Ensure `JWT_SECRET` matches in `.env`

---

## 🎯 Running Both Backend & Frontend

### Terminal 1 - Backend:
```bash
cd ChatText
npm run start
```

### Terminal 2 - Frontend:
```bash
cd ChatText/frontend
npm start
```

Both servers should now be running:
- Backend API: `http://localhost:5000`
- Frontend App: `http://localhost:3000`

---

## 🗄️ Database Setup

1. Create MongoDB Atlas cluster at [mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
2. Get connection string
3. Add to `.env` as `MONGO_URI`
4. Database will auto-create collections on first connection

---

## 🖼️ Image Upload (Cloudinary)

Image upload is configured for Cloudinary:
- **Cloud Name:** `dzoajkwqu`
- **Upload Preset:** `chatify`

Configure in: `frontend/src/components/Authentication/Signup.js`

---

## 📝 Key Features

✅ User Registration & Login (JWT Authentication)  
✅ Create & Delete Chats  
✅ Real-Time Messaging  
✅ Group Chat Management  
✅ User Search & Discovery  
✅ Notification Badge  
✅ Profile Management  

---

## 📧 API Endpoints

### Users
- `POST /api/user` - Register
- `POST /api/user/login` - Login
- `GET /api/user?search=query` - Search users

### Chats
- `GET /api/chat` - Get all chats
- `POST /api/chat` - Create chat
- `PUT /api/chat/rename` - Rename group

### Messages
- `GET /api/message/:chatId` - Get messages
- `POST /api/message` - Send message

---

## 🐛 Git Ignore

Sensitive files are excluded via `.gitignore`:
- `node_modules/`
- `.env` files
- `cred.txt`
- Build artifacts
- IDE settings

---

## 📦 Dependencies

### Backend
- express
- mongoose
- dotenv
- axios
- bcryptjs

### Frontend
- react
- axios
- @chakra-ui/react
- react-router-dom

---

## 🔐 Security Notes

⚠️ **Never commit:**
- `.env` files
- `cred.txt`
- API keys or secrets
- JWT secrets

---

## 🚢 Deployment (Production)

Before pushing to production:

1. Set secure environment variables on hosting platform
2. Use production MongoDB URI
3. Disable debug logging
4. Set `NODE_ENV=production`
5. Build frontend: `npm run build`
6. Use PM2 or similar for backend process management

```bash
# Production build
cd frontend
npm run build
# Serves static files from build/ directory
```

---

## 📞 Support

For issues:
1. Check `.env` configuration
2. Verify MongoDB connection
3. Clear browser cache and localStorage
4. Check console for specific error messages
5. Review troubleshooting section above

---

## 📄 License

This project is part of ChatWebApp development.

---

**Last Updated:** February 1, 2026
