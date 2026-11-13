# Hotel Booking API Tests (Postman)

Beginner API testing project against the public RESTful Booker API,
simulating a hotel-booking domain. Focus: functional + negative tests
and request chaining.

## API Under Test
- Base URL: https://restful-booker.herokuapp.com
- Public practice API (no real data)

## What is tested
| # | Request | Type | Chaining |
|---|---------|------|----------|
| 01 | GET /ping | Health check | – |
| 02 | POST /auth | Auth (positive) | Saves `token` |
| 03 | POST /booking | Create (positive) | Saves `bookingId` |
| 04 | GET /booking/:id | Read (uses `bookingId`) | Consumes `bookingId` |
| 05 | PUT /booking/:id | Update (uses `token`) | Consumes `token` |
| 05b | PUT /booking/:id (no auth) | Negative auth | Expect 403 |
| 06 | DELETE /booking/:id | Cleanup + verify deletion | Consumes both |

## Chaining demonstrated
1. **Token chaining** — POST /auth → `token` → used in PUT/DELETE headers.
2. **ID chaining** — POST /booking → `bookingid` → used in GET/PUT/DELETE URLs.
3. **Nested chaining** — inside DELETE, `pm.sendRequest` GETs the booking and asserts 404.

## Collection variables
- `baseUrl` — API base URL
- `token` — populated at runtime by request 02
- `bookingId` — populated at runtime by request 03


## Screenshots
See `screenshots/All-Tests_passed.png`.

## Skills demonstrated
Postman · REST API testing · Assertions (`pm.test`, `pm.expect`) ·
Request chaining · Collection & environment variables · Positive &
negative testing · Status code validation · Response body validation ·
Basic non-functional check (response time) · GitHub project structure
