# 1:1 external fork PR approval TOCTOU reproduction

This repository is used as a public GitHub reproduction target.

Roles:

- Maintainer account: repository owner.
- External contributor account: separate GitHub account with no collaborator access.

Expected sequence:

1. Maintainer creates a public repository and protects `main`.
2. External contributor forks the repository.
3. External contributor opens a fork PR with benign content.
4. Maintainer approves the benign revision.
5. External contributor pushes a second commit to the fork PR branch.
6. The PR is queried to check whether the old approval still satisfies the gate.
7. Maintainer merges the PR and verifies that `main` contains the second commit.

test