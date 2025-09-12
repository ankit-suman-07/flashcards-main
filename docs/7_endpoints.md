# 📌 **API Endpoints with Descriptions (All Phases, RESTful)**

---

## 🚀 **Phase 1 – Single User MVP**

### 👤 **User (`/api/users/*`)** → `user.routes.js`

* `POST /api/users/register` → **Register a new user account**. Saves username, email, password.
* `POST /api/auth/login` → **Login** with credentials, returns token/session.
* `POST /api/auth/logout` → **Logout** user (invalidate session/token).
* `GET /api/users/:userId` → **Get a user profile** including decks, collections, and progress.
* `GET /api/users/:userId/stats` → **Get learning stats** (streak, XP, progress summary).
* `GET /api/users/me` → **Get logged-in user profile** using token.

---

### 📚 **Decks (`/api/decks/*`)** → `deck.routes.js`

* `POST /api/decks` → **Create a deck** with name, description, visibility, tags.
* `GET /api/decks` → **List all decks** (supports `?tag=filter`).
* `GET /api/decks/:deckId` → **Get details of a deck** including its cards.
* `PUT /api/decks/:deckId` → **Update deck** (name, description, tags, visibility).
* `DELETE /api/decks/:deckId` → **Delete deck** (cascade delete cards).

---

### 🃏 **Cards (`/api/decks/:deckId/cards/*`)** → `card.routes.js`

* `POST /api/decks/:deckId/cards` → **Add a card** (question, answer, media, hint).
* `GET /api/decks/:deckId/cards` → **List all cards** in a deck.
* `GET /api/cards/:cardId` → **Get details of one card**.
* `PUT /api/cards/:cardId` → **Update a card** (question, answer, bidirectional, media, hint).
* `DELETE /api/cards/:cardId` → **Delete a card**.

---

### 🔁 **Revisions (`/api/revisions/*`)** → `revision.routes.js`

* `POST /api/revisions` → **Start a revision session** (creates `revision_session`, requires `deckId`).
* `POST /api/revisions/:revisionId/cards/:cardId/answer` → **Submit confidence** (`got_it`, `almost`, `again`) → updates **CardProgress**.
* `GET /api/revisions/:revisionId/next` → **Get next card** for revision.
* `GET /api/revisions/:revisionId/progress` → **Get progress summary** for session (deck-level stats).
* `GET /api/revisions/history` → **Get past sessions** with summary + stats.

---

## 🎨 **Phase 2 – Multimedia Enhancements**

### 🎥 **Card Media (`/api/cards/:cardId/media/*`)** → `card.routes.js`

* `POST /api/cards/:cardId/media` → **Upload media** (image, audio, video). Stores file URLs in `media_urls`.
* `GET /api/cards/:cardId/media` → **Fetch attached media** for the card.
* `DELETE /api/cards/:cardId/media/:mediaId` → **Remove media** from a card.

💡 Adds multimedia support to flashcards (diagrams, pronunciations, etc.).

---

## 👥 **Phase 3 – Multi-User & Sharing**

### 👤 **User Management (`/api/users/*`)** → `user.routes.js`

* `GET /api/users` → **List all users** (Admin only).
* `PUT /api/users/:userId` → **Update profile or preferences**.
* `DELETE /api/users/:userId` → **Delete user account**.

---

### 📂 **Collections (`/api/collections/*`)** → `collection.routes.js`

* `POST /api/collections` → **Create a collection** (group decks).
* `GET /api/collections` → **List all collections** for a user.
* `GET /api/collections/:collectionId` → **Get details of a collection**.
* `POST /api/collections/:collectionId/decks/:deckId` → **Add deck to collection**.
* `GET /api/collections/:collectionId/decks` → **List decks in collection**.
* `DELETE /api/collections/:collectionId/decks/:deckId` → **Remove deck from collection**.

💡 Lets users group decks for goals like “Exam Prep”.

---

### 🤝 **Sharing (`/api/decks/:deckId/share`, `/api/collections/:collectionId/share`)** → `share.routes.js`

* `POST /api/decks/:deckId/share` → **Share deck** with another user.
* `PUT /api/decks/:deckId/share/:userId` → **Update sharing permission** (`view | edit`).
* `DELETE /api/decks/:deckId/share/:userId` → **Revoke sharing**.
* `POST /api/collections/:collectionId/share` → **Share collection** with another user.
* `GET /api/shared/decks` → **List decks shared with me**.
* `GET /api/shared/collections` → **List collections shared with me**.

💡 Enables collaboration, study groups, classrooms.

---

## 🤖 **Phase 4 – Smart Revision & AI**

### 🔄 **Smart Revision (`/api/revisions/:revisionId/schedule`)** → `revision.routes.js`

* `GET /api/revisions/:revisionId/schedule` → **Get spaced repetition schedule** (SM-2 algorithm).

💡 Uses SRS for optimal memory retention.

---

### 🤖 **AI (`/api/ai/cards/*`)** → `ai.routes.js`

* `POST /api/ai/cards/generate` → **Upload PDF/text/webpage**, AI parses & generates flashcards.
* `GET /api/ai/cards/status/:jobId` → **Check job status** (`pending`, `processing`, `done`).
* `GET /api/ai/cards/:jobId/results` → **Retrieve generated cards** as a draft deck.

💡 Automates card generation from notes/books.

---

# ✅ Summary

* **Phase 1** = Core CRUD + Revision system.
* **Phase 2** = Multimedia flashcards.
* **Phase 3** = Multi-user, collections, sharing.
* **Phase 4** = Smart spaced repetition + AI card generation.
