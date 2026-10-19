<div align="center">
  <h1>Multi-person Collaboration Document Operation Manual</h1>
</div>

## Git Overview
Git is a distributed version control system for tracking changes and enabling collaboration. Key ideas: distributed history, snapshots (commits), branching, merging/rebasing, and conflict resolution.

### Core Ideas (brief)
- Distributed VCS: each clone contains full history.
- Snapshot/Commit: commits record project state.
- Branches: isolate work and later merge or rebase.
- Staging area: prepare changes for commit.
- Remote: GitHub/GitLab for sharing.

### Preparation
- Install Git (download installers as needed).
- Create GitHub account and set up authentication (SSH/HTTPS).
- Configure user:
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

## Collaboration Example (concise)
1. Invite collaborators
- Owner invites collaborators; invited users accept via notifications.

2. Clone repository
```bash
cd /path/to/workdir
git clone https://github.com/owner/Repo.git
cd Repo
```

3. Create branch & edit
```bash
git checkout -b feature/description
# edit files
git add file
git commit -m "Add feature description"
```

4. Push branch
```bash
git push origin feature/description
```

5. Create Pull Request
- Open a PR on GitHub, provide clear title and description, then request review.

6. Update local main
```bash
git checkout main
git pull origin main
```

7. Rebase when needed
```bash
git checkout feature/description
git fetch origin
git rebase origin/main
# resolve conflicts, then
git add resolved_file
git rebase --continue
git push --force-with-lease origin feature/description
```

8. Inspect history & diffs
```bash
git log --oneline
git log -p -- path/to/file
git diff <commitA> <commitB>
git diff <commit>^ <commit>
```

9. Push troubleshooting
- If push fails: ensure branch is up-to-date (pull/rebase), verify remote URL and credentials, check proxy settings if used.

## Best Practices
- Use consistent branch naming and descriptive commits.
- Write clear PR descriptions and run CI.
- Protect main branch and prefer reviews before merging.

This condensed README focuses on essential commands and workflows for team collaboration. All references to images in the repository's pic/ directory have been removed.
