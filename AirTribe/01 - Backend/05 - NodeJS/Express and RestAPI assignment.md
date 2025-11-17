## Assignment: “Mini Course API”

### Functional Requirements

#### 1. **GET /courses**
* Returns all the courses.
* If a query parameter `category` is provided (e.g. `/courses?category=backend`), return only those courses in that category.

Example response:

```json
[
  { "id": 1, "name": "Node.js Basics", "category": "backend" },
  { "id": 2, "name": "React for Beginners", "category": "frontend" }
]
```

---

#### 2. **GET /courses/:id**

* Returns a single course by its `id`.
* If no course is found, return `404` with a message like `"Course not found"`.

---

#### 3. **POST /courses**

* Adds a new course.
* You’ll need to accept JSON input (so use `express.json()`).
* Example request body:

  ```json
  { "name": "FastAPI for Beginners", "category": "backend" }
  ```
* The new course should get an auto-incremented `id`.

---

#### 4. **PUT /courses/:id**

* Updates the name or category of a course by ID.

---

#### 5. **DELETE /courses/:id**

* Deletes a course by ID.
* Respond with a confirmation message or `404` if not found.

---

### Bonus (Optional, if you feel confident)

Add an **extra endpoint**:

#### `GET /courses/search?keyword=node`

* Returns all courses whose names include the keyword (case insensitive).

--- 
[[Solution - Express and RestAPI assignment ]]