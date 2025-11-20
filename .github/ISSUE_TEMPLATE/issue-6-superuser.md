---
name: "Issue 6 – User Management: Create Superuser"
about: "Run Django system check and create a local superuser"
title: "Issue 6 – User Management: Create Superuser"
labels: ["issue-6"]
assignees: ""
---

## 🎯 Goal

Make sure your Django project is healthy, then create an admin superuser and log into the Django admin site.

By the end of this Issue, you will be able to:

- Run Django system checks.
- Log into `/admin/` with a superuser.
- (Optionally) manage your model through the admin.

---

## ✅ Tasks

### 1. Run Django system checks

From your terminal:

```bash
python manage.py check
```

If there are any errors, fix them before continuing (the error messages will usually tell you which file and setting are involved).

---

### 2. Register your model with the admin (optional but recommended)

Open `<app_name>/admin.py` and register your model, for example:

```python
from django.contrib import admin
from .models import Item  # or your model name

admin.site.register(Item)
```

This allows you to manage your model instances through the admin interface.

---

### 3. Create a superuser account

Run:

```bash
python manage.py createsuperuser
```

Django will ask you for:

- Username
- Email (optional)
- Password (twice)

Choose something you will remember. This account will be local to your machine.

---

### 4. Test the admin site

Start the development server:

```bash
python manage.py runserver
```

Visit:

- `http://127.0.0.1:8000/admin/`

Log in using the superuser credentials you just created.

You should see the Django admin dashboard.  
If you registered your model, you should also see it listed and be able to add/edit/delete records.

---

## 🤖 What CI will check

For branches starting with `issue-6-`, CI will:

- Re-run checks for Issues 1–5.
- Run:

  ```bash
  python manage.py check
  ```

If there is a configuration or import error, CI will fail and tell you that the system check did not pass.

CI **does not** create the superuser for you; that part is done locally on your machine.

---

## 💾 Git & GitHub Workflow (Step-by-step)

1. **Create a branch** (must start with `issue-6-`):

   ```bash
   git checkout -b issue-6-superuser
   ```

2. **Check what changed:**

   ```bash
   git status
   ```

3. **Stage your changes** (for example, if you registered models in `admin.py` or fixed settings):

   ```bash
   git add .
   ```

   You can be more specific if you prefer (e.g. `git add <app_name>/admin.py`).

4. **Commit your work:**

   ```bash
   git commit -m "Prepare project for superuser creation and admin"
   ```

5. **Push your branch:**

   ```bash
   git push -u origin issue-6-superuser
   ```

6. **Open a Pull Request targeting `main`** on GitHub.

7. **Wait for CI**:

   - If CI fails on `python manage.py check`, read the error and fix the underlying issue.
   - Commit and push again to re-run CI.

8. **Merge when CI is green ✅** and close this Issue.

After this, you will have:

- A fully working Django project.
- A custom app registered in `INSTALLED_APPS`.
- A homepage that displays data from the database using a template.
- A defined model and working migrations.
- A Django admin site with a superuser account.

🎉 You have completed the Django Setup Quest!
