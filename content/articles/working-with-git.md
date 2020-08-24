---
title: Working with Git.
description: Necessary but forgotten commands.
img: https://images.unsplash.com/photo-1556075798-4825dfaaf498?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1055&q=80
alt: Git
author: 
  name: g0d13
---

## Commands

### Delete remote branch
```git[git]
git push origin --delete test
```

### Add changes to last commit
``` git[git]
# Add changes to last commit
git commit --amend
# Editing a Commit Without Opening a File
git commit --amend -m "Your new commit message"
# Add changes to last commit, without editing last message
git commit --amend --no-edit
```
