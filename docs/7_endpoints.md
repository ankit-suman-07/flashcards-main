# 📌 **API Endpoints with Descriptions (All Phases)**

## 🚀 **Phase 1 – Single User MVP**

### 👤 User (`/api/users`)

* `POST /api/users/register` → Create user account.
* `POST /api/users/login` → Login user, return token (mock for MVP).
* `POST /api/users/logout` → Logout user (invalidate session).
* `GET /api/users/:userId` → Fetch user profile (info + decks + collections + progress).
* `GET /api/users/:userId/stats` → Get user stats (streak, XP, learning summary).

### 📚 Decks (`/api/decks`)

* `POST /api/decks` → Create deck (name, description, tags, visibility).
* `GET /api/decks` → List all decks (optional `?tag=` filter).
* `GET /api/decks/:deckId` → Fetch deck details + cards.
* `PUT /api/decks/:deckId` → Update deck details.
* `DELETE /api/decks/:deckId` → Delete deck + cascade cards.

### 🃏 Cards (`/api/decks/:deckId/cards`)

* `POST /api/decks/:deckId/cards` → Add card (question, answer, media, hint).
* `GET /api/decks/:deckId/cards` → List all cards in deck.
* `GET /api/decks/:deckId/cards/:cardId` → Fetch single card.
* `PUT /api/decks/:deckId/cards/:cardId` → Update card fields.
* `DELETE /api/decks/:deckId/cards/:cardId` → Delete card.

### 🔁 Revision (`/api/decks/:deckId/revision`)

* `POST /api/decks/:deckId/revision/start` → Start a revision session.
* `POST /api/decks/:deckId/revision/:cardId/answer` → Submit confidence (`got_it | almost | again`) → updates **CardProgress**.
* `GET /api/decks/:deckId/revision/next` → Get next card in sequence.
* `GET /api/decks/:deckId/revision/progress` → Summary progress for the deck.
* `GET /api/revision/history` → Fetch past sessions & stats.

---

## 🎨 **Phase 2 – Multimedia Enhancements**

### Card Media (`/api/decks/:deckId/cards/:cardId/media`)

* `POST /api/decks/:deckId/cards/:cardId/media` → Upload media (image/audio/video). Stores links in `media_urls`.
* `GET /api/decks/:deckId/cards/:cardId/media` → Retrieve all media attached to the card.
* `DELETE /api/decks/:deckId/cards/:cardId/media` → Remove attached media.

💡 **Why:** Supports richer flashcards (diagrams, audio pronunciations, etc.).

---

## 👥 **Phase 3 – Multi-User & Sharing**

### User Management (`/api/users`)

* `GET /api/users` → (Admin only) List all users.
* `PUT /api/users/:userId` → Update user profile/preferences.
* `DELETE /api/users/:userId` → Delete user.
* `GET /api/users/me` → Fetch profile of logged-in user (via token).

---

### Collections (`/api/collections`)

* `POST /api/collections` → Create a new collection (group of decks).
* `GET /api/collections` → List all collections owned by user.
* `GET /api/collections/:collectionId` → Fetch collection details.
* `POST /api/collections/:collectionId/decks/:deckId` → Add deck to collection.
* `GET /api/collections/:collectionId/decks` → List decks inside collection.
* `DELETE /api/collections/:collectionId/decks/:deckId` → Remove deck from collection.

💡 **Why:** Lets users group decks for specific goals (e.g., "Final Exam Prep").

---

### Sharing (`/api/decks/:deckId/share`, `/api/collections/:collectionId/share`)

* `POST /api/decks/:deckId/share` → Share deck with another user.
* `PUT /api/decks/:deckId/share/:userId` → Update permission (`view | edit`).
* `DELETE /api/decks/:deckId/share/:userId` → Revoke sharing.
* `POST /api/collections/:collectionId/share` → Share collection with another user.
* `GET /api/decks/shared-with-me` → List decks shared with me.
* `GET /api/collections/shared-with-me` → List collections shared with me.

💡 **Why:** Enables collaboration (friends, study groups, classrooms).

---

## 🤖 **Phase 4 – Smart Revision & AI**

### Smart Revision (`/api/decks/:deckId/revision/schedule`)

* `GET /api/decks/:deckId/revision/schedule` → Get spaced repetition schedule (SM-2 algorithm).

💡 **Why:** Scientifically optimized learning intervals.

---

### AI-Generated Cards (`/api/ai/cards`)

* `POST /api/ai/cards/generate` → Upload PDF/text/webpage → AI parses & generates flashcards.
* `GET /api/ai/cards/status/:jobId` → Check status (`pending`, `processing`, `done`).
* `GET /api/ai/cards/:jobId/results` → Retrieve generated cards (as draft deck).

💡 **Why:** Auto-generate decks from notes, books, or web resources.

---

# ✅ Final Notes

* **Phase 1 endpoints** = Core CRUD + revision.
* **Phase 2** = Multimedia support.
* **Phase 3** = Multi-user, collections, sharing.
* **Phase 4** = Smart repetition & AI.


Perfect 👍 You want the **same structure as before**, but with **descriptions added for each endpoint + file mapping**.
Here’s the **full expanded version (all phases)**:

---

# 📂 **Project Structure & Endpoint Grouping**

Each **entity** (User, Deck, Card, Revision, Collection, Sharing, AI) has:

* **Route** → Defines endpoints.
* **Controller** → Handles HTTP request/response.
* **Service** → Business logic + database operations.

---


# 📌 **Endpoint → File Mapping with Descriptions**

---

## 👤 **User (`/api/users/*`)** → `user.routes.js`

* `POST /register` → Create user account (signup).
* `POST /login` → Login user, return token.
* `POST /logout` → Logout user (invalidate session).
* `GET /:userId` → Get profile (decks, collections, progress).
* `GET /:userId/stats` → Get streaks, XP, learning stats.
* `GET /me` → Get profile of logged-in user (via token).

---

## 📚 **Deck (`/api/decks/*`)** → `deck.routes.js`

* `POST /` → Create a new deck.
* `GET /` → List all decks (optional filter by tag).
* `GET /:deckId` → Get deck details + cards.
* `PUT /:deckId` → Update deck (name, description, tags, visibility).
* `DELETE /:deckId` → Delete deck + cascade cards.

---

## 🃏 **Card (`/api/decks/:deckId/cards/*`)** → `card.routes.js`

* `POST /` → Add card to deck.
* `GET /` → List all cards in deck.
* `GET /:cardId` → Get single card.
* `PUT /:cardId` → Update card (question, answer, media, isBidirectional).
* `DELETE /:cardId` → Delete card.

---

## 🔁 **Revision (`/api/decks/:deckId/revision/*`)** → `revision.routes.js`

* `POST /start` → Start revision session (creates `revision_session` entry).
* `POST /:cardId/answer` → Submit confidence → update **CardProgress**.
* `GET /next` → Get next card (based on spaced repetition or status).
* `GET /progress` → Get progress summary for this deck.
* `GET /api/revision/history` → Fetch past sessions + stats.

---

## 📂 **Collections (`/api/collections/*`)** → `collection.routes.js`

* `POST /` → Create a collection.
* `GET /` → List all collections.
* `GET /:collectionId` → Get collection details.
* `POST /:collectionId/decks/:deckId` → Add deck to collection.
* `GET /:collectionId/decks` → List decks in collection.
* `DELETE /:collectionId/decks/:deckId` → Remove deck from collection.

---

## 🤝 **Sharing (`/api/decks/:deckId/share/*`, `/api/collections/:collectionId/share/*`)** → `share.routes.js`

* `POST /decks/:deckId/share` → Share deck with another user.
* `PUT /decks/:deckId/share/:userId` → Update sharing permission (`view | edit`).
* `DELETE /decks/:deckId/share/:userId` → Revoke sharing.
* `POST /collections/:collectionId/share` → Share collection with another user.
* `GET /decks/shared-with-me` → List decks shared with me.
* `GET /collections/shared-with-me` → List collections shared with me.

---

## 🤖 **AI (`/api/ai/*`)** → `ai.routes.js`

* `POST /cards/generate` → Upload PDF/text → AI generates cards.
* `GET /cards/status/:jobId` → Check status (`pending`, `processing`, `done`).
* `GET /cards/:jobId/results` → Retrieve generated cards.