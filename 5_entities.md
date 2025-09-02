### ✅ Entities (with refinements)

#### 1. **Card**

* `id`: unique identifier (UUID or ObjectId)
* `topic` / `question`: main prompt or question
* `answer` / `explanation`: the explanation or correct answer
* `status`: enum (`Confident`, `Doubtful`, `Read Again`) — good idea for progress tracking
* `imageUrl` (optional, for Phase 2 when you allow images)

---

#### 2. **Deck**

* `id`: unique identifier
* `name`: name of the deck (e.g., “Java Basics”)
* `description`: optional, a short text about the deck
* `cards`: one-to-many relation with `Card`
* `sortingOrder`: optional (could be by date, custom order, or spaced repetition in future)

---

#### 3. **Playlist / Group**

* `id`: unique identifier
* `name`: name of the playlist (e.g., “Interview Prep”)
* `decks`: one-to-many relation with `Deck`
* (optional) `visibility`: `private`, `shared`, `public` → useful when you move to **multi-user sharing**

---

#### 4. **User**

* `id`: unique identifier
* `name`: display name / username
* `email`: better than just `name` for authentication & uniqueness
* `passwordHash`: store securely (not plain password)
* `decks`: decks created by this user
* `groups / playlists`: playlists created by this user
* (optional) `role`: `user` / `admin` (for future scalability)

---

### 🔑 Why this works well

* It’s **normalized**: Cards belong to Decks, Decks can be grouped into Playlists, and Users own Playlists/Decks.
* It’s **scalable**: Later, you can add “shared decks” or “AI-generated cards” without breaking the structure.
* It’s **job-relevant**: This schema thinking applies to both SQL (Postgres/Prisma) and NoSQL (MongoDB/Mongoose).