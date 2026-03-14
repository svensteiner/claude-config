Create a commit, push to remote, and open a pull request.

Steps:
1. Run `git status` and `git diff` to review all changes
2. Stage and commit changes with clear message
3. Push to remote with `git push -u origin <branch>`
4. Create PR using `gh pr create`

PR format:
```
gh pr create --title "Title here" --body "$(cat <<'EOF'
## Summary
- Brief description of changes

## Test plan
- [ ] How to test this

🤖 Generated with [Claude Code](https://claude.com/claude-code)
EOF
)"
```

Return the PR URL when done.
