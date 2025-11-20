---
name: "Issue 3 – App Creation & Registration"
about: "Create your first Django app and register it in INSTALLED_APPS"
title: "Issue 3 – App Creation & Registration"
labels: issue-3
assignees: ""
---

# 🧩 Issue 3 – App Creation & Registration  

In this step you will:

- Create your first Django app
- Register it in `INSTALLED_APPS`
- Prepare it for URLs, views, and models

You get to choose what kind of app you’re building (blog, tasks, notes, etc.).

---

## 🔄 1. Update local `main` and create a new branch

1. Activate your virtual environment if needed.
2. Make sure `main` is up to date:

```bash
git checkout main
git pull origin main
```

3. Create a new branch for this issue:

```bash
git checkout -b issue-3-app-and-registration
```

---

## 🧱 2. Choose an app name & create the app

Pick a meaningful app name, e.g.:

- `blog`
- `tasks`
- `notes`
- `products`

Then run:

```bash
python manage.py startapp <app_name>
```

Example:

```bash
python manage.py startapp blog
```

This will create a new folder, e.g. `blog/`, containing:

- `apps.py`
- `models.py`
- `views.py`
- `tests.py`
- `admin.py`
- `migrations/` folder, etc.

---

## 🧾 3. Register your app in `INSTALLED_APPS`

1. Open your **project** settings file — this is in the folder you created in Issue 2:

   - e.g. `config/settings.py` or `core/settings.py`

2. Find the `INSTALLED_APPS` list.
3. Add your app name as a string, for example:

```python
INSTALLED_APPS = [
    # Django default apps...
    'django.contrib.staticfiles',

    # Your app(s)
    'blog',
]
```

Make sure:

- The string matches your app folder name exactly.
- It has a trailing comma.

---

## 🧪 4. Run basic Django checks

Run:

```bash
python manage.py check
```

If everything is set up correctly, Django should report **no issues**.

If you see an error, read it carefully — most likely it’s a typo in `INSTALLED_APPS`.

---

## 💾 5. Commit your work

```bash
git status
git add <app_name>/ <project_name>/settings.py
git commit -m "Issue 3: Create app and register in INSTALLED_APPS"
```

Replace `<app_name>` and `<project_name>` appropriately.

---

## 🚀 6. Push your branch

```bash
git push -u origin issue-3-app-and-registration
```

---

## 🔁 7. Open a Pull Request (PR)

1. On GitHub, open a PR from `issue-3-app-and-registration` into `main`.
2. Confirm the base and compare branches are correct.
3. Create the PR.

---

## 🤖 8. Wait for the Django Quest Checker (CI)

The CI now checks that:

- At least one app exists (has an `apps.py` file).
- That app is registered in `INSTALLED_APPS`.

Red (❌)?  

- Open the **Checks** tab.  
- Fix whatever the error message describes.  
- Commit and push again.

Green (✅)?

- You’re ready to merge!

---

## 🟢 9. Merge the PR & close this Issue

1. Merge the PR.
2. Return to this Issue.
3. Click **Close issue**.

Closing this issue (labelled `issue-3`) will automatically open **Issue 4**.

---

## 🎉 You now have a real Django app!

Next up: wiring a URL to a view so your app can actually respond to a browser request.
