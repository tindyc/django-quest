---
name: "Issue 4 – Views & URL Routing"
about: "Create a basic view and wire it to the root URL"
title: "Issue 4 – Views & URL Routing"
labels: ["issue-4"]
assignees: ""
---

## 🎯 Goal

Create a simple view function in your app and wire it so that visiting `/` returns a successful response (`HTTP 200`).

This step focuses on **views + URL routing**, using a simple `HttpResponse` (no templates yet).

---

## 🧩 Placeholders

- `<project_name>` – your Django project folder.
- `<app_name>` – your Django app folder.

---

## ✅ Tasks

### 1. Create a basic view function

Open `<app_name>/views.py` and add:

```python
from django.http import HttpResponse

def home(request):
    return HttpResponse("Hello from my Django project!")
```

You can customise the text if you like.

---

### 2. Create your app’s `urls.py`

In `<app_name>/urls.py` (create this file if it does not exist), add:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("", views.home, name="home"),
]
```

This defines a URL pattern that maps the empty path (`""`) to the `home` view.

---

### 3. Include your app’s URLs in the project URLs

Open `<project_name>/urls.py` and make sure it looks like this:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path("admin/", admin.site.urls),
    path("", include("<app_name>.urls")),  # 👈 include your app's URLs here
]
```

Make sure to:

- Import `include` from `django.urls`.
- Replace `<app_name>` with your app name (without `<` and `>`).

---

### 4. Test locally

Run:

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/`.

You should see the text from your `home` view (e.g. `Hello from my Django project!`).

Stop the server with `CTRL+C` when you’re done.

---

## 🤖 What CI will check

For branches starting with `issue-4-` (or later), CI will:

- Re-run checks for Issues 1–3.
- Use Django’s URL resolver to resolve `/`.
- Use the Django test client to send `GET /`.
- Expect `status_code == 200`.

If CI fails:

- If it says it “could not resolve root URL '/'”, check:
  - `<app_name>/urls.py` exists.
  - `<project_name>/urls.py` includes `path("", include("<app_name>.urls"))`.
- If it says `GET "/" returned status code XXX`, check your `home` view and any middleware or errors in the console.

---

## 💾 Git & GitHub Workflow (Step-by-step)

1. **Create a branch** (must start with `issue-4-`):

   ```bash
   git checkout -b issue-4-url-and-view
   ```

2. **Check what changed:**

   ```bash
   git status
   ```

3. **Stage your changes:**

   ```bash
   git add <app_name>/views.py <app_name>/urls.py <project_name>/urls.py
   ```

4. **Commit your work:**

   ```bash
   git commit -m "Add home view and root URL routing"
   ```

5. **Push your branch:**

   ```bash
   git push -u origin issue-4-url-and-view
   ```

6. **Open a Pull Request targeting `main`** on GitHub.

7. **Wait for CI to run**:

   - If CI fails, read the message about resolving `/` or status code.
   - Fix the relevant file, commit, and push again.

8. **Merge when CI is green ✅**, then **close this Issue**.

Closing this Issue (labelled `issue-4`) will automatically open **Issue 5** for you.
