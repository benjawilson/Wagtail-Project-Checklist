# Wagtail-Project-Checklist

A plan for starting new Wagtail CMS projects.

---

## Table of Contents
- [Git Setup](#git-setup)
- [GitHub Setup](#github-setup)
- [Virtual Environment](#virtual-environment)
- [Scaffolding](#scaffolding)
- [Wagtail Setup](#wagtail-setup)
- [Deployment](#deployment)

---

## Git Setup

- Create a new directory for the project
```bash
mkdir New-Project
```

- Initialize the repository and check the git config. 
- Make sure your name and email are spelled correctly.

```bash
git init
git config --list
```

- Create a development branch named dev.
```bash
git checkout -b dev
```
- Create a .gitignore or copy the .gitignore template.

- Make the first commit.
```bash
git add .gitignore
git commit -m "Add .gitignore"
```

- Sync with GitHub

---

## GitHub Setup

- Create a repository on GitHub with the CLI.
```bash
GitHub CLI

gh auth login
gh repo create --source=. --private --push
```

--- 

## Virtual Environment 

```bash
python -m venv venv
```

```bash
bash

source venv/bin/activate
```

```powershell
powershell

venv\Scripts\Activate.ps1
```

---

## Scaffolding

- Create a .env file for secrets.
```bash
touch .env
```

- Create a requirements file for python.
```bash
touch requirements.txt 
```

---

## Wagtail Setup

- Initilize a new wagtail project in a src directory.
```bash
wagtail start NewProject src

```

---

## Deployment
Deployment checklist
