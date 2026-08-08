# Headless CMS

A flexible, headless CMS built with Node.js and MongoDB for managing small business websites.

## Features

- ✅ **Content Management** — Create, edit, delete pages, blog posts, products, and more
- ✅ **User Roles** — Admin, Editor, and Viewer roles with granular permissions
- ✅ **REST API** — Full API for content delivery to any frontend
- ✅ **Authentication** — JWT-based authentication
- ✅ **Publishing Workflow** — Draft and published states
- ✅ **SEO Support** — Meta titles, descriptions, and keywords
- ✅ **Flexible Schema** — Support for various content types

## Tech Stack

- **Backend:** Node.js + Express
- **Database:** MongoDB
- **Authentication:** JWT

## Installation

1. Clone the repository
   ```bash
   git clone https://github.com/louisskiing5-eng/cms.git
   cd cms
   ```

2. Install dependencies
   ```bash
   npm install
   ```

3. Set up environment variables
   ```bash
   cp .env.example .env
   # Edit .env with your MongoDB URI and JWT secret
   ```

4. Start the server
   ```bash
   npm run dev
   ```

The CMS API will be running at `http://localhost:5000`

## API Endpoints

### Health Check
- `GET /api/health` — Check if CMS is running

### Authentication
- `POST /api/auth/register` — Register a new user
- `POST /api/auth/login` — Login user

### Content (Public)
- `GET /api/content/public` — Get all published content
- `GET /api/content/public/:slug` — Get single content by slug

### Content (Admin/Editor)
- `GET /api/content` — Get all content
- `POST /api/content` — Create content
- `PUT /api/content/:id` — Update content
- `DELETE /api/content/:id` — Delete content

### Users (Admin)
- `GET /api/users` — Get all users
- `GET /api/users/me` — Get current user
- `PUT /api/users/:id/role` — Update user role

## Content Types

The CMS supports the following content types:
- **page** — Static pages (About, Contact, etc.)
- **blog** — Blog posts
- **product** — Product listings
- **team** — Team member profiles
- **custom** — Custom content types

## Request/Response Examples

### Register
```bash
POST /api/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "securepassword123"
}
```

Response:
```json
{
  "message": "User registered successfully",
  "token": "eyJhbGc...",
  "user": {
    "id": "507f1f77bcf86cd799439011",
    "name": "John Doe",
    "email": "john@example.com",
    "role": "viewer"
  }
}
```

### Login
```bash
POST /api/auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "securepassword123"
}
```

### Create Content
```bash
POST /api/content
Authorization: Bearer eyJhbGc...
Content-Type: application/json

{
  "title": "Welcome to our website",
  "slug": "welcome",
  "contentType": "page",
  "content": {
    "body": "This is the homepage content"
  },
  "status": "published",
  "seo": {
    "metaTitle": "Welcome",
    "metaDescription": "Welcome to our website",
    "keywords": ["welcome", "home"]
  }
}
```

### Get Published Content
```bash
GET /api/content/public
```

## User Roles

- **Admin** — Full access to all features and user management
- **Editor** — Can create, edit, and delete their own content
- **Viewer** — Can only view published content

## Environment Variables

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/headless-cms
JWT_SECRET=your_very_secure_secret_key_here
NODE_ENV=development
CLIENT_URL=http://localhost:3000
```

## Next Steps

- [ ] Build admin dashboard (React/Vue)
- [ ] Add media management
- [ ] Add webhooks
- [ ] Add API documentation (Swagger/OpenAPI)
- [ ] Add email notifications
- [ ] Deploy to production (Heroku, AWS, etc.)

## License

ISC

---

**Created by louisskiing5-eng** | Headless CMS v1.0.0
