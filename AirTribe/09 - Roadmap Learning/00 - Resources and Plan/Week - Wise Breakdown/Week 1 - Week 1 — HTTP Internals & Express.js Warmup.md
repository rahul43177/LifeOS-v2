## Goals for the week
> Goals for the week

* [ ] Master the end-to-end HTTP request lifecycle (DNS → TCP/IP → TLS → HTTP request → response)
* [ ] Inspect and reason about real HTTP requests with Chrome DevTools and cURL
* [ ] Build and test a minimal Express server with health, auth-guard, and basic logging
* [ ] Produce the following deliverables: `http-lifecycle.md`, `status-codes-cheatsheet.md`, and header screenshots for at least 10 requests

---
## Study checklist (core concepts)

* [ ] DNS resolution: recursive vs iterative lookup, authoritative vs recursive resolvers, A/AAAA/CNAME
* [ ] TCP handshake (3-way handshake), ports, and how TCP ensures reliable delivery
* [ ] TLS basics: certificate validation, handshake overview, and why HTTPS matters
* [ ] HTTP message structure: start-line, headers, body; difference between request and response
* [ ] Methods semantics: idempotency vs safety; use-cases for GET/POST/PUT/PATCH/DELETE/OPTIONS/HEAD
* [ ] Common headers and their purposes: `Host`, `User-Agent`, `Accept`, `Authorization`, `Content-Type`, `Cache-Control`, `ETag`, `If-None-Match`, `Cookie`, `Set-Cookie`
* [ ] Status codes: quick classification (1xx, 2xx, 3xx, 4xx, 5xx) and when to use each
* [ ] CORS basics: preflight, `Access-Control-*` headers, and why browsers block cross-origin requests
* [ ] Caching primitives: `Cache-Control`, `Expires`, `ETag`, and `Vary`
* [ ] Idempotency and safe operations: which methods must be retried safely and how to design idempotent APIs

---

## Resources (quick list to embed in notes)

* MDN: HTTP Overview — [https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
* Express docs — [https://expressjs.com/en/starter/installing.html](https://expressjs.com/en/starter/installing.html)
* HTTP Crash Course (video) — Traversy Media
* cURL cheat sheet — include common commands in `http-lifecycle.md`

---

## Hands-on tasks (priority order)

* [ ] Task A — Chrome DevTools exploration

  * Open three different websites (one public app, one API-driven page, one single-page app).
  * Record screenshots of the network tab showing: request headers, response headers, timing waterfall.
  * Save at least 10 request screenshots inside `devtools-screenshots/` and link them in notes.

* [ ] Task B — cURL practice

  * Make requests demonstrating: GET, POST (JSON), PUT, DELETE, OPTIONS, HEAD.
  * Practice sending custom headers and observing responses.
  * Save a small `curl-examples.md` with 8–10 reproducible commands.

* [ ] Task C — Minimal Express server

  * Implement a minimal Express app with the following endpoints:

    * `GET /health` — returns 200 + `{ "status": "ok" }`
    * `GET /time` — returns server time and request headers (for debugging)
    * `POST /echo` — accepts JSON and echoes it back (validate `Content-Type`)
  * Add logging middleware that logs: method, url, timestamp, and response time
  * Add error-handling middleware that sends `{ error: <message> }` with proper status
  * Run locally and test with Postman/cURL

* [ ] Task D — Document lifecycle

  * Produce `http-lifecycle.md` with a clear diagram (ASCII or image) and step-by-step notes covering DNS → TCP → TLS → HTTP exchange and what happens in the browser vs server.

* [ ] Task E — Status code cheat sheet

  * Create `status-codes-cheatsheet.md` with one-line descriptions and recommended use-cases for at least the following codes: 200, 201, 204, 301, 302, 304, 400, 401, 403, 404, 409, 422, 429, 500, 502, 503

---

## Deliverables for the week

* [ ] `http-lifecycle.md` (markdown explanation + diagram)
* [ ] `status-codes-cheatsheet.md`
* [ ] `curl-examples.md`
* [ ] `devtools-screenshots/` with 10 annotated screenshots
* [ ] `express-minimal/` basic server repo or code snippets pushed to GitHub

---

## Week 1 — Daily goals and tasks

This section is formatted as a separate daily plan that you can copy into `daily-goals-week1.md` inside your Obsidian vault. Each day contains a focused study goal, hands-on task, and a concrete deliverable.

### Day 1 — Foundations: DNS, TCP, HTTP start-line
* Study goals
  * [ ] Read about DNS resolution and recursive vs iterative lookups
  * [ ] Understand the TCP 3-way handshake and connection lifecycle
  * [ ] Read the HTTP message start-line format (request-line and status-line)

* Hands-on
  * [ ] Run `dig +trace example.com` (or `nslookup`) and capture output
  * [ ] Use `tcpdump` or Wireshark (optional) for a local TCP handshake capture, or use browser DevTools to inspect TCP timings

* Deliverable
  * [ ] Save `day1-notes.md` with captured `dig` output and one paragraph summarizing the TCP handshake

### Day 2 — TLS & HTTPS, Certificates

* Study goals
  * [ ] Read a short TLS handshake summary (client hello → server hello → certificate verification)
  * [ ] Learn where certificates are stored in the browser and how to view them

* Hands-on
  * [ ] In Chrome, view certificate information for `https://github.com` and take a screenshot of the certificate details
  * [ ] Use `openssl s_client -connect example.com:443 -showcerts` to view the server certificate chain

* Deliverable
  * [ ] `day2-notes.md` with screenshot + `openssl` output and 3 bullet points on certificate chain

### Day 3 — HTTP headers deep dive

* Study goals

  * [ ] Read about important request and response headers: `Host`, `Accept`, `User-Agent`, `Authorization`, `Content-Type`, `Cache-Control`, `ETag`, `If-None-Match`, `Set-Cookie`

* Hands-on

  * [ ] Use DevTools to capture 5 requests and annotate which headers are present and why
  * [ ] Practice `curl -I` and `curl -v` on a public URL and note differences

* Deliverable

  * [ ] `day3-notes.md` summarizing headers and attaching 5 request screenshots

### Day 4 — Methods, idempotency, and caching basics

* Study goals

  * [ ] Learn idempotent vs safe operations and why HTTP defines them
  * [ ] Read caching directives (`Cache-Control`, `Expires`, `ETag`)

* Hands-on

  * [ ] Implement two small endpoints in Express: one `GET /resource` (cacheable) and one `POST /resource` (non-cacheable)
  * [ ] Use `curl` to demonstrate `ETag` and conditional request with `If-None-Match`

* Deliverable

  * [ ] `day4-notes.md` with code snippets and curl output demonstrating 304 Not Modified

### Day 5 — Chrome DevTools practice + cURL mastery

* Study goals

  * [ ] Master Network tab filters, `Timing`, and `Headers` panels
  * [ ] Learn `curl` flags: `-X`, `-H`, `-d`, `-I`, `-v`, `--compressed`

* Hands-on

  * [ ] Capture 10 distinct requests (mix static assets, XHR, and API calls). Annotate type, cache headers, and timings.
  * [ ] Create `curl-examples.md` with 8 useful commands you can reuse

* Deliverable

  * [ ] `devtools-screenshots/` updated; `curl-examples.md` committed

### Day 6 — Minimal Express server day

* Study goals

  * [ ] Understand Express middleware ordering and the role of `next()`
  * [ ] Learn how to structure a small Express app (routes, controllers, middleware)

* Hands-on

  * [ ] Build and run `express-minimal` with endpoints: `/health`, `/time`, and `/echo`
  * [ ] Add a simple logging middleware (method, url, start time, response time)
  * [ ] Add an error handler and test by throwing an error inside a route

* Deliverable

  * [ ] Push the repo or save code snippets as `express-minimal/` and `day6-notes.md` with run commands

### Day 7 — Documentation day + synthesis

* Study goals

  * [ ] Review all notes from days 1–6
  * [ ] Create a short, final version of `http-lifecycle.md` synthesising the week

* Hands-on

  * [ ] Produce final versions of `http-lifecycle.md` and `status-codes-cheatsheet.md`
  * [ ] Ensure all screenshots and code snippets are linked from the weekly index note

* Deliverable

  * [ ] `http-lifecycle.md`, `status-codes-cheatsheet.md`, and a weekly checklist that marks all tasks complete

---

## Suggested templates (copy into each day file)

```
# Day X — Title

## Study notes
-

## Commands / snippets
-

## Observations / takeaways
-

## Deliverables
- [ ]
```

---

## Tips for efficient learning (practical)

* Always run `EXPLAIN ANALYZE` when you start touching databases (Week 2) — but get comfortable with HTTP first.
* When you capture headers/screenshots, add a one-line comment explaining why that header is present.
* For all Express code, add a `README.md` describing how to run the app and the endpoints.

---

## Next steps (after Week 1 completes)

* Run a short retrospective: what surprised you? What felt unclear?
* Add two focused tasks for Week 2: design schema for Todo API and create initial migration SQL.

---

End of Week 1 Obsidian notes (copy this file into your vault and split files as suggested).
