---
name: "Issue 3 – App Creation & Registration"
about: "Create your first Django app and add it to INSTALLED_APPS"
title: "Issue 3 – App Creation & Registration"
labels: ["issue-3"]
assignees: ""
---

## 🎯 Goal

Create your first Django app and register it in the project’s `INSTALLED_APPS`.

You choose the app name based on what you’re building.

Examples:

- Blog → `blog`
- Todo list → `tasks`
- Recipes → `recipes`
- Shop → `shop`

---

## 🧩 Placeholders

- `<app_name>` – the name of your app (e.g. `blog`, `tasks`, `recipes`).

Do **not** type the `<` and `>` characters when you run commands.

---

## ✅ Tasks

> Make sure `python manage.py runserver` works before doing this.

### 1. Create the app

```bash
python manage.py startapp <app_name>
```

This will create a folder `<app_name>/` containing:

- `apps.py`
- `models.py`
- `views.py`
- `admin.py`
- `tests.py`
- `migrations/` (folder, usually with `__init__.py`)

---

### 2. Register the app in your project settings

Open `<project_name>/settings.py` and find the `INSTALLED_APPS` list.

Add your app name to it, for example:

```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "<app_name>",  # 👈 add this line
]
```

Make sure you spell `<app_name>` exactly the same as your folder name.

---

### 3. Optional sanity check

Run Django’s built-in checks:

```bash
python manage.py check
```

If everything is set up correctly, it should report no errors.

---

## 🤖 What CI will check

For branches starting with `issue-3-` (or later), CI will:

- Re-run **Issue 1** and **Issue 2** checks.
- Look for app folders that contain `apps.py` (e.g. `<app_name>/apps.py`).
- For each such app folder, check that the folder name appears in `INSTALLED_APPS` in your settings file.

If CI finds an app folder but does not see its name in `INSTALLED_APPS`, it will fail and tell you which app is missing.

> ❗ If you see a notice like:
>
> `No Django Quest checks ran because your branch name does not start with 'issue-X-'`
>
> Make sure your branch name starts with `issue-3-`.

---

## 💾 Git & GitHub Workflow (Step-by-step)

1. **Create a branch** (must start with `issue-3-`):

   ```bash
   git checkout -b issue-3-create-<app_name>-app
   ```

2. **Check what changed:**

   ```bash
   git status
   ```

3. **Stage your changes:**

   ```bash
   git add <app_name>/ <project_name>/settings.py
   ```

4. **Commit your work:**

   ```bash
   git commit -m "Create and register <app_name> app"
   ```

5. **Push your branch:**

   ```bash
   git push -u origin issue-3-create-<app_name>-app
   ```

6. **Open a Pull Request targeting `main`** on GitHub.

7. **Wait for CI (Django Setup Quest Checker):**

   - If CI fails and complains about an app not in `INSTALLED_APPS`, open `<project_name>/settings.py` and add it.
   - Commit and push again; CI will re-run.

8. **Merge when CI is green ✅**, then **close this Issue**.

Closing this Issue (labelled `issue-3`) will automatically open **Issue 4** for you.
