# Wagtail-Project-Checklist

A plan for starting new Wagtail CMS projects.

---

## Table of Contents
- [Git Setup](#git-setup)
- [Virtual Environment](#virtual-environment)
- [Deployment](#deployment)

---

## Git Setup

- Create a new directory for the project
```bash
$ mkdir New-Project
```

- Initialize the repository and check the git config. 
- Make sure your name and email are spelled correctly.

```bash
$ git init
$ git config --list
```

- Create a development branch named dev.
```bash
$ git checkout -b dev
```
- Create a gitignore or copy the gitignore template.

---

## Virtual Environment 

```bash
$ python -m venv venv
```

```bash
bash

$ source venv/bin/activate
```
```powershell
powershell

$ venv\Scripts\Activate.ps1
```

---

## Deployment
Deployment checklist
