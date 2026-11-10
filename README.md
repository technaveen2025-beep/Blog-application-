# MongoDB database files for Blog Application

This folder contains the MongoDB connection and Mongoose models for a Node.js/Express blog project.

## Files
- `config/db.js` — connects your Express backend to MongoDB.
- `models/User.js` — user schema.
- `models/Blog.js` — blog post schema; each blog references its author.
- `.env.example` — environment variable template. Copy it to `.env` locally and add your real values.
- `.gitignore` — prevents secrets and dependencies from being committed.

## Install
From your backend folder, run:

```bash
npm install mongoose dotenv
```

If your login/registration routes use password hashing and JWT authentication, also install:

```bash
npm install bcryptjs jsonwebtoken
```

## Configure
1. Create a MongoDB Atlas cluster and database user.
2. Copy `.env.example` to `.env` in your backend folder.
3. Replace the `MONGO_URI` placeholder with your Atlas connection string.
4. Replace `JWT_SECRET` with a long random secret.
5. Keep `.env` private. Do not upload it to GitHub.

## Connect in server.js
At the top of your server file:

```javascript
require("dotenv").config();
const connectDB = require("./config/db");
```

Before accepting requests, connect to the database:

```javascript
connectDB().catch((error) => {
  console.error("Database connection failed:", error.message);
  process.exit(1);
});
```

Keep your existing Express routes and middleware. Adjust import paths if you place these files in a different folder.

## Important
These are database connection and schema files, not a database backup or a complete application. MongoDB Atlas stores the actual records online. Add these files to your existing backend, connect your existing API routes to the models, and test registration, login, blog creation, blog listing, and blog details before submitting.
