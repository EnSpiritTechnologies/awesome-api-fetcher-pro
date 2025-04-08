# 🔌 Awesome API Fetcher Pro

This is a custom WordPress plugin that fetches data from an external API, stores it in a custom database table, exposes a REST API endpoint, provides a shortcode for frontend rendering, and includes a full-featured admin panel.

The plugin is designed with modularity, maintainability, and performance in mind, following modern WordPress development practices.

---

## 📦 Features

- Fetches posts from `https://jsonplaceholder.typicode.com/posts`
- Stores them in a custom DB table (`wp_awesome_posts`)
- Creates a custom REST API endpoint for accessing the stored data
- Adds a shortcode `[awesome-posts]` for displaying posts on the frontend
- Provides a clean admin UI under **Tools > Awesome API**
- Includes cron job to automatically refresh API data every 6 hours
- Supports manual data fetch and record deletion from admin
- Refactored legacy procedural code into modern OOP

---

## 🧩 Plugin Structure

- **/includes/**
  - Classes and helpers for API fetching, DB interactions, REST API, and shortcode rendering
- **/admin/**
  - Admin UI logic, list table, action handlers
- **awesome-api-fetcher-pro.php**
  - Plugin bootstrap and core hook registration

---

## 🔗 REST API Endpoint

`GET /wp-json/awesome/v1/posts`

### Optional Query Parameters:
- `?search=` – filter by post title
- `?limit=` – limit number of returned results
- `?sort=` – sort by title or date

---

## 💻 Shortcode

`[awesome-posts limit="10" search="ipsum" sort="title"]`

Renders a list of post titles stored in the DB with optional filtering. Cached via transients for performance.

---

## ⚙️ Admin Interface

Available at: **Tools > Awesome API**

- View stored posts in a paginated list
- Manually trigger API fetch
- Delete individual or bulk records
- Protected with nonces and capability checks

---

## 🔄 CRON Sync

- A WP-Cron task runs every 6 hours to refresh the data
- Handles API errors and logs failures

---

## 🧼 Code Refactoring

Legacy procedural code (see `legacy-functions.php`) has been refactored into classes and integrated using dependency injection where appropriate. Old logic preserved for reference.

---

## 🚀 Installation

1. Clone this repo into your WordPress plugins folder:
```bash
git clone https://github.com/YOUR-USERNAME/awesome-api-fetcher-pro.git wp-content/plugins/awesome-api-fetcher-pro
