# Git Commands and Best Practices

## Basic Git Commands

### Initialize a Repository
```bash
git init
```

### Clone a Repository
```bash
git clone <repository-url>
```

### Check Status
```bash
git status
```

### Add Files to Staging Area
```bash
git add <file-name>
git add .  # Add all changes
```

### Commit Changes
```bash
git commit -m "Your commit message"
```

### Push Changes
```bash
git push origin <branch-name>
```

### Pull Changes
```bash
git pull origin <branch-name>
```

### Create and Switch to a New Branch
```bash
git checkout -b <new-branch-name>
```

### Switch Branches
```bash
git checkout <branch-name>
```

### Merge Branches
```bash
git merge <branch-name>
```

## Advanced Git Commands

### Stash Changes
```bash
git stash
git stash pop  # Apply and remove the latest stash
git stash apply  # Apply but keep the stash
```

### Rebase
```bash
git rebase <branch-name>
```

### Cherry-pick
```bash
git cherry-pick <commit-hash>
```

### Reset
```bash
git reset --soft HEAD~1  # Undo last commit, keep changes staged
git reset --mixed HEAD~1  # Undo last commit, unstage changes
git reset --hard HEAD~1  # Undo last commit, discard changes
```

### Reflog
```bash
git reflog  # View history of HEAD changes
```

### Amend Last Commit
```bash
git commit --amend
```

### Interactive Rebase
```bash
git rebase -i HEAD~3  # Rebase last 3 commits
```

## Gitflow Workflow

Gitflow is a branching model for Git that helps manage larger projects. Here's a basic overview:

1. `main` (or `master`): Represents production-ready code
2. `develop`: Integration branch for features
3. `feature/*`: For developing new features
4. `release/*`: For preparing releases
5. `hotfix/*`: For quick fixes to production

Example workflow:

```bash
# Start a new feature
git checkout -b feature/new-feature develop

# Finish the feature
git checkout develop
git merge --no-ff feature/new-feature
git branch -d feature/new-feature

# Prepare a release
git checkout -b release/1.0.0 develop

# Finish the release
git checkout main
git merge --no-ff release/1.0.0
git tag -a 1.0.0
git checkout develop
git merge --no-ff release/1.0.0
git branch -d release/1.0.0
```

## Conventional Commits

Conventional Commits is a specification for adding human and machine-readable meaning to commit messages. Here are some common types:

- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation only changes
- `style`: Changes that do not affect the meaning of the code (white-space, formatting, etc)
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `perf`: A code change that improves performance
- `test`: Adding missing tests or correcting existing tests
- `chore`: Changes to the build process or auxiliary tools and libraries

Example commit messages:

```
feat: add user authentication
fix: resolve memory leak in data processing
docs: update API documentation
style: format code according to style guide
refactor: simplify login process
perf: optimize database queries
test: add unit tests for user model
chore: update dependencies
```

These commit types help in generating changelogs and determining semantic version bumps automatically.
