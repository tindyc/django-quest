> ⚠️ **Important:**  
> This repository is a **Template** for the Django Quest.  
> **Do not** clone or fork this repo to do the exercises.  
> Instead, click **Use this template → Create a new repository** and work in **your own copy**.

# 🚀 The Django Setup Quest: Build Your First Django Project!

![Django Logo](https://img.icons8.com/color/452/django.png)

Welcome to the **Django Setup Quest** — an interactive, automated, step-by-step journey that teaches you how to build a fully working Django project using **GitHub Issues**, **Pull Requests**, and **GitHub Actions**.

Whether you're building a blog, a to-do list manager, an online shop, or your own idea — this Quest gives you the solid foundation every Django developer needs.

---

## 🎯 What You Will Build

By the end of this Quest, you will have a fully functioning Django project with:

- ✔ A dedicated Python virtual environment  
- ✔ A `requirements.txt` with your dependencies  
- ✔ A Django project (`manage.py`, `settings.py`, etc.)  
- ✔ A custom Django app registered in `INSTALLED_APPS`  
- ✔ A working homepage routed through your app  
- ✔ A real database model + migrations  
- ✔ A template that displays database data  
- ✔ A superuser + working Django Admin  

---

## 🧭 How the Django Quest Works

This workshop uses **GitHub’s own features** as the learning platform:

- 📌 **Issues** = your instructions  
- 📌 **Branches** = your workspace  
- 📌 **Pull Requests** = your submissions  
- 📌 **GitHub Actions CI** = your automated mentor  

You complete the quest one Issue at a time.  
Each Issue gives you instructions and also triggers validation checks in GitHub Actions.

---

## ⭐ Before You Begin: Start Issue 1

Because this repository uses automatic Issue sequencing, you must create **Issue #1 manually** the very first time.

<details>
<summary><strong>👉 Step 1 — Create and Open Issue #1</strong> (click to expand)</summary>

1. Go to the **Issues** tab in this GitHub repository  
2. Click **New Issue**  
3. Select the template:  
   > <strong>“Issue 1 – Setup: Install Django & Dependencies”</strong>  
4. Submit the issue  

Once Issue 1 exists, the rest of the quest unlocks automatically.  
When you close Issue 1 at the end, **Issue 2** will be created for you.

</details>

---

## 🧩 The Quest Loop (Your Process for Every Issue)

This is the pattern you’ll repeat for every Issue (1 → 6).  
If you ever feel lost, come back to this section.

<details>
<summary><strong>🔁 The 8-Step Quest Loop (click to expand)</strong></summary>

### 1️⃣ Open the current Issue

Read the instructions **carefully**.  
Every Issue tells you:

- What you're building  
- The exact commands to run  
- The files to create/edit  
- What the CI will validate  

---

### 2️⃣ Create a new branch for that Issue

Your branch MUST start with:

```bash
issue-X-
```

Where `X` is the Issue number (1–6).

Examples:

```bash
issue-1-install-django
issue-2-create-project
issue-3-create-app
issue-4-routing-view
issue-5-models-and-template
issue-6-superuser
```

This naming is important:  
The GitHub Action uses your branch name to know **which Issue’s checks** to run.

---

### 3️⃣ Do the work locally

Follow the steps in the Issue:

- Install dependencies  
- Run Django commands  
- Create/edit files  
- Test your project with:

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` in your browser to check.

---

### 4️⃣ Commit & push your work

When you’re happy with your changes:

```bash
git add .
git commit -m "Completed Issue X tasks"
git push -u origin issue-X-description
```

Replace `X` with the Issue number.

---

### 5️⃣ Open a Pull Request (PR)

1. Go to your repository on GitHub  
2. Click **“Compare & pull request”** (you should see a banner)  
3. Make sure:  
   - **Base branch**: `main`  
   - **Compare branch**: `issue-X-...`  
4. Submit the PR  

---

### 6️⃣ Let the CI checker validate your work

The **Django Setup Quest Checker** will run automatically on your PR.

- 🟢 **Green** = Everything looks good  
- 🔴 **Red** = Something needs fixing  

Click the failing check, then:

- Open the job log  
- Read the error message (it will mention specific files or steps)  

---

### 7️⃣ Fix issues (if needed)

If CI failed:

1. Go back to your code locally  
2. Fix the problem (e.g. missing file, wrong command, typo)  
3. Run:

```bash
git add .
git commit -m "Fix CI for Issue X"
git push
```

The PR will update and CI will re-run automatically.

---

### 8️⃣ Merge & close the Issue

Once CI is green:

1. Click **“Merge pull request”** → confirm  
2. Go to the corresponding Issue → click **“Close issue”**  

🎉 When you close each Issue, the next Issue in the Quest is automatically opened for you.

</details>

---

## 💻 Git & Terminal Cheat Sheet

<details>
<summary><strong>📚 Git Commands You’ll Use Often (click to expand)</strong></summary>

| Action | Command | Why |
|-------|---------|-----|
| Create branch | `git checkout -b issue-X-name` | Start work for Issue X on a new branch |
| Check changes | `git status` | See which files changed or are untracked |
| Stage changes | `git add .` | Add all changes to the next commit |
| Stage specific file | `git add path/to/file` | Only add a particular file |
| Commit | `git commit -m "message"` | Save a snapshot of your work |
| Push | `git push -u origin issue-X-name` | Upload your branch to GitHub |
| Switch to main | `git checkout main` | Move back to main branch |
| Update main | `git pull` | Get the latest changes from GitHub |

💡 **Tip:** After merging a PR on GitHub, remember to:

```bash
git checkout main
git pull
```

So your local `main` matches the remote `main`.

</details>

---

## 🛠 Troubleshooting Guide

<details>
<summary><strong>❌ CI says "requirements.txt not found" (click to expand)</strong></summary>

You probably forgot to create or commit `requirements.txt`.

Fix:

```bash
pip freeze --local > requirements.txt
git add requirements.txt
git commit -m "Add requirements file"
git push
```

Then reopen your PR page and wait for CI to re-run.

</details>

<details>
<summary><strong>❌ CI says "Django is missing from requirements.txt"</strong></summary>

You may have installed Django but didn’t regenerate `requirements.txt`.

Fix:

```bash
pip install "Django>=4.2,<6.0"   # if not already installed
pip freeze --local > requirements.txt
git add requirements.txt
git commit -m "Ensure Django is in requirements"
git push
```

</details>

<details>
<summary><strong>❌ CI says "manage.py not found"</strong></summary>

This usually means the project was created without the final dot:

```bash
django-admin startproject <project_name> .
```

**Fix:**

1. Remove any incorrect extra nested folders (if needed)  
2. Re-run:

```bash
django-admin startproject <project_name> .
```

3. Commit and push the new files:

```bash
git add manage.py <project_name>/
git commit -m "Fix project structure"
git push
```

</details>

<details>
<summary><strong>❌ CI says "Could not resolve root URL '/'"</strong></summary>

Check these:

1. You created `<app_name>/urls.py` with a pattern for `""` (empty path)  
2. Your `<project_name>/urls.py` includes your app URLs:

```python
from django.urls import path, include

urlpatterns = [
    path("admin/", admin.site.urls),
    path("", include("<app_name>.urls")),
]
```

Don’t forget to:

```bash
git add <app_name>/urls.py <project_name>/urls.py
git commit -m "Wire up root URL"
git push
```

</details>

<details>
<summary><strong>❌ CI failing on migrations</strong></summary>

Run the commands locally to see the full error:

```bash
python manage.py makemigrations
python manage.py migrate
```

Common fixes:

- Check for typos in `models.py`  
- Make sure your app is in `INSTALLED_APPS`  
- Make sure you imported `models` correctly  

After fixing:

```bash
git add <app_name>/models.py <app_name>/migrations/
git commit -m "Fix model and migrations"
git push
```

</details>

<details>
<summary><strong>❌ CI shows only a notice: "No Django Quest checks ran..."</strong></summary>

This means your **branch name** is wrong.  
It must start with:

```bash
issue-X-
```

Examples that **work**:

- `issue-1-setup-django`
- `issue-3-blog-app`
- `issue-5-models`

Examples that **do not work**:

- `issue1`
- `setup-issue-1`
- `my-branch`

Create a correctly named branch and repeat the steps for that Issue.

</details>

---

## 🎉 You're Ready to Start!

Create **Issue 1** using the template and begin your Quest!  

You’ll build:

- 🧱 A Django project  
- 🧩 A custom app  
- 🌐 URL routing  
- 🖼 Templates  
- 🔗 Models & migrations  
- 🛡️ Admin + Superuser  
- ⚙️ A complete, working backend foundation  

Good luck — may your migrations always succeed and your debugging be swift! 🧙‍♂️⚡  

---

*Happy Coding!* 💚

Author: Tindy