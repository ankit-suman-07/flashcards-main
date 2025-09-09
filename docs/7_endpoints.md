# 📌 Endpoints Mapping (by Entities & Features)

## **Phase 1: Single User App (MVP)**

### User

* `POST /api/users/register` → Create account (signup).
* `POST /api/users/login` → Login and get token (simple mock token in Phase 1).
* `POST /api/users/logout` → Invalidate session (optional in Phase 1, full in Phase 3).
* `GET /api/users/:userId` → Get user profile (details: decks, collections, progress).
* `GET /api/users/:userId/stats` → Get streaks, XP, and learning stats.

---

### Deck

* `POST /api/decks` → Create a new deck.
* `GET /api/decks` → List all decks (with optional `?tag=` filter).
* `GET /api/decks/:deckId` → Get details of a deck (cards included).
* `PUT /api/decks/:deckId` → Update deck (name, description, tags, visibility).
* `DELETE /api/decks/:deckId` → Delete deck.

---

### Card

* `POST /api/decks/:deckId/cards` → Add new card to deck.
* `GET /api/decks/:deckId/cards` → List all cards in a deck.
* `GET /api/decks/:deckId/cards/:cardId` → Get single card.
* `PUT /api/decks/:deckId/cards/:cardId` → Update card (question, answer, media, isBidirectional).
* `DELETE /api/decks/:deckId/cards/:cardId` → Delete card.

---

### Revision (uses **CardProgress**)

* `POST /api/decks/:deckId/revision/start` → Start revision session.
* `POST /api/decks/:deckId/revision/:cardId/answer` → Submit confidence (`got_it | almost | again`) → updates **CardProgress**.
* `GET /api/decks/:deckId/revision/next` → Get next card in sequence.
* `GET /api/decks/:deckId/revision/progress` → Get progress summary for this deck.
* `GET /api/revision/history` → Retrieve past sessions and stats.

---

## **Phase 2: Multimedia + Enhancements**

### Card Media

* `POST /api/decks/:deckId/cards/:cardId/media` → Upload image/audio/video.
* `GET /api/decks/:deckId/cards/:cardId/media` → Fetch attached media.
* `DELETE /api/decks/:deckId/cards/:cardId/media` → Remove media.

---

## **Phase 3: Multi-User + Sharing**

### User Management

* `GET /api/users` → (Admin only) list all users.
* `PUT /api/users/:userId` → Update user profile/preferences.
* `DELETE /api/users/:userId` → Delete user.
* `GET /api/user/me` → Get my profile (via token).

---

### Collections (Groups of Decks)

* `POST /api/collections` → Create collection.
* `GET /api/collections` → List all collections.
* `GET /api/collections/:collectionId` → Get collection details.
* `POST /api/collections/:collectionId/decks/:deckId` → Add deck to collection.
* `GET /api/collections/:collectionId/decks` → List decks in collection.
* `DELETE /api/collections/:collectionId/decks/:deckId` → Remove deck.

---

### Sharing

* `POST /api/decks/:deckId/share` → Share deck with another user.
* `PUT /api/decks/:deckId/share/:userId` → Update sharing permission (`view | edit`).
* `DELETE /api/decks/:deckId/share/:userId` → Revoke sharing.
* `POST /api/collections/:collectionId/share` → Share collection with another user.
* `GET /api/decks/shared-with-me` → Get decks shared with me.
* `GET /api/collections/shared-with-me` → Get collections shared with me.

---

## **Phase 4: Smart & AI Features**

### Smart Revision

* `GET /api/decks/:deckId/revision/schedule` → Get spaced repetition schedule for this deck (SM-2 algorithm).

### AI-Generated Cards

* `POST /api/ai/cards/generate` → Upload PDF/text → AI creates cards.
* `GET /api/ai/cards/status/:jobId` → Track job status.
* `GET /api/ai/cards/:jobId/results` → Retrieve generated cards.

---

# 📌 Mapping to Features

| Requirement                   | Endpoint(s)                                                                             | Notes                      |
| ----------------------------- | --------------------------------------------------------------------------------------- | -------------------------- |
| Deck & card creation          | `/api/decks`, `/api/decks/:deckId/cards`                                                | Core CRUD                  |
| User login/profile            | `/api/users/login`, `/api/users/:id`, `/api/users/logout`                               | Token-based from Phase 3   |
| User-specific progress        | `/api/decks/:deckId/revision/...`, `/api/revision/history`                              | Uses **CardProgress**      |
| Image/audio/video upload      | `/api/decks/:deckId/cards/:cardId/media`                                                | Multimedia support         |
| Multi-user collaboration      | `/api/decks/:deckId/share`, `/api/collections/:collectionId/share`                      | Controlled permissions     |
| Collections (groups of decks) | `/api/collections/...`                                                                  | Flexible organization      |
| Gamification & stats          | `/api/users/:id/stats`, `/api/decks/:deckId/revision/progress`                          | Streaks + XP               |
| AI card generation            | `/api/ai/cards/generate`, `/api/ai/cards/status/:jobId`, `/api/ai/cards/:jobId/results` | Async job model            |
| Smart spaced repetition       | `/api/decks/:deckId/revision/schedule`                                                  | Implements SM-2 scheduling |