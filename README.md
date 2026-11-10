# Full Stack Blog Application

A full-stack blog application where users can register, log in, and manage their own blog posts.

## Live Demo

- Frontend URL: `ADD_YOUR_VERCEL_URL_HERE`
- Backend API URL: `ADD_YOUR_RENDER_URL_HERE`
- GitHub Repository: `ADD_YOUR_GITHUB_REPOSITORY_URL_HERE`

## Features

- User registration and login
- JWT-based authentication
- Protected dashboard
- User profile
- Create, read, update, and delete blog posts
- Users can view and manage their own posts
- Responsive user interface

> Remove or edit any feature above that is not implemented and tested in your application.

## Technologies Used

- Frontend: HTML, CSS, JavaScript
- Backend: Node.js, Express.js
- Database: MongoDB / MongoDB Atlas
- Authentication: JSON Web Tokens (JWT), bcryptjs
- Deployment: Vercel (frontend), Render (backend)

## Project Structure

```text
Blog-Application/
├── frontend/
│   ├── index.html
│   ├── login.html
│   ├── register.html
│   ├── dashboard.html
│   ├── style.css
│   └── ...
├── backend/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── server.js
│   ├── package.json
│   └── ...
├── README.md
└── .gitignore
```

Update this structure to match your actual repository.

## Run Locally

### Backend

```bash
cd backend
npm install
```

Create a private `.env` file in the backend folder:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_long_random_secret
```

Start the backend:

```bash
npm start
```

### Frontend

Open the frontend using your local development server or the method used by your project. Update the frontend API base URL to your backend URL.

## Deployment

### Backend on Render

- Connect this GitHub repository to Render.
- Set the backend root directory (for example, `backend`).
- Build command: `npm install`
- Start command: `npm start`
- Add `MONGO_URI`, `JWT_SECRET`, and any other required environment variables in Render's environment settings.
- Set `NODE_ENV=production` if your app uses it.

### Frontend on Vercel

- Import this GitHub repository into Vercel.
- Set the frontend root directory (for example, `frontend`).
- For a plain HTML/CSS/JavaScript project, use the Other framework preset and leave the build command empty unless your project requires one.
- Update the API base URL to the deployed backend URL.
- Configure backend CORS to allow your deployed frontend domain.

## API Endpoints

Update this table to match your actual backend routes.

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register a user |
| POST | `/api/auth/login` | Log in |
| GET | `/api/dashboard/profile` | Get logged-in user's profile |
| GET | `/api/dashboard/my-blogs` | Get logged-in user's blogs |
| GET | `/api/blogs` | List blogs |
| POST | `/api/blogs` | Create a blog |
| PUT | `/api/blogs/:id` | Update a blog |
| DELETE | `/api/blogs/:id` | Delete a blog |

## Testing Checklist

- [ ] Registration works
- [ ] Login works
- [ ] Protected routes reject requests without a valid token
- [ ] Dashboard displays the correct user profile
- [ ] Users can see only their own blogs where intended
- [ ] Create, update, and delete operations work
- [ ] Logout works
- [ ] Frontend works on mobile screen sizes
- [ ] Deployed frontend can communicate with deployed backend

## Security

- Never commit `.env` files, database passwords, JWT secrets, or API keys.
- Store deployment secrets in Render's environment settings.
- Use HTTPS in production.
- Configure CORS for the actual frontend domain.
- Use secure cookie-based token storage and additional protections for production deployments.

## Screenshots

Add screenshots of your homepage, login page, dashboard, and mobile layout here.
