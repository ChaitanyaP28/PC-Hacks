# GIT

## Repo

### Add files
```bash
git add .
```

### Commit changes
```bash
git commit -m "Comment"
```

### Commit to previous 
```bash
git commit --amend --no-edit
```

### Push changes
```bash
git push
```

## GIT Branch

### Checkout to a Branch
```bash
git checkout <Branch_Name>
```

### Status
```bash
git status
```

### List all Branches
```bash
git branch
```

### Create Branch
```bash
git branch <Branch_Name>
```

### Rename Branch
```bash
git branch -m <Old_Branch_Name> <New_Branch_Name>
```

If already on current branch
```bash
git branch -m <New_Branch_Name>
```

### Delete Branch
```bash
git branch -d `<Branch_Name>`
```

## GitIgnore
Create `.gitignore`
```bash
touch .gitignore
```
Edit `.gitignore`
```bash
nano .gitignore
```
Add files to `.gitignore`

`<File_Name.txt>`

Example:
```bash
config.json
```

Add folders to `.gitignore`

`<Folder_Name>`/

Example:
```bash
logs/
```

## Push to Github without commit History

```bash
git add .
git commit --amend --no-edit
git push --force-with-lease origin main
```

**Caution:** This wont give any commit points on GitHub.



