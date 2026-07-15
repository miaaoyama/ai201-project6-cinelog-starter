# PR Response Doc — CineLog Watchlist Feature

## AI Usage
I used AI tools to help me understand the existing codebase before making changes, explain unfamiliar functions, and verify that my changes followed the project's existing patterns. I verified all AI suggestions against the project code and ran the test suite after making changes.

---

## Comment 1 — Rename

**What I did:**
I renamed `save_to_watchlist()` to `add_to_watchlist()` and updated all imports and function calls to use the new name.

**How I verified:**
I searched the project to confirm there were no remaining references to `save_to_watchlist()` and ran `pytest` to ensure all tests still passed.

---

## Comment 2 — Deduplication

**What I did:**
I added duplicate checking before creating a new watchlist entry. If the user already has the film in their watchlist, the service now raises `AlreadyInWatchlistError` instead of creating a duplicate entry. I also updated the route to return an HTTP 409 Conflict response when this exception occurs.

**How I verified:**
I confirmed the duplicate-check logic was added to the service, updated the route to handle the new exception, and ran the test suite to verify that existing functionality was unaffected.

---

## Comment 3 — Missing test

**What I did:**
I added a test that verifies `FilmNotFoundError` is raised when attempting to add a film that does not exist. I followed the same testing style used in `tests/test_collection.py`.

**How I verified:**
I ran `pytest` and confirmed that all tests, including the new watchlist test, passed successfully.

---

## Comment 4 — Default visibility

**My position:**
I kept `public=True` as the default.

**Reasoning:**
CineLog is designed as a social film-tracking application, so public watchlists encourage sharing and make it easier for users to discover films through one another.

**Tradeoff acknowledged:**
Using a public default is convenient for social features, but it is less privacy-friendly. A future improvement would be allowing users to explicitly choose the visibility of their watchlist when adding items.

---

## Comment 5 — Sort order

**My position:**
I changed the watchlist to sort by **date added (newest first)** instead of alphabetical order.

**Reasoning:**
Most users are likely to want quick access to the films they recently added, making newest-first ordering more practical for everyday use.

**Engagement with reviewer's point:**
I agreed with the reviewer's suggestion because it provides a better user experience and is consistent with how the existing collection feature is organized.

---

## Comment 6 — Rebase

**What conflicted:**
To be completed after rebasing onto the updated `main` branch.

**How I resolved it:**
To be completed after rebasing.

**How I verified no conflict remains:**
To be completed after rebasing.

---

## PR Description

*To be completed after all changes are finished and the rebase is complete.*