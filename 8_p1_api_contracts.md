# 📌 API Contracts – Flashcard App (Phase 1)

---

## 1. **Users**

(for Phase 1 you may skip login, but let’s add at least signup/login for later multi-user support)

### `POST /users/signup`

**Purpose:** Register a new user

**Request:**

```json
{
  "username": "john123",
  "email": "john@example.com",
  "password": "securePass123"
}
```

**Response:**

```json
{
  "id": 1,
  "username": "john123",
  "email": "john@example.com",
  "createdAt": "2025-08-29T10:00:00Z"
}
```

---

### `POST /users/login`

**Purpose:** User login and receive token

**Request:**

```json
{
  "email": "john@example.com",
  "password": "securePass123"
}
```

**Response:**

```json
{
  "token": "jwt.token.value",
  "user": {
    "id": 1,
    "username": "john123",
    "email": "john@example.com"
  }
}
```

---

## 2. **Decks**

### `POST /decks`

**Purpose:** Create a new deck

**Request:**

```json
{
  "name": "Biology Deck",
  "description": "Basic biology flashcards"
}
```

**Response:**

```json
{
  "id": 1,
  "name": "Biology Deck",
  "description": "Basic biology flashcards",
  "cards": [],
  "createdAt": "2025-08-29T10:00:00Z"
}
```

---

### `GET /decks`

**Purpose:** List all decks of the logged-in user

**Response:**

```json
[
  {
    "id": 1,
    "name": "Biology Deck",
    "description": "Basic biology flashcards",
    "cardCount": 15
  },
  {
    "id": 2,
    "name": "Math Formulas",
    "description": "Important math formulas",
    "cardCount": 10
  }
]
```

---

### `GET /decks/{deckId}`

**Purpose:** Get details of one deck + its cards

**Response:**

```json
{
  "id": 1,
  "name": "Biology Deck",
  "description": "Basic biology flashcards",
  "cards": [
    { "id": 101, "front": "Cell is the ___", "back": "Basic unit of life", "status": "new" },
    { "id": 102, "front": "Mitochondria is the ___", "back": "Powerhouse of the cell", "status": "new" }
  ]
}
```

---

### `DELETE /decks/{deckId}`

**Purpose:** Delete a deck

**Response:**

```json
{
  "message": "Deck deleted successfully"
}
```

---

## 3. **Cards**

### `POST /decks/{deckId}/cards`

**Purpose:** Add a new card to a deck

**Request:**

```json
{
  "front": "What is photosynthesis?",
  "back": "Process by which green plants make food using sunlight",
  "tags": ["biology", "plants"]
}
```

**Response:**

```json
{
  "id": 201,
  "front": "What is photosynthesis?",
  "back": "Process by which green plants make food using sunlight",
  "tags": ["biology", "plants"],
  "status": "new"
}
```

---

### `GET /decks/{deckId}/cards/{cardId}`

**Purpose:** Fetch single card

**Response:**

```json
{
  "id": 201,
  "front": "What is photosynthesis?",
  "back": "Process by which green plants make food using sunlight",
  "tags": ["biology", "plants"],
  "status": "new"
}
```

---

### `PATCH /decks/{deckId}/cards/{cardId}`

**Purpose:** Update card details

**Request:**

```json
{
  "front": "Photosynthesis occurs in ___?",
  "back": "Chloroplasts"
}
```

**Response:**

```json
{
  "id": 201,
  "front": "Photosynthesis occurs in ___?",
  "back": "Chloroplasts",
  "tags": ["biology", "plants"],
  "status": "new"
}
```

---

### `DELETE /decks/{deckId}/cards/{cardId}`

**Purpose:** Delete a card

**Response:**

```json
{
  "message": "Card deleted successfully"
}
```

---

## 4. **Revision Mode**

### `GET /decks/{deckId}/revision`

**Purpose:** Start revision session → return first card

**Response:**

```json
{
  "sessionId": "rev-abc123",
  "deckId": 1,
  "currentCard": {
    "id": 101,
    "front": "Cell is the ___",
    "back": null,
    "status": "new"
  }
}
```

---

### `POST /revision/{sessionId}/answer`

**Purpose:** Submit answer and get next card (simulate flashcard flipping + status update)

**Request:**

```json
{
  "cardId": 101,
  "userAnswer": "Basic unit of life",
  "result": "got-it" // "got-it", "almost", "again"
}
```

**Response:**

```json
{
  "updatedCard": {
    "id": 101,
    "front": "Cell is the ___",
    "back": "Basic unit of life",
    "status": "got-it"
  },
  "nextCard": {
    "id": 102,
    "front": "Mitochondria is the ___",
    "back": null,
    "status": "new"
  }
}
```

---

## 5. **Playlists (Optional for Phase 1)**

If you want multiple decks grouped together for revision:

### `POST /playlists`

```json
{
  "name": "Final Exam Prep",
  "deckIds": [1, 2, 3]
}
```

**Response:**

```json
{
  "id": 301,
  "name": "Final Exam Prep",
  "deckIds": [1, 2, 3]
}
```