# 📌 Endpoints Mapping (by Entities & Features)

## **Phase 1: Single User App (MVP)**

### User (single-user, so minimal)

* `POST /api/user/register` → Create account (optional in MVP, you can hardcode a single user for testing)
* `POST /api/user/login` → Login and get session/token
* `GET /api/user/profile` → Get user details (decks, playlists, stats)

### Deck

* `POST /api/decks` → Create a new deck
* `GET /api/decks` → List all decks
* `GET /api/decks/:deckId` → Get details of a deck (cards included)
* `PUT /api/decks/:deckId` → Update deck name/description
* `DELETE /api/decks/:deckId` → Delete deck

### Card

* `POST /api/decks/:deckId/cards` → Add new card to deck
* `GET /api/decks/:deckId/cards` → List all cards in a deck
* `GET /api/decks/:deckId/cards/:cardId` → Get single card
* `PUT /api/decks/:deckId/cards/:cardId` → Update card (question/answer/status)
* `DELETE /api/decks/:deckId/cards/:cardId` → Delete card

### Revision Mode (Core use-case: John revises deck)

* `POST /api/decks/:deckId/revision/start` → Start revision session
* `POST /api/decks/:deckId/revision/:cardId/answer` → Submit answer & mark confidence (`got_it | almost | again`)
* `GET /api/decks/:deckId/revision/next` → Get next card in sequence

---

## **Phase 2: Image Support for Cards**

### Card Enhancements

* `POST /api/decks/:deckId/cards/:cardId/image` → Upload image for card
* `GET /api/decks/:deckId/cards/:cardId/image` → Fetch image
* `DELETE /api/decks/:deckId/cards/:cardId/image` → Remove image

---

## **Phase 3: Multi-User + Sharing**

### User

* `GET /api/users` → (Admin only) list users
* `PUT /api/user/:userId` → Update user profile
* `DELETE /api/user/:userId` → Delete user

### Sharing

* `POST /api/decks/:deckId/share` → Share deck with another user
* `POST /api/playlists/:playlistId/share` → Share playlist with another user
* `GET /api/decks/shared-with-me` → Get decks shared with me
* `GET /api/playlists/shared-with-me` → Get playlists shared with me

---

## **Phase 4: AI Features**

### AI-Generated Cards

* `POST /api/ai/cards/generate` → Upload PDF/text, AI creates cards
* `GET /api/ai/cards/status/:jobId` → Track job status (in case async generation)

---

# 📌 Mapping to Features

| Requirement                             | Endpoint(s)                                                            | Notes                             |
| --------------------------------------- | ---------------------------------------------------------------------- | --------------------------------- |
| Create decks/cards                      | `/api/decks`, `/api/decks/:deckId/cards`                               | Core CRUD                         |
| Revision flow (Got It / Almost / Again) | `/api/decks/:deckId/revision/...`                                      | Handles spaced repetition logic   |
| Image upload                            | `/api/decks/:deckId/cards/:cardId/image`                               | Use cloud storage (S3/Cloudinary) |
| Multi-user                              | `/api/user/*`, `/api/decks/shared-with-me`, `/api/decks/:deckId/share` | Requires auth & ACLs              |
| AI card generation                      | `/api/ai/cards/generate`                                               | Can be async (queue-based)        |

---

👉 This gives a **clean separation**:

* CRUD endpoints (basic entity management)
* Revision endpoints (business logic)
* Sharing endpoints (multi-user)
* AI endpoints (extension features)