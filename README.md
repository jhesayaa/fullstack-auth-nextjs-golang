# 🔐 Full-Stack Authentication - Next.js + Golang

Complete authentication system with **Next.js 14** frontend and **Golang API** backend featuring JWT authentication, built with modern tech stack.

## ✨ Features

### Frontend (Next.js)
- 🎨 **Modern UI** - Clean and responsive design with Tailwind CSS
- 🔒 **Login & Register** - Complete authentication flow
- 🛡️ **Protected Routes** - Auto redirect for authenticated users
- 💾 **Token Management** - Secure localStorage handling
- ⚡ **API Client** - Axios with interceptors
- 🔄 **Error Handling** - User-friendly error messages
- 📱 **Responsive Design** - Works on all devices

### Backend (Golang)
- 🔐 **JWT Authentication** - Secure token-based auth
- 🔒 **Password Hashing** - Bcrypt for security
- 📊 **PostgreSQL** - Reliable database with GORM
- ⚡ **Gin Framework** - Fast HTTP server
- 🌐 **CORS Support** - Ready for production
- ✅ **Input Validation** - Request validation

## 🛠️ Tech Stack

### Frontend
- **Next.js 14** - React framework with App Router
- **TypeScript** - Type safety
- **Tailwind CSS** - Styling
- **Axios** - HTTP client

### Backend
- **Go 1.21+** - Backend language
- **Gin** - Web framework
- **GORM** - ORM
- **PostgreSQL** - Database
- **JWT** - Authentication
- **Bcrypt** - Password hashing

## 📁 Project Structure

```
.
├── backend/                 # Golang API
│   ├── cmd/
│   │   ├── migrate/
│   │   │   └── main.go     # Database migration
│   │   └── server/
│   │       └── main.go     # Server entry point
│   ├── internal/
│   │   ├── database/       # Database connection
│   │   ├── handlers/       # HTTP handlers
│   │   ├── middleware/     # JWT middleware
│   │   └── models/         # Data models
│   └── pkg/
│       └── utils/          # Utilities (JWT, password)
│
└── frontend/               # Next.js Frontend
    ├── app/
    │   ├── (auth)/
    │   │   ├── login/      # Login page
    │   │   └── register/   # Register page
    │   └── page.tsx        # Home (redirects to login)
    └── lib/
        ├── api.ts          # Axios client
        └── auth.service.ts # Auth service
```

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- Go 1.21+
- PostgreSQL 14+

### Backend Setup

1. **Navigate to backend**
```bash
cd backend
```

2. **Install dependencies**
```bash
go mod download
```

3. **Setup environment variables**
```bash
cp .env.example .env
```

Edit `.env`:
```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=your_password
DB_NAME=auth_db
DB_SSLMODE=disable

PORT=8080
JWT_SECRET=your-secret-key-change-in-production
```

4. **Create database**
```bash
createdb auth_db
```

5. **Run migrations**
```bash
go run cmd/migrate/main.go
```

6. **Start backend server**
```bash
go run cmd/server/main.go
```

Backend runs on `http://localhost:8080`

### Frontend Setup

1. **Navigate to frontend**
```bash
cd frontend
```

2. **Install dependencies**
```bash
npm install
```

3. **Setup environment variables**
```bash
cp .env.example .env.local
```

Edit `.env.local`:
```env
NEXT_PUBLIC_API_URL=http://localhost:8080/api
```

4. **Start frontend**
```bash
npm run dev
```

Frontend runs on `http://localhost:3000`

## 📚 API Endpoints

### Authentication

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login user |
| GET | `/api/me` | Get current user (protected) |

### Example Requests

**Register:**
```bash
curl -X POST http://localhost:8080/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123"
  }'
```

**Login:**
```bash
curl -X POST http://localhost:8080/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "john@example.com",
    "password": "password123"
  }'
```

**Get Current User:**
```bash
curl http://localhost:8080/api/me \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

## 🔒 Authentication Flow

1. **User registers** → Backend creates user with hashed password
2. **Backend returns** → User data + JWT token
3. **Frontend stores** → Token in localStorage
4. **Subsequent requests** → Include `Authorization: Bearer <token>` header
5. **Backend validates** → JWT token on protected routes
6. **Token expires** → User redirected to login

## 🎨 Screenshots

### Login Page
Clean and modern login interface with form validation.

### Register Page
Simple registration with password confirmation and validation.

## 🛡️ Security Features

- ✅ Password hashing with bcrypt (cost 10)
- ✅ JWT tokens with 24-hour expiration
- ✅ Protected routes with middleware
- ✅ Input validation on backend and frontend
- ✅ CORS configuration
- ✅ Secure token storage (localStorage)
- ✅ Auto logout on token expiration

## 🧪 Testing

### Backend
Test with Thunder Client, Postman, or curl:

```bash
# Register
POST http://localhost:8080/api/auth/register

# Login
POST http://localhost:8080/api/auth/login

# Get user (with token)
GET http://localhost:8080/api/me
```

### Frontend
1. Open `http://localhost:3000`
2. Click "Sign up" to register
3. Login with your credentials
4. Check browser DevTools → Application → Local Storage for token

## 📝 Environment Variables

### Backend (.env)
```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=your_password
DB_NAME=auth_db
DB_SSLMODE=disable
PORT=8080
JWT_SECRET=change-this-in-production
```

### Frontend (.env.local)
```env
NEXT_PUBLIC_API_URL=http://localhost:8080/api
```

## 🚀 Deployment

### Backend
- Can be deployed to any Go-compatible platform (Heroku, Railway, Fly.io)
- Make sure to set environment variables
- Use production database

### Frontend
- Deploy to Vercel (recommended for Next.js)
- Update `NEXT_PUBLIC_API_URL` to production backend URL

## 📄 License

MIT License - feel free to use for learning or projects.

## 👤 Author

**Jeje**
- GitHub: [@jhesayaa](https://github.com/jhesayaa)
- Location: Semarang, Indonesia

## 🙏 Acknowledgments

- Built with [Next.js](https://nextjs.org/)
- Backend with [Gin](https://github.com/gin-gonic/gin)
- ORM with [GORM](https://gorm.io/)
- JWT with [golang-jwt](https://github.com/golang-jwt/jwt)

---

⭐ **Star this repo** if you find it helpful for learning!

## 📖 Learn More

This project demonstrates:
- Full-stack application architecture
- JWT authentication implementation
- API design and best practices
- Modern frontend patterns with Next.js
- Clean code structure and organization
- Type-safe development with TypeScript

Perfect for learning or as a starter template for your next project!
