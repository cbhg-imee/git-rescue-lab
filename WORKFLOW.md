# Git Rescue Lab Answers

## Task 1: Bisect Finding
- **Commit Hash:** c99fb4209e6fb6e5ed2789893fdb2f893d61d6c6
- **Explanation:** The commit changed the BULK20 item length condition from `>= 5` to `> 5`, breaking discounts for orders with exactly 5 items.

## Branching Strategy
For a 4-person team, **GitHub Flow** is ideal. Developers create short-lived feature branches off `main`, open Pull Requests for review, and merge into `main` after continuous integration tests pass. It avoids the overhead of Git Flow while keeping `main` deployable.

## Secret History Cleanup
- **Complete Removal:** I would use `git-filter-repo` or BFG Repo-Cleaner to strip `.env` from all past commit objects, force push the cleaned history, and immediately revoke/rotate the compromised credentials.
- **Why skipped here:** Cleaning history changes commit SHAs across the entire git tree, which can break existing forks/clones and is unnecessary for learning working-tree tracking fixes.

## History Rewriting Rules
- **Acceptable in Task 2:** The commit was local and unpushed; no one else had based work on it.
- **Unacceptable if shared:** Rewriting shared history breaks commit SHAs for teammates who pulled the original commits, resulting in merge conflicts and detached HEAD states when pushing/pulling.