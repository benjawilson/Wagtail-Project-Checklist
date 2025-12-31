# Wagtail-Project-Checklist

A plan for starting new Wagtail CMS projects.

---

## Table of Contents
- [Git Setup](#git-setup)
- [Virtual Environment](#virtual-environment)
- [Deployment](#deployment)

---

## Git Setup
How to setup Git

Create a new directory for the project
```markdown
$ mkdir New-Project
```

Initialize the repository and check the git config. Your name and email should be spelled correctly.
```markdown
$ git init
$ git config --list
```

Create a development branch named dev.
```markdown
$ git checkout -b dev
```
Create a gitignore or copy the gitignore template.

---

## Virtual Environment 

```markdown
$ python -m venv venv
```

```bash
$ source venv/bin/activate
```

```powershell
$ venv/Scripts/activate
```

---

## Deployment
Deployment checklist
