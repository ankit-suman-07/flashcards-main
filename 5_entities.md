# ✨ Entity List

### 1. **User**

* `id`
* `username`
* `email`
* `passwordHash`
* `preferences`: JSON (dark mode, notifications, etc.)
* `streakCount`, `xpPoints` (for gamification)
* `role`: enum → `user`, `admin`
* `createdAt`, `updatedAt`

---

### 2. **Deck**

* `id`
* `name`
* `description`
* `tags`: array (e.g., “biology”, “interview prep”)
* `ownerId`: FK → `User`
* `cards`: relation to `Card`
* `visibility`: enum (`private`, `shared`, `public`)
* `createdAt`, `updatedAt`

---

### 3. **Card**

* `id`
* `question`
* `answer`
* `isBidirectional`: boolean
* `mediaUrls`: array (image/audio/video)
* `hint`: optional (for AI-generated hints in Phase 4)
* `deckId`: FK → `Deck`
* `createdAt`, `updatedAt`

---

### 4. **CardProgress** (new, critical)

* `id`
* `userId`: FK → `User`
* `cardId`: FK → `Card`
* `status`: enum (`Confident`, `Doubtful`, `Read Again`)
* `lastReviewedAt`
* `nextReviewAt` (for spaced repetition schedules)
* `createdAt`, `updatedAt`

---

### 5. **Collection**

* `id`
* `name`
* `description`
* `decks`: relation to `Deck`
* `visibility`: enum (`private`, `shared`, `public`)
* `ownerId`: FK → `User`
* `createdAt`, `updatedAt`

---

### 6. *(Optional Phase 4)* **AIContent**

* `id`
* `deckId`
* `sourceFileUrl` (e.g., PDF, notes)
* `generatedCards`: JSON or relation
* `createdAt`, `updatedAt`