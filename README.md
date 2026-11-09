# BlogSpace Backend Project
Frontend: HTML, CSS, JavaScript. Backend: Node.js and Express.js.

## Run
1. Install Node.js LTS.
2. Open this folder in VS Code terminal.
3. Run `npm install`.
4. Copy `.env.example` to `.env`; set a long random `JWT_SECRET`.
5. Run `npm start`.
6. Visit http://localhost:3000 (do not open HTML directly).

## REST API
| Method | Endpoint | Purpose |
|---|---|---|
| GET | /api/health | Check server |
| POST | /api/auth/register | Register user |
| POST | /api/auth/login | Login |
| GET | /api/blogs | List public blogs |
| POST | /api/blogs | Create blog (Bearer token) |
| GET | /api/blogs/mine | User's blogs (Bearer token) |
| DELETE | /api/blogs/:id | Delete own blog (Bearer token) |

Passwords are hashed with bcrypt and protected routes use JWT. Demo data is stored in data.json. For production, use a real database and additional security controls. Never upload `.env`, `data.json`, or `node_modules` to GitHub.
