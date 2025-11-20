---
name: "Issue 2 – Project Core: Create Project Structure"
about: "Run django-admin startproject <project_name> ."
title: "Issue 2 – Project Core"
labels: ["issue-2"]
assignees: ""
---

## 🎯 Goal

Create the base Django project structure so that:

- `manage.py` exists in the repository root.
- A `<project_name>/` folder exists with `settings.py`, `urls.py`, `wsgi.py`, `asgi.py`, and `__init__.py`.
- You can run the development server and see the Django welcome page.

---

## 🧩 Placeholders

- `<project_name>` – choose a project name that fits your idea (e.g. `blogsite`, `taskmanager`, `shop`, `recipes`).

Do **not** type the `<` and `>` characters when you run commands.

---

## ✅ Tasks

> Make sure you completed **Issue 1** and can install packages from `requirements.txt`.

### 1. Create the Django project

From the root of your repo (where `requirements.txt` lives), run:

```bash
django-admin startproject <project_name> .
```

**Important:** The final `.` means “create the project in the current directory”.  
Without the dot, Django creates an extra nested folder that will break our CI.

This should create:

- `manage.py`
- `<project_name>/__init__.py`
- `<project_name>/settings.py`
- `<project_name>/urls.py`
- `<project_name>/wsgi.py`
- `<project_name>/asgi.py`

---

### 2. Test the development server locally

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` in your browser.

You should see the Django rocket “installation successful” page.

Press `CTRL+C` in the terminal to stop the server when you’re done.

---

## 🤖 What CI will check

For branches starting with `issue-2-` (or later), CI will:

- Re-run **Issue 1** checks (`requirements.txt` + Django).
- Check that `manage.py` exists.
- Read `DJANGO_SETTINGS_MODULE` from `manage.py`.
- Confirm the corresponding `settings.py` file exists at that path.

If something fails, common causes are:

- You forgot the `.` in `django-admin startproject <project_name> .`.
- You didn’t commit the `<project_name>/` folder.
- You accidentally edited or removed `DJANGO_SETTINGS_MODULE` in `manage.py`.

---

## 💾 Git & GitHub Workflow (Step-by-step)

1. **Create a branch** (must start with `issue-2-`):

   ```bash
   git checkout -b issue-2-project-core
   ```

2. **Check what changed:**

   ```bash
   git status
   ```

3. **Stage your changes:**

   ```bash
   git add manage.py <project_name>/
   ```

4. **Commit your work:**

   ```bash
   git commit -m "Create Django project structure"
   ```

5. **Push your branch:**

   ```bash
   git push -u origin issue-2-project-core
   ```

6. **Open a Pull Request targeting `main`** on GitHub.

7. **Wait for CI to run** (Django Setup Quest Checker):

   - If it fails, read the message about missing `manage.py` or `settings.py`.
   - Fix locally, commit, and push again; the PR will update automatically.

8. **Merge the PR when green ✅** and then **close this Issue**.

Closing this Issue (labelled `issue-2`) will automatically open **Issue 3** for you.
