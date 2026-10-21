# Number Guessing Game (SER 316 - Assignment 1)

## Initial Branch Structure & Feature Overview
- `main`: Baseline Java number guessing game.
- `dev`: Active integration branch containing player encouragement messages.
- `feature1`: Adds ability to quit using negative numbers, a play-again loop, and improved guess feedback.
- `feature2`: Adds a 10-attempt limit (`MAX_ATTEMPTS`) and game over conditions.
- `feature3`: Adds a hint system revealing proximity after 3 failed attempts (contains 4 messy development commits).
- `hotfix`: Critical off-by-one fix in `Utils.randomInt` to include the upper boundary.

## Task 2: Git Strategy & History Analysis Summary

### 1. Differences Between Git Integration Strategies
- **Merge (`git merge`)**: Preserves the complete branch history and exact commit times. When history diverges, it generates a two-parent merge commit. Best for integrating large features into public branches where full context is required.
- **Rebase (`git rebase`)**: Re-applies commits on top of another base commit. It creates new commit hashes and linearizes the project history, avoiding "train tracks" merge commits.
- **Squash (`git rebase -i` or `merge --squash`)**: Combines multiple intermediate WIP commits into a single atomic commit. Keeps shared branches clean and readable.
- **Cherry-Pick (`git cherry-pick`)**: Copies a specific single commit by hash and applies it onto the current branch. Perfect for backporting critical bugfixes directly to `main` without pulling in unfinished features from `dev`.

### 2. Observations Across Feature Branches
- **`feature1`**: Used standard merge. Left an explicit merge commit documenting when it integrated with `dev`.
- **`feature2`**: Used rebase. History is linear, but required resolving conflicts at each commit step during the rebase.
- **`feature3`**: Used squashing followed by rebase. Reduced 4 messy WIP commits into one clear, atomic commit and required only a single conflict resolution.

### 3. Real-World Recommendations
- Use **feature branches** for isolated tasks.
- **Squash & Rebase** local feature commits before creating Pull Requests to keep upstream history clean.
- Use **Cherry-Pick** for emergency hotfixes across production and maintenance releases.
- Never rebase a public shared branch (e.g., `main` or `dev`) that teammates are actively pulling from.