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

### 1. Download git-crypt
PowerShell
```PowerShell
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
irm get.scoop.sh | iex
```

### 2. instal git-crypt & gnupg
```bash
scoop install git-crypt 

```
```bash
scoop install gnupg
```

### 3. Verify git-crypt version
```bash
git-crypt --version
```

```bash
gpg --version
```

### 4. Initialization
```bash 
git-crypt init
```
### 5. Verify Initialization
```bash 
git-crypt status
```

---

### Now we must understand that there are two methods to encrypt data, and we need to distinguish between them.

### in both Method you add .gitattributes
``` bash 
touch .gitattributes

``` 

### inside .gitattributes you specify what are the fodder or file you need to encrypted is formatted by this layout


#### .gitattributes 


```gitattributes
<path>    filter=git-crypt    diff=git-crypt
```
 **Note:** You can add a folder by using `<folder-name>/*` to include only the files inside that folder, or `<folder-name>/**` to include the folder and all its subfolders.

``` bash 
<folder-name>/**  filter=git-crypt    diff=git-crypt
```
---

## First Method: Key-Based
From its name, this method is based on a key file that you must have in order to decrypt your data.
 

### 1.Initialize git-crypt

```bash 
git-crypt init

```

### 2. See status and what are encrypted
```bash
 git-crypt status
 ```
### 3. export key:
```bash
git-crypt export-key ./git-crypt.key
```
### 4. decrypt data by key
```bash 
git-crypt unlock ./git-crypt.key
```

## To be honest, this method has both advantages and disadvantages.  
It’s not always practical every time you encrypt or decrypt, you need to use the key manually.  
Yes, it’s only one command, but what if there’s an automatic way to handle that?  
Of course, you would choose the automatic one if it exists.

## Second Method: GPG key pair

### 1.Initialize git-crypt

```bash 
git-crypt init

```
### 2. See status and what are encrypted
```bash
 git-crypt status
 ```

### 3. create GPG key:
```bash
gpg --full-generate-key 
```

### 4. decrypt data by key
```bash 
git-crypt unlock  
```
### 5.list available key
```bash
gpg --list-secret-keys 
```
### 6. add new user 
```bash
git-crypt add-gpg-user <user@email.com>   
```




