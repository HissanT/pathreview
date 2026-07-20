## Week 7 — Issue selection

**Issue link:** https://github.com/jamjamgobambam/pathreview/issues/43

**Issue title:** Agent session state is not cleared between reviews for the same user

**Tier:** [X] Tier 1  [ ] Tier 2  [ ] Tier 3

**Selection notes:** I chose Tier 1 because this is my first open-source contribution. The issue is focused on the session store, the expected behavior is clear, and the scope feels manageable within the estimated time.

**Problem summary:**
`session_store.py` currently caches agent state using only the user ID, allowing tool results to outlive the review that produced them. When the same user updates their portfolio and requests another review, the orchestrator reuses stale cached results instead of running the tools against the updated content. This can produce feedback based on the user's previous portfolio state and makes repeat reviews unreliable. The fix should clear or scope cached state at review boundaries so each new review recomputes its tool results while state remains reusable within a single review.

**Branch name:** `fix/43-uncleared-session-state`

**Setup confirmation:** [X] App runs locally at localhost:5173

**Cohort ledger:** [X] Issue added to cohort ledger
