
---
# Month 01 — Backend Engineering Core (Hybrid Plan)
> “Understand the web deeply, and build production-level systems.”

---

## Month Goals
- [ ] Master the HTTP protocol — not just what it does, but how it works  
- [ ] Build production-grade Express.js APIs with proper structure and security  
- [ ] Gain SQL and schema design mastery using PostgreSQL  
- [ ] Learn authentication, middleware, and logging  
- [ ] Understand caching, async behavior, and system scalability  
- [ ] Maintain a consistent DSA practice habit  
- [ ] Build & deploy **2 real projects**: Todo API (Postgres + Auth) & URL Shortener  

---

## Success Metrics
- [ ] Can explain full HTTP lifecycle (DNS → TCP/IP → request → response)  
- [ ] Can build a secure REST API with JWT, middleware, and proper logging  
- [ ] Can design a relational schema with indexes and constraints  
- [ ] Can integrate Redis caching into an API  
- [ ] Can solve 2 medium DSA problems in 45 minutes  
- [ ] Have 2 deployed APIs with README + documentation  

---

# Week 1 – HTTP Internals + Express.js Warmup

**🎯 Goal:** Build intuition for web request lifecycles, then code an API aligned with that understanding.

###  Study
- [ ] Learn **DNS → TCP/IP → HTTP request/response** flow  
- [ ] Understand **headers, cookies, and caching directives**  
- [ ] Study **HTTP methods** (GET, POST, PUT, PATCH, DELETE, OPTIONS, HEAD)  
- [ ] Review **HTTP status codes** (200, 201, 204, 301, 400, 401, 403, 404, 500)  
- [ ] Learn **idempotency** and **statelessness** in REST APIs  
- [ ] Explore **Chrome DevTools → Network Tab** for live request debugging  
- [ ] Practice cURL commands  

### Resources
* [MDN - HTTP Overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
* [*HTTP: The Definitive Guide* ](https://dl.ebooksworld.ir/books/HTTP.The.Definitive.Guide.Brian.Totty.David.Gourley.OReilly.9781565925090.EBooksWorld.ir.pdf)— Chapters 1–3
* [Traversy Media - HTTP Crash Course](https://www.youtube.com/watch?v=iYM2zFP3Zn0)
* [Express.js Docs](https://expressjs.com/en/starter/installing.html)

### Hands-on
* [x] Analyse 10 website requests via Chrome DevTools
* [x] Build first minimal **Express server** with `/health` route
* [ ] Document request/response lifecycle with diagrams

### Deliverables
* [ ] `http-lifecycle.md` — written explanation in your words
* [ ] `status-codes-cheatsheet.md` — quick reference
* [ ] Screenshots of analysed headers

### Week Wise Plan 
[[../Week - Wise Breakdown/Week 1 - Week 1 — HTTP Internals & Express.js Warmup|Week 1 - Week 1 — HTTP Internals & Express.js Warmup]]


---

# Week 2 – Database Design + SQL (PostgreSQL Focus)

**🎯 Goal:** Learn to design schemas, model relationships, and query efficiently.

### Study

* [ ] Understand **RDBMS**, **ACID**, **Normalization (1NF–3NF)**
* [ ] Learn **Joins** (INNER, LEFT, RIGHT, CROSS)
* [ ] Understand **indexes**, **constraints**, and **transactions**
* [ ] Explore **denormalization** and query optimization (`EXPLAIN ANALYZE`)
* [ ] Learn **connection pooling** with Node.js (`pg` or Prisma)

### Resources

* [PostgreSQL Tutorial](https://www.postgresqltutorial.com/)
* *Designing Data-Intensive Applications* — Chapters 1–3
* [SQL Crash Course – Traversy Media](https://www.youtube.com/watch?v=HXV3zeQKqGY)
* [SQLBolt - Interactive SQL Practice](https://sqlbolt.com/)

### Hands-on

* [ ] Design a **User-Todo relational schema**
* [ ] Write SQL for CRUD, pagination (`LIMIT`, `OFFSET`), and joins
* [ ] Connect Node.js API to Postgres using `pg` module
* [ ] Test database queries via Postman

### Deliverables

* [ ] ER Diagram (User ↔ Todo relationship)
* [ ] `Todo API v2` using Postgres
* [ ] SQL queries + notes in `database-notes.md`

---

# Week 3 – Authentication, Middleware & Logging

**🎯 Goal:** Add production-level security, validation, and observability.

### Study

* [ ] Understand **JWT-based authentication**
	* [ ] Learn JTW Token authentication 
	* [ ] Learn OAuth 
* [ ] Learn **bcrypt** for password hashing
* [ ] Study **Express middleware flow** (`app.use`, `next()`)
* [ ] Build custom middleware for:
  * Auth check
  * Error handling
  * Request logging
* [ ] Learn `.env` and environment variable management
* [ ] Implement validation (`express-validator` / `zod`)

### Resources

* [Auth0 – JWT in Node.js](https://auth0.com/blog/building-modern-apps-with-jwt/)
* [Express Middleware Guide](https://expressjs.com/en/guide/using-middleware.html)
* NPM:

  * [`bcryptjs`](https://www.npmjs.com/package/bcryptjs)
  * [`jsonwebtoken`](https://www.npmjs.com/package/jsonwebtoken)
  * [`winston`](https://www.npmjs.com/package/winston)
  * [`express-validator`](https://www.npmjs.com/package/express-validator)

### Hands-on

* [ ] Add `authMiddleware` to protect routes
* [ ] Use `Winston` to log all requests (method, URL, status)
* [ ] Add `.env` for config management
* [ ] Refactor folder structure: routes / controllers / middleware

### Deliverables

* [ ] Secure `Todo API v3`
* [ ] Auth flow diagram
* [ ] `middleware-notes.md` with examples

---

# Week 4 – Async, Caching & System Design Intro

**🎯 Goal:** Optimize performance and learn how scalable systems behave.

### Study

* [ ] Deepen understanding of **Event Loop**, **Promises**, **async/await**
* [ ] Learn **Redis caching fundamentals** (SET, GET, TTL)
* [ ] Understand **cache invalidation** and **lazy loading**
* [ ] Learn basics of **Horizontal vs Vertical Scaling**, **Load Balancers**
* [ ] SQL vs NoSQL differences
* [ ] CDN + latency reduction basics

### Resources

* [Redis Crash Course – Traversy Media](https://www.youtube.com/watch?v=Hbt56gFj998)
* [System Design Primer – GitHub](https://github.com/donnemartin/system-design-primer)
* [Neetcode.io System Design Notes](https://neetcode.io/)
* [Node.js Async Docs](https://nodejs.org/en/docs/guides/blocking-vs-non-blocking/)

### Hands-on

* [ ] Integrate **Redis caching** into Todo API
* [ ] Implement **URL Shortener** project (Postgres + Redis)
* [ ] Deploy one API (Render / Railway / Vercel)
* [ ] Document API endpoints + caching logic

### Deliverables

* [ ] `URL Shortener` repo + deployed link
* [ ] `Caching-Notes.md` (cache invalidation strategy)
* [ ] Screenshot of deployed API

---

# DSA Plan (Throughout Month)

**🎯 Goal:** Build daily consistency and pattern recognition.

### Focus Patterns

* Arrays, Strings, HashMaps
* Sliding Window, Two Pointers
* Stack & Queue based problems

### Schedule

* [ ] 2 problems/day (Easy → Medium)
* [ ] 1 review/day from previous topic
* [ ] Weekly reflection: what pattern was repeated?

### Resources

* [Neetcode.io Patterns](https://neetcode.io/)
* Striver’s A2Z DSA Sheet
* [LeetCode Study Plan – Arrays & Strings](https://leetcode.com/study-plan/)

### Deliverables

* [ ] `DSA Tracker` (Topic, Problem, Time, Space)
* [ ] 25–30 problems completed
* [ ] Reflection: “What patterns am I recognizing now?”

---

# End-of-Month Deliverables Summary

| Category           | Deliverable                               |
| ------------------ | ----------------------------------------- |
| **HTTP Internals** | Lifecycle notes + status code cheat sheet |
| **Database**       | Todo API (Postgres) + schema diagram      |
| **Security**       | JWT Auth + middleware logs                |
| **Caching**        | Redis-integrated Todo API                 |
| **System Design**  | URL Shortener project                     |
| **Deployment**     | One live API (Render/Railway)             |
| **DSA**            | 25–30 problems + tracker sheet            |
| **Documentation**  | Organized notes in Obsidian per topic     |

---

# Folder Structure Suggestion (for Obsidian)

AirTribe / Roadmap / Month 01 - Backend Engineering Core
│
├── Week 01 - HTTP & Express
│   ├── http-lifecycle.md
│   ├── status-codes-cheatsheet.md
│
├── Week 02 - Database & SQL
│   ├── database-notes.md
│   ├── Todo API v2.md
│
├── Week 03 - Auth & Middleware
│   ├── middleware-notes.md
│   ├── Auth flow diagram.png
│
├── Week 04 - Async & Caching
│   ├── caching-notes.md
│   ├── URL Shortener.md
│
├── DSA
│   ├── DSA Tracker.md
│   ├── Reflections.md
│
└── Monthly Summary.md

---

# End-of-Month Reflection Prompts

* What new mental model did I build about backend systems?
* Which bug or debug session taught me the most?
* Which part of my API feels “production-grade” now?
* What should I improve next month (architecture, DSA, or scaling)?

---
 **Remember:**

> “A great backend engineer isn’t the one who writes APIs fastest — it’s the one who *understands every layer* of how a request travels, how data is stored, and how the system behaves under stress.”

Keep this pace, Rahul — by the end of this month, you won’t just “know Node,”
you’ll **think like a backend architect.** 🧠💪
