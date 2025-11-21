---
name: "Issue 2 – Project Core: Create Project Structure"
about: "Create your main Django project with manage.py and settings.py"
title: "Issue 2 – Project Core: Create Project Structure"
labels:
  - issue-2
assignees: ""
---

# 🧱 Issue 2 – Project Core: Create Project Structure  

In this step you will:

- Create your main Django project
- Generate `manage.py`
- Create the project settings module
- Prepare for apps, URLs, and views

---

## 🔄 1. Update local `main` and create a new branch

1. Make sure your virtual environment is active (`(venv)` in your terminal).
2. Switch back to `main` and pull latest changes:

```bash
git checkout main
git pull origin main
```

3. Create a new branch for this issue:

```bash
git checkout -b issue-2-project-core
```

---

## 🏗 2. Create your Django project

You can pick any project name you like, such as `django_project`, `community_platform`, or `mysite`.  
In this quest we’ll call it `<project_name>` in the instructions — replace it with **your** chosen name.

> 🔑 The final dot `.` at the end of the command is **very important**.  
> It tells Django to place files in the *current folder* instead of creating a nested directory.

Run:

```bash
django-admin startproject <project_name> .
```
> Please remember the dot `.`at the end!

Example:

```bash
django-admin startproject django_project .
```

This should create:

- `manage.py`
- A folder named after your project (e.g. `django_project/`)
  - `__init__.py`
  - `settings.py`
  - `urls.py`
  - `asgi.py`
  - `wsgi.py`

---

## ✅ 3. Sanity check: does the dev server run?

Run:

```bash
python manage.py runserver
```

You should see a message ending with something like:

```text
Starting development server at http://127.0.0.1:8000/
```

Open the URL in your browser — you should see Django’s default “rocket” welcome page.

Press **Ctrl + C** (or **Cmd + C** in the terminal) to stop the server.

---

## 🧾 4. Review your changes

In VS Code:

- You should see `manage.py` at the project root.
- You should see your project folder (e.g. `django_project/`) with `settings.py` and `urls.py` inside.

---

## 💾 5. Commit your work

```bash
git status      # check which files changed
git add manage.py <project_name>/
git commit -m "Issue 2: Create Django project core"
```

(Replace `<project_name>` with your actual project folder, e.g. `django_project/`.)

---

## 🚀 6. Push your branch to GitHub

```bash
git push -u origin issue-2-project-core
```

---

## 🔁 7. Open a Pull Request (PR)

1. Go to your repository on GitHub.
2. Click **Compare & pull request**.
3. Check:
   - **Base branch:** `main`
   - **Compare branch:** `issue-2-project-core`
4. Click **Create pull request**.

---

## 🤖 8. Wait for the Django Quest Checker (CI)

The CI will now:

- Check that `requirements.txt` contains Django (Issue 1)
- Check that `manage.py` exists and that your settings module can be found (Issue 2)

If it’s green (✅), you’re good.

If it’s red (❌):

1. Open the **Checks** tab.
2. Read the error message (it will say exactly what’s missing or wrong).
3. Fix the issue locally.
4. `git add`, `git commit`, and `git push` again.

---

## 🟢 9. Merge the PR & close this Issue

Before merging, **wait for all checks to finish**.  
Only merge when the status shows **✅ All checks have passed**.

Merging too early (before CI finishes) can cause failures or block the next Quest.

Once CI is **green**:

1. Click **Merge pull request**.
2. Return to this Issue.
3. Click **Close issue**.

Closing this issue (labelled `issue-2`) will automatically open **Issue 3** for you.

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

## 🎉 Nice work!

Your Django project core is now created.  
Next up: **create your first app and register it properly.**
