# Library Client — Frontend UI

A lightweight browser-based client for the [Library API](https://github.com/filatok/Library-api). Built with plain HTML, JavaScript, and Axios — no framework, no build step required.

---

## Tech Stack

| | |
|---|---|
| Language | HTML + Vanilla JavaScript |
| HTTP Client | Axios (CDN) |
| Build tool | None — open directly in browser |

---

## Prerequisites

- A modern web browser (Chrome, Firefox, Edge)
- The **Library API running locally** at `http://localhost:8080`  
  → See the [Library API README](https://github.com/filatok/Library-api) for setup instructions

---

## Getting Started

No installation needed. Just open the file in your browser:

```
index.html → Right-click → Open with → Browser
```

Or serve it with any static file server, for example with VS Code's **Live Server** extension.

 The API must be running at `http://localhost:8080` before using the client, otherwise all requests will fail.

---

## Features

The UI has a top navigation bar with three sections: **Home**, **Authors**, and **Books**.

---

### Home
The default landing page. Displays a welcome message.

---

### Authors

Displays a table of all authors fetched from `GET /authors`.

**For each author you can:**

| Action | Description |
|---|---|
| Edit | Opens an edit form pre-filled with the author's data |
| Create | Opens a blank form to add a new author |
| Delete | Prompts for confirmation, then deletes the author |

**The Author form includes:**

- Name, Nationality, Birthdate fields
- A table of the author's currently assigned books (Title, ISBN, Category, Publication Year) with a remove button per book
- A dropdown to assign an existing book to the author (already-assigned books are filtered out)
- **Save** — creates a new author (`POST /authors`) or updates an existing one (`PUT /authors/{id}`)
- **Close** — returns to the authors list

---

### Books

Displays a table of all books fetched from `GET /books`.

**For each book you can:**

| Action | Description |
|---|---|
| Edit | Opens an edit form pre-filled with the book's data |
| Create | Opens a blank form to add a new book |
| Delete | Prompts for confirmation, then deletes the book |

**The Book form includes:**

- Title, Category, Publication Year, ISBN fields
- A table of the book's currently assigned authors (Name, Nationality, Birthdate) with a remove button per author
- A dropdown to assign an existing author to the book (already-assigned authors are filtered out)
- **Save** — creates a new book (`POST /books`) or updates an existing one (`PUT /books/{id}`)
- **Close** — returns to the books list

---

## API Calls Summary

| Action | Method | Endpoint |
|---|---|---|
| Load all authors | GET | `/authors` |
| Load author by ID | GET | `/authors/{id}` |
| Load books by author | GET | `/authors/{id}/books` |
| Create author | POST | `/authors` |
| Update author | PUT | `/authors/{id}` |
| Delete author | DELETE | `/authors/{id}` |
| Assign book to author | POST | `/authors/{authorId}/books/{bookId}` |
| Remove book from author | DELETE | `/authors/{authorId}/books/{bookId}` |
| Load all books | GET | `/books` |
| Load book by ID | GET | `/books/{id}` |
| Load authors by book | GET | `/books/{id}/authors` |
| Create book | POST | `/books` |
| Update book | PUT | `/books/{id}` |
| Delete book | DELETE | `/books/{id}` |
| Assign author to book | POST | `/books/{bookId}/authors/{authorId}` |
| Remove author from book | DELETE | `/books/{bookId}/authors/{authorId}` |

---

## Known Limitations

- The API base URL (`http://localhost:8080`) is **hardcoded** in the JavaScript. To point to a different server, do a find-and-replace in `index.html`.
- No authentication — relies on the API's open CORS policy.
- Error handling shows browser `alert()` dialogs.

---
