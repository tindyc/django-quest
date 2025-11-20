---
name: "Issue 5 – Models, Migrations & Templates"
about: "Create a model, run migrations, and display data in a template"
title: "Issue 5 – Models, Migrations & Templates"
labels: ["issue-5"]
assignees: ""
---

## 🎯 Goal

Create your first model, run migrations, and then render that model’s data in a Django template.

You will move from:

- Static `HttpResponse` → HTML template  
- Hard-coded text → Data stored in the database

---

## 🧩 Placeholders

- `<app_name>` – your Django app folder name.

---

## ✅ Tasks

### 1. Define a model in `<app_name>/models.py`

Open `<app_name>/models.py` and define a model that fits your project idea.

Example (customise as you like):

```python
from django.db import models

class Item(models.Model):  # You can rename this (e.g. Post, Task, Recipe)
    title = models.CharField(max_length=100)
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title
```

Choose a name and fields that make sense (e.g. `Post(title, body)`, `Task(title, done)`, `Recipe(title, instructions)`).

---

### 2. Make and apply migrations

From your terminal:

```bash
python manage.py makemigrations
python manage.py migrate
```

This will:

- Generate migration files under `<app_name>/migrations/`.
- Apply them to your database.

---

### 3. Create some sample data

You can do this via the admin later, but let’s create a couple of records right now from the Django shell:

```bash
python manage.py shell
```

Then in the Python shell:

```python
from <app_name>.models import Item  # or your model name
Item.objects.create(title="First item")
Item.objects.create(title="Second item")
exit()
```

Now your database has some rows to display.

---

### 4. Create a template to display the items

Create the following folder structure:

```
templates/<app_name>/item_list.html
```

In `templates/<app_name>/item_list.html`, add:

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My Items</title>
  </head>
  <body>
    <h1>Items</h1>
    <ul>
      {% for item in items %}
        <li>{{ item.title }}</li>
      {% empty %}
        <li>No items yet.</li>
      {% endfor %}
    </ul>
  </body>
</html>
```

> 🔎 Tip: Django’s default settings already look for templates in app directories when `APP_DIRS` is `True` (which it is by default for new projects).

---

### 5. Update your view to render the template with data

Open `<app_name>/views.py` and change it to something like:

```python
from django.shortcuts import render
from .models import Item  # or your model class name

def item_list(request):
    items = Item.objects.all()
    return render(request, "<app_name>/item_list.html", {"items": items})
```

Replace `<app_name>` with your actual app name.

---

### 6. Update your app’s URLs to use the new view

Open `<app_name>/urls.py` and update it to:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("", views.item_list, name="item-list"),
]
```

Now, visiting `/` (root URL) should show the list of items from the database.

---

### 7. Test locally

Run:

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/`.

You should see your HTML page with a list of items.  
If you created sample data earlier, you’ll see them listed; otherwise you should see “No items yet.”

---

## 🤖 What CI will check

For branches starting with `issue-5-` (or later), CI will:

- Re-run checks for Issues 1–4.
- Run:

  ```bash
  python manage.py makemigrations --noinput
  python manage.py migrate --noinput
  ```

If there is a problem with your model code (syntax errors, missing imports, etc.), CI will fail at `makemigrations` or `migrate` and tell you something is wrong.

> 🧠 Tip: If CI fails, run the same commands locally and read the full error message:
>
> ```bash
> python manage.py makemigrations
> python manage.py migrate
> ```

---

## 💾 Git & GitHub Workflow (Step-by-step)

1. **Create a branch** (must start with `issue-5-`):

   ```bash
   git checkout -b issue-5-models-and-templates
   ```

2. **Check what changed:**

   ```bash
   git status
   ```

3. **Stage your changes** (models, migrations, templates, views, urls):

   ```bash
   git add <app_name>/models.py <app_name>/migrations/ templates/<app_name>/item_list.html <app_name>/views.py <app_name>/urls.py
   ```

4. **Commit your work:**

   ```bash
   git commit -m "Add model, migrations, and template list view"
   ```

5. **Push your branch:**

   ```bash
   git push -u origin issue-5-models-and-templates
   ```

6. **Open a Pull Request targeting `main`** on GitHub.

7. **Wait for CI**:

   - If CI fails on `makemigrations` or `migrate`, review your `models.py`.
   - Fix locally, commit, and push again.

8. **Merge when CI is green ✅**, then **close this Issue**.

Closing this Issue (labelled `issue-5`) will automatically open **Issue 6** for you.
