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
python3 -m venv venv
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
pip install wagtail
mkdir src
wagtail start NewProject src

```

## Connect to Database

- Install dependencies 
```bash
pip install python-dotenv
pip install dj-database-url
```

- Create .env file at project root

```bash
cd src
vim .env
```

- Add Neon connection string to .env in double quotes
```env
DATABASE_URL="postgresql://username:password@ep-something.neon.tech/dbname?sslmode=require"
```

- Edit Wagtail settings
```bash
vim settings/base.py 
```
- Import libraries

```
import os
from pathlib import Path
from dotenv import load_dotenv
import dj_database_url

load_dotenv()
```
- Edit databases block

```
DATABASES = {
    "default": dj_database_url.parse(
        os.environ["DATABASE_URL"],
        conn_max_age=600,
        ssl_require=True,
    )
}
```
---

## Connect to R2 Bucket

- Install dependencies
```bash
pip install ...
```


- Edit media block
```
# Media / Storage (R2 if configured, else local)
R2_ACCESS_KEY_ID = os.environ.get("R2_ACCESS_KEY_ID")
R2_SECRET_ACCESS_KEY = os.environ.get("R2_SECRET_ACCESS_KEY")
R2_BUCKET_NAME = os.environ.get("R2_BUCKET_NAME")
R2_ENDPOINT_URL = os.environ.get("R2_ENDPOINT_URL")
R2_CUSTOM_DOMAIN = os.environ.get("R2_CUSTOM_DOMAIN")

USE_R2 = all([R2_ACCESS_KEY_ID, R2_SECRET_ACCESS_KEY, R2_BUCKET_NAME, R2_ENDPOINT_URL])

if USE_R2:
    AWS_ACCESS_KEY_ID = R2_ACCESS_KEY_ID
    AWS_SECRET_ACCESS_KEY = R2_SECRET_ACCESS_KEY
    AWS_STORAGE_BUCKET_NAME = R2_BUCKET_NAME
    AWS_S3_ENDPOINT_URL = R2_ENDPOINT_URL

    AWS_S3_REGION_NAME = "auto"
    AWS_S3_SIGNATURE_VERSION = "s3v4"
    AWS_DEFAULT_ACL = None
    AWS_QUERYSTRING_AUTH = False
    AWS_S3_FILE_OVERWRITE = False

    # Optional: helps some setups avoid odd redirect/host issues
    AWS_S3_ADDRESSING_STYLE = "virtual"

    # If you have a custom domain like media.example.com, use it; else use R2 public URL
    if R2_CUSTOM_DOMAIN:
        MEDIA_URL = f"https://{R2_CUSTOM_DOMAIN}/"
    else:
        MEDIA_URL = f"https://{AWS_STORAGE_BUCKET_NAME}.r2.cloudflarestorage.com/"

    STORAGES = {
        "default": {"BACKEND": "storages.backends.s3boto3.S3Boto3Storage"},
        "staticfiles": {"BACKEND": "django.contrib.staticfiles.storage.StaticFilesStorage"},
    }
else:
    MEDIA_ROOT = BASE_DIR / "media"
    MEDIA_URL = "/media/"

    STORAGES = {
        "default": {"BACKEND": "django.core.files.storage.FileSystemStorage"},
        "staticfiles": {"BACKEND": "django.contrib.staticfiles.storage.StaticFilesStorage"},
    }
```


---

## Deployment
Deployment checklist
