# Advanced Manhwa Tracker

A lightweight, client-side manhwa/webtoon tracker built with plain HTML, CSS (Tailwind), and vanilla JavaScript. It stores your library in the browser (localStorage) and offers features to add, edit, delete, search, filter, sort, paginate, import/export data, and preview/upload cover images.

This README describes how to run and use the tracker. The main UI file is indexmy.html.

---

## Features

- Add new entries with title, author, chapter, status, website, image (URL or upload), and notes.
- Edit existing entries via a modal editor.
- Delete entries with confirmation.
- Search by title or author (debounced).
- Filter by status and sort by date added, title, chapter, or last updated.
- Pagination (configurable items per page).
- Image handling:
  - Image URL has priority; uploaded images (max 2 MB) are stored as data URLs.
  - Fallback placeholder images generated via placehold.co.
- Client-side storage in localStorage under the key `manhwas_v2`.
- Import/export JSON backups (merge or replace on import).
- Responsive and accessible UI with keyboard-friendly elements where appropriate.

---

## Quick Start

No build step required — this is a static single-page application.

Option A — Open locally:
1. Download or clone the repository.
2. Open `indexmy.html` in your web browser.

Option B — Serve locally (recommended for consistent behavior with file inputs & fetch):
1. From the project root, run a simple static server:
   - Python 3: `python -m http.server 8000`
   - Node (http-server): `npx http-server -p 8000`
2. Open `http://localhost:8000/indexmy.html` in your browser.

---

## Usage

- Add New: Click "Add New" to open the form. Title is required.
  - If you supply both an image URL and an uploaded file, the URL takes priority.
  - Uploaded images are validated and limited to 2 MB.
- Edit: Click the edit icon on a card to open the edit modal and update fields.
- Delete: Click the trash icon and confirm.
- Search: Type in the search box; results update after a small debounce.
- Filter & Sort: Use the dropdowns to narrow or reorder results.
- Export: Save a JSON backup of your library.
- Import: Load a JSON backup; you will be prompted to merge or replace your current library.

Data is persisted in localStorage; clearing browser storage will remove saved entries.

---

## Data Format (JSON)

Saved entries follow this structure:

{
  id: number,
  title: string,
  author: string,
  chapter: number,
  status: string, // Reading, Planned, On Hold, Completed, Dropped
  website: string,
  image: string, // URL or data URL
  description: string,
  dateAdded: number, // timestamp
  lastUpdated: number // timestamp
}

When importing, the app validates the array structure and prompts to merge or replace.

---

## Notes & Tips

- localStorage size limits vary by browser. Storing many large uploaded images (data URLs) could hit quota. Prefer image URLs for large cover images.
- The app uses `manhwas_v2` key in localStorage; migrating or renaming keys will require code changes.
- Uploaded image validation rejects non-image files and files larger than 2 MB.
- The app is purely client-side — no server required. If you want multi-device sync, consider adding an export/import workflow or connect it to a backend.

---

## Contributing

Bug reports, suggestions, or pull requests are welcome. For small changes:
- Fork the repository
- Create a feature branch
- Open a PR describing the change

If you want help implementing server-side sync, pagination improvements, or authentication, open an issue outlining the intended behavior.

---

## Contact

If you need help or want to discuss features, open an issue in the repository.

---

Happy tracking!
