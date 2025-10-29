# git-crypt

## What is git-crypt
`git-crypt` is a tool that lets you upload your project to GitHub while keeping some files encrypted.  
Only you or trusted users with the right key can read the real content — everyone else will see encrypted data.

---

## Why git-crypt is useful
Imagine you are working on a project and have a folder called `notes/`.  
You use multiple devices (for example your laptop and desktop), and you want to sync your work on GitHub but keep your notes private.  
`git-crypt` makes that possible automatically.

It is also useful when your team shares **API keys, passwords, or tokens**.  
Instead of sending keys manually or exposing them publicly on GitHub, you can encrypt them so only specific teammates can read them.

---

## Getting started

### 1. Initialize git-crypt
```bash
git-crypt init
