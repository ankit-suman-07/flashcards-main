# 📌 Core Database Schema (PostgreSQL)

## **1. users**

Holds all user info (single-user in MVP, expands later).

| Column         | Type         | Notes                                 |
| -------------- | ------------ | ------------------------------------- |
| user\_id (PK)  | UUID         | Primary key, `gen_random_uuid()`      |
| username       | VARCHAR(50)  | Unique username                       |
| email          | VARCHAR(100) | Unique, indexed                       |
| password\_hash | TEXT         | Store hashed password (BCrypt/Argon2) |
| full\_name     | VARCHAR(100) | Display name                          |
| created\_at    | TIMESTAMP    | Default `now()`                       |
| updated\_at    | TIMESTAMP    | Auto-updated                          |

---

## **2. decks**

Each deck belongs to a user.

| Column        | Type         | Notes                       |
| ------------- | ------------ | --------------------------- |
| deck\_id (PK) | UUID         | Primary key                 |
| user\_id (FK) | UUID         | References `users(user_id)` |
| name          | VARCHAR(100) | Deck name                   |
| description   | TEXT         | Optional                    |
| created\_at   | TIMESTAMP    | Default `now()`             |
| updated\_at   | TIMESTAMP    | Auto-updated                |
| is\_shared    | BOOLEAN      | Default `false`             |

---

## **3. cards**

Each card belongs to a deck.

| Column             | Type        | Notes                                     |
| ------------------ | ----------- | ----------------------------------------- |
| card\_id (PK)      | UUID        | Primary key                               |
| deck\_id (FK)      | UUID        | References `decks(deck_id)`               |
| question           | TEXT        | Card front                                |
| answer             | TEXT        | Card back                                 |
| difficulty\_level  | VARCHAR(20) | Enum: `easy`, `medium`, `hard` (optional) |
| confidence\_status | VARCHAR(20) | Enum: `got_it`, `almost`, `again`         |
| created\_at        | TIMESTAMP   | Default `now()`                           |
| updated\_at        | TIMESTAMP   | Auto-updated                              |

---

## **4. card\_images**

Supports multiple images per card.

| Column         | Type      | Notes                       |
| -------------- | --------- | --------------------------- |
| image\_id (PK) | UUID      | Primary key                 |
| card\_id (FK)  | UUID      | References `cards(card_id)` |
| image\_url     | TEXT      | Location in S3/Cloudinary   |
| created\_at    | TIMESTAMP | Default `now()`             |

---

## **5. playlists**

A playlist can contain many decks.

| Column            | Type         | Notes                       |
| ----------------- | ------------ | --------------------------- |
| playlist\_id (PK) | UUID         | Primary key                 |
| user\_id (FK)     | UUID         | References `users(user_id)` |
| name              | VARCHAR(100) | Playlist name               |
| description       | TEXT         | Optional                    |
| created\_at       | TIMESTAMP    | Default `now()`             |

---

## **6. playlist\_decks**

Many-to-many relation between playlists and decks.

| Column                  | Type | Notes                               |
| ----------------------- | ---- | ----------------------------------- |
| playlist\_deck\_id (PK) | UUID | Primary key                         |
| playlist\_id (FK)       | UUID | References `playlists(playlist_id)` |
| deck\_id (FK)           | UUID | References `decks(deck_id)`         |

---

## **7. revision\_sessions**

Tracks each revision session.

| Column           | Type      | Notes                       |
| ---------------- | --------- | --------------------------- |
| session\_id (PK) | UUID      | Primary key                 |
| user\_id (FK)    | UUID      | References `users(user_id)` |
| deck\_id (FK)    | UUID      | References `decks(deck_id)` |
| started\_at      | TIMESTAMP | Session start               |
| ended\_at        | TIMESTAMP | Session end (nullable)      |

---

## **8. revision\_attempts**

Logs answers for each card in a revision session.

| Column             | Type        | Notes                                        |
| ------------------ | ----------- | -------------------------------------------- |
| attempt\_id (PK)   | UUID        | Primary key                                  |
| session\_id (FK)   | UUID        | References `revision_sessions(session_id)`   |
| card\_id (FK)      | UUID        | References `cards(card_id)`                  |
| user\_answer       | TEXT        | Optional (if you want to capture user input) |
| confidence\_status | VARCHAR(20) | Enum: `got_it`, `almost`, `again`            |
| attempted\_at      | TIMESTAMP   | Default `now()`                              |

---

## **9. deck\_shares**

Sharing decks between users.

| Column                | Type        | Notes                       |
| --------------------- | ----------- | --------------------------- |
| share\_id (PK)        | UUID        | Primary key                 |
| deck\_id (FK)         | UUID        | References `decks(deck_id)` |
| owner\_id (FK)        | UUID        | References `users(user_id)` |
| shared\_with\_id (FK) | UUID        | References `users(user_id)` |
| permission            | VARCHAR(20) | Enum: `view`, `edit`        |
| created\_at           | TIMESTAMP   | Default `now()`             |

---

## **10. ai\_jobs**

For async AI-based card generation.

| Column        | Type        | Notes                                           |
| ------------- | ----------- | ----------------------------------------------- |
| job\_id (PK)  | UUID        | Primary key                                     |
| user\_id (FK) | UUID        | References `users(user_id)`                     |
| source\_type  | VARCHAR(20) | Enum: `pdf`, `text`, `webpage`                  |
| source\_url   | TEXT        | If file/web resource                            |
| status        | VARCHAR(20) | Enum: `pending`, `processing`, `done`, `failed` |
| created\_at   | TIMESTAMP   | Default `now()`                                 |
| updated\_at   | TIMESTAMP   | Auto-updated                                    |

---

# 📌 Relationships Overview

* **User → Decks → Cards → CardImages**
* **User → Playlists → PlaylistDecks (→ Decks)**
* **User → RevisionSessions → RevisionAttempts (→ Cards)**
* **User → AI Jobs → Cards (generated)**
* **Deck → Shared with other Users (deck\_shares)**

---

⚡ This schema will:

* Scale from single-user → multi-user.
* Allow tracking of **revision history** for stats.
* Support AI card generation & async jobs.
* Stay normalized (no duplicate deck–card–playlist relationships).
