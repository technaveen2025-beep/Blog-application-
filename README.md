# Authentication & Dashboard

This is an integration package for a Blog Application using Node.js, Express, MongoDB, and JWT.

## Features
- User registration with hashed passwords (bcryptjs)
- User login and JWT token generation
- Protected dashboard API routes
- User profile display
- Display only the logged-in user's blogs
- Logout by clearing the saved token

## 1. Install backend packages

From your existing backend folder:

```bash
npm install express mongoose bcryptjs jsonwebtoken dotenv
```

If your frontend and backend run on different origins, configure CORS in your existing server:

```bash
npm install cors
```

Then in `server.js`:

```js
const cors = require("cors");
app.use(cors());
app.use(express.json());
```

## 2. Expected existing MongoDB models

This package expects `backend/models/User.js` to export a Mongoose model with:
- `name` (String)
- `email` (String, unique)
- `password` (String)

It expects `backend/models/Blog.js` to export a model with:
- `title` (String)
- `content` (or `description`)
- `author` (ObjectId referencing the User model)

If your existing model uses different field names, update the route code to match it. Your blog creation route must save the logged-in user's ID in `author`.

## 3. Add the routes to backend/server.js

Keep your existing MongoDB connection and other routes. Add:

```js
require("dotenv").config();

const authRoutes = require("./routes/auth");
const dashboardRoutes = require("./routes/dashboard");

app.use("/api/auth", authRoutes);
app.use("/api/dashboard", dashboardRoutes);
```

Make sure `app.use(express.json())` is registered before the routes.

Add a private JWT secret to your local `.env` file:

```env
JWT_SECRET=replace_this_with_a_long_random_secret
```

Do not upload `.env` to GitHub. Use `.env.example` as a template only.

## 4. Connect the frontend

- Copy `dashboard.html` and `dashboard.js` into your frontend folder.
- Update `API_BASE` in the JavaScript files if your backend URL is different.
- Add the logic from `login-integration.js` to your existing login form handler.
- Ensure your login form uses IDs `loginForm`, `email`, and `password` if using the example event listener.

## 5. API endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/auth/register` | Register a user |
| POST | `/api/auth/login` | Log in and receive JWT |
| GET | `/api/dashboard/profile` | Get logged-in user's profile |
| GET | `/api/dashboard/my-blogs` | Get only the logged-in user's blogs |

For protected requests, send this HTTP header:

`Authorization: Bearer YOUR_TOKEN`

## 6. Test before submitting

1. Start MongoDB and your backend.
2. Register a test account.
3. Log in and confirm a token is returned.
4. Open the dashboard and confirm profile details load.
5. Create a blog while logged in and confirm it appears under My Blogs.
6. Log out and confirm the dashboard redirects to the login page.
7. Try the dashboard API without a token; it should return HTTP 401.

## Important security note

This is a learning/demo implementation. For production applications, prefer secure HttpOnly cookies and add protections such as rate limiting, input validation, HTTPS, and appropriate CORS settings. A frontend redirect is not security by itself; the backend middleware protects the API.

This package is a set of integration files, not a complete replacement for your existing project. Merge it with your current code and test it before describing the milestone as completed.
