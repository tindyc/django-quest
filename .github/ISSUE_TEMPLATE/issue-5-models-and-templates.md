---
name: "Issue 5 – Models & Migrations"
about: "Create a Django model, run makemigrations and migrate successfully"
title: "Issue 5 – Models & Migrations"
labels: issue-5
assignees: ""
---

# 🗄 Issue 5 – Models & Migrations  

In this step you will:

- Define a simple model in your app
- Generate migrations with `makemigrations`
- Apply them with `migrate`
- Prepare data for the admin site

---

## 🔄 1. Update local `main` and create a new branch

```bash
git checkout main
git pull origin main
git checkout -b issue-5-models-and-templates
```

Activate your virtual environment if needed.

---

## 🧱 2. Add a model in `models.py`

Open your app’s `models.py`, e.g. `blog/models.py`, and add a simple model.  
Here’s an example for a blog post; adapt the names to your idea if you like:

```python
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=200)
    body = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title
```

Notes:

- `CharField` needs a `max_length`.
- `auto_now_add=True` records creation time automatically.
- `__str__` helps display objects nicely in the admin and shell.

---

## 🧪 3. Run `makemigrations`

Run:

```bash
python manage.py makemigrations
```

You should see output indicating a new migration file for your app, e.g.:

```text
Migrations for 'blog':
  blog/migrations/0001_initial.py
```

If you get errors, read them carefully — they usually point to a syntax issue in `models.py`.

---

## 🧱 4. Apply migrations with `migrate`

Run:

```bash
python manage.py migrate
```

This applies all unapplied migrations (including your new one) to the database.

---

## 🧾 5. (Optional but recommended) Register your model in `admin.py`

Open your app’s `admin.py` and register your model:

```python
from django.contrib import admin
from .models import Post

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
    list_display = ("title", "created_at")
```

If you chose a different model name, update the import and registration.

---

## 💾 6. Commit your work

```bash
git status
git add <app_name>/models.py <app_name>/migrations/ <app_name>/admin.py
git commit -m "Issue 5: Add model and run migrations"
```

---

## 🚀 7. Push your branch

```bash
git push -u origin issue-5-models-and-templates
```

---

## 🔁 8. Open a Pull Request (PR)

- Open a PR from `issue-5-models-and-templates` into `main`.
- Create the PR.

---

## 🤖 9. Wait for the Django Quest Checker (CI)

The CI will run:

- `python manage.py makemigrations --noinput`
- `python manage.py migrate --noinput`

If there’s a problem with your models, migrations, or database, CI will fail with a helpful error.

Fix, commit, and push until it goes green.

---

## 🟢 10. Merge the PR & close this Issue

Once CI is green:

1. Merge the PR.
2. Close this Issue.

Closing this issue (labelled `issue-5`) will automatically open **Issue 6**.

---

## 🎉 Your project now has real database schema!

Next: you’ll create a superuser and log into the admin site.
