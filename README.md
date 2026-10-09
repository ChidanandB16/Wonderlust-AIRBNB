# Wanderlust

An Airbnb-inspired web application for exploring accommodation listings, sharing properties, and leaving reviews. Built with Node.js, Express, MongoDB, and EJS.

## Live demo

**[Explore Wanderlust](https://wanderlust-s9l5.onrender.com/listings)**

## Features

- Browse accommodation listings with photos, locations, descriptions, and nightly prices.
- Sign up, log in, and log out using Passport authentication.
- Create listings with image uploads to Cloudinary.
- Edit and delete your own listings with owner checks.
- Add ratings and comments to listings.
- View listing locations on a Mapbox map, with geocoding when a listing is created.
- Show or hide the 18% GST label beside nightly prices.
- Display success and error messages using flash notifications.
- Store sessions in MongoDB.

## Tech stack

| Area | Tools |
| --- | --- |
| Server | Node.js, Express.js |
| Database | MongoDB, Mongoose |
| Templates and UI | EJS, EJS-Mate, Bootstrap, CSS, JavaScript |
| Authentication | Passport, Passport Local, Passport Local Mongoose |
| Sessions | Express Session, Connect Mongo, Connect Flash |
| Image uploads | Multer, Cloudinary, Multer Storage Cloudinary |
| Maps | Mapbox GL JS, Mapbox SDK |
| Environment configuration | Dotenv |
| Live deployment | Render |

## Repository status

The live demo is available at the link above. This repository currently contains a flat upload of the project files, while the application expects folders such as `models/`, `routes/`, `controllers/`, `utils/`, `views/`, and `public/`.

The required model files are not included in the current upload. A fresh clone cannot run as-is until the original folder structure and missing models are restored. The setup below describes the application's configuration once those files are in place.

## Local setup

### Requirements

- Node.js 22.1.0, as specified in `package.json`
- A local MongoDB instance or MongoDB Atlas database
- Cloudinary credentials for image uploads
- A Mapbox access token
- The complete project structure and model files noted above

### Install dependencies

```bash
git clone https://github.com/ChidanandB16/Wonderlust-AIRBNB.git
cd Wonderlust-AIRBNB
npm install
```

### Configure environment variables

Create a `.env` file in the project root:

```dotenv
ATLASDB_URL=your_mongodb_connection_string
SECRET=your_strong_session_secret
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret
MAP_TOKEN=your_mapbox_access_token
PORT=8080
```

Keep `.env` and credentials out of version control. Set a strong `SECRET` instead of relying on the application's fallback value.

If `ATLASDB_URL` is not set, the application uses `mongodb://localhost:27017/mydatabase`.

### Start the application

After restoring the required folders and models:

```bash
node app.js
```

The deployed application is available at **[https://wanderlust-s9l5.onrender.com/listings](https://wanderlust-s9l5.onrender.com/listings)**.

`app.js` is the web server entry point. The current `index.js` is a database seed script, not the server; it deletes existing listings and uses a hard-coded owner ID, so do not run it against a database containing data you want to keep.

## Development notes

- There is no `npm start` script in the current `package.json`.
- An automated test suite is not configured; `npm test` currently exits with a placeholder error.
- The search box and category icons are present in the UI, but the current listing controller returns all listings without search or category filtering.
- This is a listing-and-review project. Booking and payment flows are not implemented in the uploaded code.
