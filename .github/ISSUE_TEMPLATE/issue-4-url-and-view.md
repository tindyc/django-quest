---
name: "Issue 4 – URL Routing & View Test"
about: "Create a view in your app and route the root URL ('/') to it"
title: "Issue 4 – URL Routing & View Test"
labels:
  - issue-4
assignees: ""
---

# 🌐 Issue 4 – URL Routing & View Test  

In this step you will:

- Create your first view function
- Map the root URL `/` to that view
- Confirm that visiting `/` returns HTTP 200

This is where your project starts responding to the browser.

---

## 🔄 1. Update local `main` and create a new branch

```bash
git checkout main
git pull origin main
git checkout -b issue-4-url-and-view
```

Make sure your virtual environment is active.

---

## 🧾 2. Create a simple view in your app

1. Open your app’s `views.py`, e.g. `blog/views.py`.
2. Add a simple homepage view:

```python
from django.http import HttpResponse

def home(request):
    return HttpResponse("Hello from your Django Quest app!")
```

You can customise the message if you like.

---

## 🧭 3. Create your app’s `urls.py` (if not present)

In your app folder (e.g. `blog/`), create a file named `urls.py` with:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]
```

This means: when the app’s URL config is included at some prefix, the empty path (`''`) will call `views.home`.

---

## 🧩 4. Include your app URLs in the project URLs

1. Open **project** `urls.py`, e.g. `django_project/urls.py`.
2. Import `include`:

```python
from django.urls import path, include
```

3. Add a pattern that points the **root URL** (`'/'`) to your app:

```python
urlpatterns = [
    path('', include('<app_name>.urls')),
    # path('admin/', admin.site.urls),  # (this is usually already there)
]
```

Replace `<app_name>` with your actual app name, e.g. `blog`.

Now `GET /` should go:

> project `urls.py` → include app `urls.py` → `home` view → `HttpResponse`.

---

## ✅ 5. Test locally

Run:

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` in your browser.

You should see your custom text from the `home` view.

Stop the server with **Ctrl + C** in the terminal.

---

## 💾 6. Commit your work

```bash
git status
git add <app_name>/views.py <app_name>/urls.py <project_name>/urls.py
git commit -m "Issue 4: Wire root URL to app home view"
```

---

## 🚀 7. Push your branch

```bash
git push -u origin issue-4-url-and-view
```

---

## 🔁 8. Open a Pull Request (PR)

- Open a PR from `issue-4-url-and-view` into `main`.
- Confirm base and compare branches.
- Create the PR.

---

## 🤖 9. Wait for the Django Quest Checker (CI)

The CI will:

- Attempt to resolve `/`
- Make a request using Django’s test client
- Expect HTTP status code **200**

If it fails:

- Check the error message — it will usually say:
  - It couldn’t resolve `/`, or
  - `/` returned a non-200 status
- Fix your URLs or view
- Commit & push again

---

## 🟢 10. Merge the PR & close this Issue

When CI is green:

1. Merge the PR.
2. Close this Issue.

Closing this issue (labelled `issue-4`) will automatically open **Issue 5**.

<details>
<summary><strong>📌 How to Close This Issue (and Unlock the Next One)</strong></summary>

When your pull request has been **successfully merged**, you must **close this issue manually** to trigger the next Quest.

### ✅ Steps to Close the Issue

1. Open your repository on GitHub  
2. Click the **Issues** tab  
3. Open the issue you just completed  
4. Scroll down and click **Close issue**  
5. Wait a few seconds — the **next Quest issue will be created automatically**

> ⚠️ **Important:**  
> Merging the pull request is **not enough**.  
> You *must* close the issue yourself for the next Quest to appear.

</details>

---

## 📝 Summary

<details>
<summary><strong>Click to expand</strong></summary>

### 🌟 What You Did  
- Added a view  
- Set up URLs  
- Connected app URLs to project URLs

### 🔧 Example Commands / Files Edited

#### No terminal commands required, except for git commits
You mainly edited these files:

- `<app-name>/views.py`
- `<app-name>/urls.py` (you created this)
- `<project-name>/urls.py`

</details>

---

## 🎉 Your project now handles real HTTP requests!

Next: you’ll create a database model and run migrations so your app can store data.
