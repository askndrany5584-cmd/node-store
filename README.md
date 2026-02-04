# Smart S3r - Monorepo

Full-stack e-commerce application with React frontend and Express backend.

## 🚀 Quick Start

```bash
# Install dependencies (from root)
npm install

# Start both frontend and backend
npm run dev
```

This will start:
- **Backend**: http://localhost:3000
- **Frontend**: http://localhost:5173

## 📁 Project Structure

```
smarts3r/
├── apps/
│   ├── frontend/          # React + Vite + TypeScript
│   └── backend/           # Express + Prisma + Supabase
├── packages/
│   └── types/             # Shared TypeScript types
├── package.json           # Root workspace config
└── README.md
```

## 🔧 Available Scripts

### Root Level (runs both)
```bash
npm run dev              # Start frontend + backend simultaneously
npm run build            # Build both for production
npm run install:all      # Install all dependencies
```

### Backend Only
```bash
npm run dev:backend      # Start backend dev server
npm run build:backend    # Build backend
npm start              # Start production server
```

### Frontend Only
```bash
npm run dev:frontend     # Start frontend dev server
npm run build:frontend   # Build frontend
```

### Database (Backend)
```bash
npm run prisma:generate  # Generate Prisma client
npm run prisma:push      # Push schema to database
npm run prisma:studio    # Open Prisma Studio
npm run setup-db         # Setup database
```

## 🗄️ Database

This project uses **Supabase** (PostgreSQL).

1. Set up your `.env` file in `apps/backend/`:
```env
DATABASE_URL="postgresql://postgres:[password]@[host]:[port]/postgres"
JWT_SECRET="your-secret-key"
CLOUDINARY_CLOUD_NAME=""
CLOUDINARY_API_KEY=""
CLOUDINARY_API_SECRET=""
```

2. Run database setup:
```bash
npm run setup-db
```

## 🚀 Deployment

### Vercel (Recommended)

The project is configured for Vercel deployment:

1. **Frontend**: Connect your repo to Vercel, it will auto-detect the Vite app
2. **Backend**: Deploy as serverless functions (already configured in `vercel.json`)

Both can be deployed from the same monorepo using Vercel's monorepo support.

### Environment Variables for Production

Set these in your Vercel dashboard:
- `DATABASE_URL` - Supabase connection string
- `JWT_SECRET` - Secret for JWT tokens
- `CLOUDINARY_*` - Cloudinary credentials (if using image uploads)

## 🛠️ Tech Stack

**Frontend:**
- React 19
- TypeScript
- Vite
- Tailwind CSS
- Zustand (state management)
- React Router
- Axios

**Backend:**
- Express.js
- TypeScript
- Prisma ORM
- Supabase (PostgreSQL)
- JWT Authentication
- Cloudinary (image uploads)

## 📝 Notes

- This is an **npm workspaces** monorepo (not NX)
- Shared types are in `packages/types/` - import with `@smarts3r/types`
- Backend uses `tsx` for development (hot reload)
- Frontend uses Vite for fast HMR

## 🐛 Troubleshooting

**Port conflicts?**
Make sure ports 3000 (backend) and 5173 (frontend) are available.

**Database connection issues?**
Check your `DATABASE_URL` in `apps/backend/.env`

**Frontend can't connect to backend?**
- Local dev: Frontend proxies to backend automatically
- Production: Set `VITE_API_URL` environment variable
