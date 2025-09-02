# 📌 Core Database Schema (PostgreSQL – Refined)

## **1. users**

| Column         | Type         | Notes                                  |
| -------------- | ------------ | -------------------------------------- |
| user\_id (PK)  | UUID         | Primary key, `gen_random_uuid()`       |
| username       | VARCHAR(50)  | Unique username                        |
| email          | VARCHAR(100) | Unique, indexed                        |
| password\_hash | TEXT         | Store hashed password (BCrypt/Argon2)  |
| full\_name     | VARCHAR(100) | Display name                           |
| preferences    | JSONB        | User settings (theme, reminders, etc.) |
| streak\_count  | INT          | For gamification streaks               |
| xp\_points     | INT          | Total XP earned                        |
| role           | VARCHAR(20)  | Enum: `user`, `admin`                  |
| created\_at    | TIMESTAMP    | Default `now()`                        |
| updated\_at    | TIMESTAMP    | Auto-updated                           |

---

## **2. decks**

| Column        | Type         | Notes                                    |
| ------------- | ------------ | ---------------------------------------- |
| deck\_id (PK) | UUID         | Primary key                              |
| user\_id (FK) | UUID         | References `users(user_id)` (deck owner) |
| name          | VARCHAR(100) | Deck name                                |
| description   | TEXT         | Optional                                 |
| visibility    | VARCHAR(20)  | Enum: `private`, `shared`, `public`      |
| tags          | TEXT\[]      | Array of keywords for discovery/search   |
| created\_at   | TIMESTAMP    | Default `now()`                          |
| updated\_at   | TIMESTAMP    | Auto-updated                             |

---

## **3. cards**

| Column            | Type      | Notes                                  |
| ----------------- | --------- | -------------------------------------- |
| card\_id (PK)     | UUID      | Primary key                            |
| deck\_id (FK)     | UUID      | References `decks(deck_id)`            |
| question          | TEXT      | Card front                             |
| answer            | TEXT      | Card back                              |
| is\_bidirectional | BOOLEAN   | Whether card can be flipped both ways  |
| media\_urls       | TEXT\[]   | Optional (images, audio, video links)  |
| hint              | TEXT      | Optional (AI-generated or manual hint) |
| created\_at       | TIMESTAMP | Default `now()`                        |
| updated\_at       | TIMESTAMP | Auto-updated                           |

---

## **4. card\_progress**

Tracks each user’s learning progress per card.

| Column           | Type        | Notes                                       |
| ---------------- | ----------- | ------------------------------------------- |
| progress\_id(PK) | UUID        | Primary key                                 |
| user\_id (FK)    | UUID        | References `users(user_id)`                 |
| card\_id (FK)    | UUID        | References `cards(card_id)`                 |
| status           | VARCHAR(20) | Enum: `confident`, `doubtful`, `read_again` |
| last\_reviewed   | TIMESTAMP   | Last time user reviewed this card           |
| next\_review\_at | TIMESTAMP   | When this card should appear next (SRS)     |
| review\_count    | INT         | Number of times reviewed                    |
| ease\_factor     | FLOAT       | For SM-2 spaced repetition algorithm        |

---

## **5. collections** (previously playlists/groups)

| Column             | Type         | Notes                               |
| ------------------ | ------------ | ----------------------------------- |
| collection\_id(PK) | UUID         | Primary key                         |
| user\_id (FK)      | UUID         | References `users(user_id)` (owner) |
| name               | VARCHAR(100) | Collection name                     |
| description        | TEXT         | Optional                            |
| visibility         | VARCHAR(20)  | Enum: `private`, `shared`, `public` |
| created\_at        | TIMESTAMP    | Default `now()`                     |

---

## **6. collection\_decks**

Many-to-many relation between collections and decks.

| Column                   | Type | Notes                                   |
| ------------------------ | ---- | --------------------------------------- |
| collection\_deck\_id(PK) | UUID | Primary key                             |
| collection\_id (FK)      | UUID | References `collections(collection_id)` |
| deck\_id (FK)            | UUID | References `decks(deck_id)`             |

---

## **7. revision\_sessions**

| Column          | Type      | Notes                       |
| --------------- | --------- | --------------------------- |
| session\_id(PK) | UUID      | Primary key                 |
| user\_id (FK)   | UUID      | References `users(user_id)` |
| deck\_id (FK)   | UUID      | References `decks(deck_id)` |
| started\_at     | TIMESTAMP | Session start               |
| ended\_at       | TIMESTAMP | Session end (nullable)      |

---

## **8. revision\_attempts**

Logs each card attempt in a session.

| Column          | Type        | Notes                                      |
| --------------- | ----------- | ------------------------------------------ |
| attempt\_id(PK) | UUID        | Primary key                                |
| session\_id(FK) | UUID        | References `revision_sessions(session_id)` |
| card\_id (FK)   | UUID        | References `cards(card_id)`                |
| user\_answer    | TEXT        | Optional (if user types an answer)         |
| status          | VARCHAR(20) | Enum: `confident`, `doubtful`, `again`     |
| attempted\_at   | TIMESTAMP   | Default `now()`                            |

---

## **9. deck\_shares**

| Column           | Type        | Notes                       |
| ---------------- | ----------- | --------------------------- |
| share\_id (PK)   | UUID        | Primary key                 |
| deck\_id (FK)    | UUID        | References `decks(deck_id)` |
| owner\_id (FK)   | UUID        | References `users(user_id)` |
| shared\_with\_id | UUID        | References `users(user_id)` |
| permission       | VARCHAR(20) | Enum: `view`, `edit`        |
| created\_at      | TIMESTAMP   | Default `now()`             |

---

## **10. ai\_jobs**

| Column        | Type        | Notes                                           |
| ------------- | ----------- | ----------------------------------------------- |
| job\_id (PK)  | UUID        | Primary key                                     |
| user\_id (FK) | UUID        | References `users(user_id)`                     |
| source\_type  | VARCHAR(20) | Enum: `pdf`, `text`, `webpage`                  |
| source\_url   | TEXT        | File or web resource                            |
| status        | VARCHAR(20) | Enum: `pending`, `processing`, `done`, `failed` |
| created\_at   | TIMESTAMP   | Default `now()`                                 |
| updated\_at   | TIMESTAMP   | Auto-updated                                    |

---

# 📌 Relationships Overview

* **User → Decks → Cards → CardProgress**
* **User → Collections → CollectionDecks (→ Decks)**
* **User → RevisionSessions → RevisionAttempts (→ Cards)**
* **User → AI Jobs → Cards (generated)**
* **Deck → Shared with other Users (deck\_shares)**

---

⚡ This schema now:

* Handles **per-user card progress** (research-aligned).
* Supports **multimedia, bidirectionality, and AI-generated hints**.
* Prepares for **gamification & spaced repetition algorithms**.
* Scales from MVP → advanced phases cleanly.