# TriggerLog 🍽️

**A food and symptom journal built with Node.js, Express, and MongoDB.**

TriggerLog lets users record meals, foods, symptoms, and severity in one place. It provides a searchable history for reviewing entries over time.

## Features

- **Manage entries:** Create, view, edit, and delete food and symptom logs.
- **Record meal details:** Add multiple foods and quantities to an entry.
- **Track symptoms:** Record multiple symptoms with severity ratings from 1–10.
- **Add context:** Include dates, meal times, and optional notes.
- **Search history:** Find entries using fuzzy search.
- **Responsive interface:** Bootstrap-based layouts for different screen sizes.
- **Theme switching:** Choose between light and dark modes.

## Tech Stack

| Area | Technologies |
|---|---|
| Backend | Node.js, Express |
| Templates | Handlebars |
| Database | MongoDB |
| ODM | Mongoose |
| Frontend | Bootstrap 5, Font Awesome, JavaScript, CSS |
| Supporting tools | dotenv, method-override, express-session, connect-mongo |

## Getting Started

### Requirements

- A supported Node.js LTS version compatible with the project's dependencies
- npm
- A local MongoDB instance or MongoDB Atlas database

### Installation

Download or clone this repository, then open a terminal in the project folder.

Install dependencies:

```bash
npm install
```

Create a `.env` file in the project root:

```env
MONGODB_URI=mongodb://127.0.0.1:27017/triggerlog
PORT=3000
```

For MongoDB Atlas, replace `MONGODB_URI` with your database connection string.

Start the application:

```bash
npm start
```

Open **http://localhost:3000** in your browser.

If a development script is defined in `package.json`, you can also run:

```bash
npm run dev
```

### Configuration

| Variable | Purpose |
|---|---|
| `MONGODB_URI` | Connection string for the MongoDB database |
| `PORT` | Server port; use `3000` for local development |

Keep your `.env` file out of Git. A committed `.env.example` should contain placeholder values only.

## Using TriggerLog

1. Create a new entry and select its date and meal time.
2. Add the foods you ate and their quantities.
3. Record symptoms and rate their severity.
4. Add any notes that help describe the entry.
5. Save the entry and review it in your log history.
6. Search, edit, or delete entries as needed.

Entries are personal observations. TriggerLog does not establish that a particular food caused a symptom.

## Application Routes

The application renders HTML pages and processes form submissions.

| Method | Route | Purpose |
|---|---|---|
| `GET` | `/logs` | View all entries |
| `GET` | `/logs/new` | Open the new-entry form |
| `POST` | `/logs` | Create an entry |
| `GET` | `/logs/search` | Search entries |
| `GET` | `/logs/:id` | View an entry |
| `GET` | `/logs/:id/edit` | Open the edit form |
| `PUT` | `/logs/:id` | Update an entry |
| `DELETE` | `/logs/:id` | Delete an entry |

HTML forms use `method-override` to submit update and delete requests.

## Entry Data

Each log records:

- Date and meal time
- Foods and quantities
- Symptoms and severity ratings
- Optional notes
- Creation and update timestamps

MongoDB stores the entries, and Mongoose defines their structure.

## Deployment

For a Node.js hosting service such as Render:

1. Connect the GitHub repository.
2. Use `npm install` as the build command.
3. Use `npm start` as the start command.
4. Configure `MONGODB_URI` through the host's environment settings.
5. Ensure the MongoDB database permits connections from the hosting service.

The server must listen on the port provided by the host. Commit the application source, templates, static assets, and dependency files.

## Troubleshooting

**The application cannot connect to MongoDB**

Check the connection string, database credentials, and database network-access settings. For local development, confirm MongoDB is running.

**Styles or scripts are missing**

Check that static files are committed and that template URLs match their paths under `public/`.

**Foods or symptoms are not saving correctly**

Check that form field names match the nested structure expected by the route handlers and Mongoose schema.

## Author

**Jonathan Ilori**

[GitHub](https://github.com/lorris02) • [Portfolio](https://jonathanilori.com/) • [Email](mailto:ilorijonathan947@gmail.com)
