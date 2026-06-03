# Authentification

A simple authentication app built with Express and Passport.js, part of [The Odin Project](https://www.theodinproject.com) Full Stack JavaScript curriculum.

## Tech Stack

| Technology   | Purpose                          |
|-------------|----------------------------------|
| **Express 5** | Web framework                  |
| **EJS**       | Template engine (views)        |
| **Passport.js** + `passport-local` | Authentication |
| **bcryptjs**  | Password hashing               |
| **express-session** | Session management        |
| **PostgreSQL** (`pg`) | Database               |

## Project Structure

```
Authentification/
├── app.js                     # Entry point — all routes, models, middleware
├── package.json
├── public/
│   └── stylesheets/
│       └── style.css          # Custom styles
└── views/
    ├── index.ejs              # Home page (logged-in / logged-out states)
    ├── log-in.ejs             # Login form with flash messages
    ├── sign-up-form.ejs       # Registration form
    ├── _header.ejs            # Nav partial
    └── _footer.ejs            # Footer partial
```

## Routes

| Method | Path       | Description                |
|--------|-----------|----------------------------|
| GET    | `/`       | Home page                  |
| GET    | `/sign-up`| Sign-up form               |
| POST   | `/sign-up`| Create user (bcrypt hash)  |
| GET    | `/log-in` | Login form with messages   |
| POST   | `/log-in` | Passport local auth        |
| GET    | `/log-out`| Logout and redirect        |

> All route handlers, database queries, Passport strategy, serialization, and session config live in `app.js` — no separate routes, models, or middleware directories.

## Database

This app expects a PostgreSQL database with a `users` table:

```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  username VARCHAR(255) UNIQUE NOT NULL,
  password VARCHAR(255) NOT NULL
);
```

Connection config is hardcoded in `app.js` (default: `postgres:postgres@localhost:5432/auth_app`).

## Getting Started

```bash
# Install dependencies
npm install

# Make sure PostgreSQL is running and auth_app database exists

# Start the server
npm run dev
```

Visit `http://localhost:3000`.

## Scripts

| Script | Command         |
|--------|-----------------|
| `start`| `node app.js`   |
| `dev`  | `node --watch app.js` |
