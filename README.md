# Blog Application — CRUD Milestone

This package contains files to add Create, Read, Update, Delete, search, and category filtering to an existing Node.js + Express + MongoDB blog application.

## Included files

- `backend/routes/blogs.js` — CRUD API routes, search, category filter, and author-only update/delete checks.
- `backend/models/Blog.js` — Mongoose blog schema with category and author fields.
- `frontend/crud.js` — browser-side functions for calling the CRUD APIs.

## Integration

1. Copy the `backend/routes/blogs.js` file into your backend, replacing or merging your existing blog routes.
2. Copy `backend/models/Blog.js` into your backend. If you already have a Blog model, merge the `category` field into it rather than defining the model twice.
3. In your backend server file, ensure the routes are mounted:

   ```javascript
   app.use("/api/blogs", require("./routes/blogs"));
   ```

   Adjust the path if your routes folder is elsewhere.

4. Ensure your server loads environment variables and has JSON parsing enabled:

   ```javascript
   require("dotenv").config();
   app.use(express.json());
   ```

5. Ensure your backend `.env` contains `JWT_SECRET` and `MONGO_URI`. Never commit the real `.env` file.
6. Copy `frontend/crud.js` into your frontend and include it in the relevant HTML page:

   ```html
   <script src="crud.js"></script>
   ```

7. Update the API URL in `crud.js` if your backend does not run at `http://localhost:5000`.
8. Ensure login stores the JWT returned by the login API in `localStorage` under the key `token`.

## API endpoints

| Method | Endpoint | Description | Login required |
|---|---|---|---|
| POST | `/api/blogs` | Create a blog | Yes |
| GET | `/api/blogs` | Read all blogs | No |
| GET | `/api/blogs/:id` | Read one blog | No |
| PUT | `/api/blogs/:id` | Update own blog | Yes |
| DELETE | `/api/blogs/:id` | Delete own blog | Yes |
| GET | `/api/blogs?search=term` | Search title/content | No |
| GET | `/api/blogs?category=Technology` | Filter by category | No |

For POST and PUT, send JSON such as:

```json
{
  "title": "My first blog",
  "content": "This is my blog content.",
  "category": "Technology"
}
```

For authenticated requests, send this HTTP header:

`Authorization: Bearer YOUR_LOGIN_TOKEN`

## Test before submission

- Register and log in.
- Create a blog and verify it appears in MongoDB.
- Read all blogs and open an individual blog.
- Update a blog while logged in as its author.
- Confirm another user cannot update or delete that blog.
- Delete your own blog.
- Test search and category filtering.

## Important

This is an integration package, not a complete ready-to-run website or a MongoDB database backup. Merge it into your existing project, connect the functions to your current form/buttons, test locally, and then commit the updated files to GitHub. Do not upload database passwords, JWT secrets, `.env`, or `node_modules`.
