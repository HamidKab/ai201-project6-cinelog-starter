# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->

## Comment 1 — Rename
**What I did:**  I asked Claude to find every reference of save_to_watchlist() and when it mapped them I changed every reference to add_to_watchlist().

**How I verified:**
I verified it by asking claude to check that save_to_watchlist() was no longer referenced and that add_to_watchlist() had replaced it. It then ran a grep on save_to_watchlist() and add_to_watchlist().

## Comment 2 — Deduplication
**What I did:** I read the logic within the collection service and applied the same logic to the add_to_watchlist()

**How I verified:** I verified this by creating a separate test case for checking for deduplication in the test suite.

## Comment 3 — Missing test
**What I did:** I looked into the testcase, test_add_to_collection_nonexistent_film_raises(), in test_collection and replicated in test_watchlist with test_add_to_watch_nonexistent_film_raises()
**How I verified:** I verified it by running the test suite and seeing if it passed or failed

## Comment 4 — Default visibility
**My position:** I believe this should be changed to False
**Reasoning:** I dont think everyone should be able to grab other users watchlist. To me I think this might be an invasion of privacy to users. There should at least be the option for users to public or private that information
**Tradeoff acknowledged:** A trade off for changing public to False would be adding more work on users to request information, but in return we would have a safer privacy default.

## Comment 5 — Sort order
**My position:** I would like it to remain in alphabetic 
**Reasoning:** Sorting by date would allow users to see what they added recently easier but it would create a mess when considering shows added further back in time. By keeping it in alphabetical order regardless of when the show was added users will be easily be able to find their shows

**Engagement with reviewer's point:** I understand that seeing the most recent adds is convenient but that convenience comes at the cost of being able to easily find shows that were added months or even years back.

## Comment 6 — Rebase
**What conflicted:** CONFLICT (content): Merge conflict in models.py. Main switched film IDs from integers to UUID string and my comment changed that same line and added index=True
**How I resolved it:**  I kept both changes in models in one line in models.py line 81
**How I verified no conflict remains:** I hit git rebase --continue to see if any conflicts remained and from there I merged changes and sucessfully rebased.

## PR Description