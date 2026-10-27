# Coding Practice Plan (started 2026-09-01)

## The one rule
**Timer on. AI off.** Plain editor (VS Code with Copilot disabled, or Notepad on purpose).
AI is only allowed AFTER the timer ends — for review, never for writing.

## Why (Honeywell, 2026-09-02)
Cleared theory easily, could not prototype a React chat UI in 20-30 min. Rejected in round 1.
Diagnosis: 8-9 days of AI-assisted building = strong architecture vocabulary, zero unassisted
typing fluency. Both DSA and dev code affected. Fix = daily reps, not more theory.

## Daily structure (60-90 min/day, 6 days/week)
1. **DSA (30-40 min):** 1 problem in JavaScript (fluency first; Java later for JDs that demand it)
2. **Dev drill (30-45 min):** 1 timed build from a blank file
3. **Review (10 min):** run it, then ask Claude to review AS AN INTERVIEWER — what a reviewer
   would flag, what to do faster next time. Log time taken in LOG.md.

## Week 1-2: DSA track (JavaScript, easy -> classic patterns)
- D1-2: arrays/strings — reverse string, two sum, max subarray (Kadane)
- D3-4: hashmap/set — anagram check, first non-repeating char, group anagrams
- D5-6: two pointers — palindrome, container with most water, merge sorted arrays
- D7-8: sliding window — longest substring w/o repeats, max sum window of size k
- D9-10: stack/queue — valid parentheses, min stack
- D11-12: linked list — reverse, detect cycle, merge two lists
- D13-14: redo the 4 you were slowest at, cold

## Week 1-2: Dev-drill track (blank file, timed)
- D1-3: **Chat UI in React** (list + input + send + optimistic append + auto-scroll). Repeat until < 15 min.
- D4-5: Todo app (add/toggle/delete/filter), then again with useReducer
- D6-7: Fetch list from API with loading/error states + debounced search box
- D8-9: Infinite scroll (IntersectionObserver) — your own pagination story, in code
- D10-11: Express: GET /messages?cursor=&limit= + POST /messages, in-memory store
- D12-14: Cold redo of D1 and D8; 30 min basic SQL (JOIN, GROUP BY, index) on sqliteonline.com

## Targets
- Chat UI skeleton: < 15 min without thinking
- Any easy DSA problem: < 20 min including edge cases
- Talk out loud while coding — narration is half the interview score

## Log
Record every session in LOG.md: date | drill | time taken | what broke | one fix for next time
