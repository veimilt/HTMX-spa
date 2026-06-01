# HTMX SPA

## Link to the deployed application

https://htmx-spa.onrender.com

A small Express application that demonstrates server-rendered pages with Pug and partial page updates with HTMX.

The app shows a simple article list, individual article pages, and a form for adding new articles. Full pages are rendered by Express with Pug templates, while HTMX updates the article list without a full browser refresh after a new article is submitted.

## Features

- Express server with Pug as the view engine
- Shared layout template for pages
- Reusable Pug partials for the article list and loading indicator
- HTMX-powered form submission
- Static assets served from `public/`
- In-memory article data

## Project Structure

```text
.
├── app.js
├── data/
│   └── articles.js
├── public/
│   ├── shuriken.png
│   └── styles.css
├── routes/
│   └── index.js
└── views/
    ├── article.pug
    ├── index.pug
    ├── layouts/
    │   └── layout.pug
    └── partials/
        ├── list.pug
        └── loader.pug
```

## How It Works

`app.js` creates the Express server, serves static files from `public/`, enables form body parsing, sets Pug as the view engine, and mounts the router.

The main routes are defined in `routes/index.js`:

- `GET /` renders the home page with all articles.
- `GET /articles/:id` renders a single article page.
- `POST /articles` creates a new article and returns the updated article list partial.

The Pug views live in `views/`. `index.pug` and `article.pug` both extend `views/layouts/layout.pug`, which provides the shared HTML structure, navigation, stylesheet link, and HTMX script.

The article list is rendered through `views/partials/list.pug`. This partial is used on the initial page load and again after submitting the add-article form. HTMX swaps the returned partial HTML into `.article-list`.

## Getting Started

Install dependencies:

```bash
npm install
```

Start the server:

```bash
node app.js
```

Then open:

```text
http://localhost:3000
```

## Dependencies

- [Express](https://expressjs.com/)
- [Pug](https://pugjs.org/)
- [HTMX](https://htmx.org/)

## Credit

This project is based on a tutorial by [Net Ninja](https://www.youtube.com/@NetNinja).
