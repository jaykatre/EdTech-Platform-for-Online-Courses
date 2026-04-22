# Study-Notion

A full-stack EdTech platform where instructors create and sell courses, and students browse, enroll, and learn — built with the MERN stack.

---

## Features

### Students
- Browse and filter courses by category
- Add courses to cart and purchase via Razorpay
- Track progress through video lectures
- Rate and review enrolled courses

### Instructors
- Multi-step course builder (details → sections/videos → publish)
- Upload video content to Cloudinary
- Dashboard with course statistics and enrollments
- Edit or delete courses at any time

### Admin
- Create and manage course categories

### General
- Email OTP verification on signup
- JWT-based authentication
- Password reset via email
- Role-based access control (Student / Instructor / Admin)

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 18, Redux Toolkit, React Router 6, Tailwind CSS |
| Backend | Node.js, Express 4 |
| Database | MongoDB (Mongoose) |
| Auth | JWT, bcryptjs |
| Media Storage | Cloudinary |
| Payments | Razorpay |
| Email | Nodemailer (Gmail SMTP) |

---

## Project Structure

```
Study-Notion/
├── src/                      # React frontend
│   ├── pages/                # Route-level page components
│   ├── components/           # Reusable UI components
│   │   ├── common/           # Navbar, Footer, modals
│   │   └── core/             # Feature-specific components
│   ├── slices/               # Redux state slices
│   ├── services/             # Axios API calls
│   └── utils/                # Constants and helpers
│
└── server/                   # Express backend
    ├── config/               # DB, Cloudinary, Razorpay setup
    ├── models/               # Mongoose schemas
    ├── controllers/          # Business logic
    ├── routes/               # API route definitions
    ├── middlewares/          # JWT auth, role guards
    ├── mail/templates/       # Email HTML templates
    └── utils/                # Mail sender and helpers
```

---

## Getting Started

### Prerequisites

- Node.js v14+
- MongoDB Atlas account
- Cloudinary account
- Razorpay account
- Gmail account (with App Password enabled)

### 1. Clone the repository

```bash
git clone https://github.com/your-username/Study-Notion.git
cd Study-Notion
```

### 2. Configure environment variables

**Frontend — `.env`**
```env
REACT_APP_BASE_URL=http://localhost:4000/api/v1
```

**Backend — `server/.env`**
```env
PORT=4000
MONGODB_URL=mongodb+srv://<username>:<password>@cluster.mongodb.net/StudyNotionDB

# Cloudinary
CLOUD_NAME=your_cloud_name
API_KEY=your_api_key
API_SECRET=your_api_secret
FOLDER_NAME=StudyNotion

# JWT
JWT_SECRET=your_jwt_secret

# Email
MAIL_HOST=smtp.gmail.com
MAIL_USER=your_gmail@gmail.com
MAIL_PASS=your_gmail_app_password

# Razorpay
RAZORPAY_KEY=your_razorpay_key
RAZORPAY_SECRET=your_razorpay_secret
```

### 3. Install dependencies

```bash
# Frontend
npm install

# Backend
cd server && npm install
```

### 4. Run the application

```bash
# From the project root — runs both frontend and backend concurrently
npm run dev
```

Or run them separately:

```bash
# Terminal 1 — Frontend (port 3000)
npm start

# Terminal 2 — Backend (port 4000)
cd server && npm run dev
```

---

## API Overview

```
/api/v1/auth       — Signup, login, OTP, password reset
/api/v1/profile    — Get/update/delete user profile
/api/v1/course     — Course CRUD, sections, subsections, ratings, categories
/api/v1/payment    — Razorpay capture, verify, enrollment email
```

---

## Database Models

| Model | Purpose |
|---|---|
| User | Account info, enrolled courses |
| Profile | Extended user details |
| Course | Course metadata, pricing, status |
| Section | Course chapters |
| SubSection | Individual video lessons |
| Category | Course categories |
| RatingAndReviews | Student course reviews |
| CourseProgress | Per-student completion tracking |
| OTP | Time-limited email verification codes |

---

## Deployment

1. Deploy the backend to Railway, Render, or AWS
2. Deploy the frontend to Vercel or Netlify
3. Update `REACT_APP_BASE_URL` in the frontend `.env` to your backend's production URL
4. Update the CORS `origin` in `server/index.js` to your frontend's production domain
5. Ensure all secrets are stored as environment variables — never commit `.env` files

---

## License

MIT
