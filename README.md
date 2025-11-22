# 🚀 The Django Quest  
Wellcome to Django Quest. Build Your First Django Project!

> ⚠️ **Important:**  
> This repository is a **Template** for the Django Quest.  
> **Do not** clone or fork this repo to do the exercises.  
> Instead, click **Use this template → Create a new repository** and work in **your own copy**.

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)]()
[![Django](https://img.shields.io/badge/Django-4.x-092E20?logo=django&logoColor=white)]()
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI-2088FF?logo=githubactions&logoColor=white)]()
[![GitHub Issues](https://img.shields.io/badge/GitHub-Issues-orange?logo=github&logoColor=white)]()
[![GitHub PRs](https://img.shields.io/badge/GitHub-Pull%20Requests-brightgreen?logo=github&logoColor=white)]()

Welcome to the **Django Setup Quest** — an interactive, automated, step-by-step journey where you build a fully working Django project using **GitHub Issues**, **Branches**, **Pull Requests**, and **GitHub Actions CI**.

Whether you're building a blog, a to-do app, an online shop, or your own idea — this Quest gives you the solid foundation for any Django project you start in the future.

---

# 🧰 Tech Stack & Skills You Will Learn

### 🐍 Backend & Python
- Python 3  
- Django  
- Virtual environments (`venv`)  
- Settings, apps, URLs, models, migrations, templates, and admin  

### 📦 Environment & Dependencies
- Installing packages with `pip`  
- Managing dependencies (`requirements.txt`)  
- Understanding environment isolation  

### 🗃 Database Layer
- Django ORM  
- Models & migrations  
- Django Admin  

### 🌐 Web Fundamentals
- URL routing  
- Views  
- Templates  
- Rendering DB data  

### 🛠 Git & GitHub Workflow
- Branching  
- Commit hygiene  
- Pull Requests  
- CI checks  
- Merging safely  

### 📝 GitHub Automation
- GitHub Issues as tasks  
- Issue Templates  
- Automatic Issue sequencing  
- CI validation  
- Auto README update on completion  

---

# ⭐ How to Start the Quest

## 1️⃣ Create your repo from this template  
1. Click **Use this template**  
2. Select **Create a new repository**  
3. Name it anything you like  
4. Recommended: make it **public**  
5. Click **Create repository**

---

## 2️⃣ Create **Issue 1**  
Automation cannot begin until Issue 1 exists.

1. Go to your new repo  
2. Open **Issues**  
3. Click **New Issue**  
4. Choose:  
   **Issue 1 – Setup Django & Dependencies**  
5. Submit Issue 1  

🎉 The Quest has officially begun.

---

# 🧩 The Quest Loop (You’ll Repeat This for Issues 1–6)

<details>
<summary><strong>🔁 Click to view</strong></summary>
Each Issue contains step-by-step instructions, screenshots, tips, and common mistakes for that specific task.  
You’ll find all the detailed explanations inside the Issues themselves — this section is just a quick overview of the workflow.

### 1️⃣ Open the current Issue  
Read the instructions carefully — the Issue explains exactly what to do and what the CI will check.

### 2️⃣ Create your branch  
Must start with:

```
issue-X-
```

Examples:

```
issue-1-install-django
issue-3-create-app
issue-5-models
```

### 3️⃣ Do the work locally
>> Please make sure you are working in the **issue** branch.

### 4️⃣ Commit & push  
```
git add .
git commit -m "Completed Issue X"
git push -u origin issue-X-description
```

### 5️⃣ Open a Pull Request  
Base: `main`  
Compare: `issue-X-*`

### 6️⃣ CI validates your progress

### 7️⃣ Fix anything CI reports

### 8️⃣ Merge the PR & close the Issue  
Closing each Issue automatically generates the next one.

</details>

---

# 💻 Git & Terminal Cheat Sheet

<details>
<summary><strong>📚 Click to expand</strong></summary>

| Action | Command |
|--------|---------|
| Create branch | `git checkout -b issue-X-name` |
| Check changes | `git status` |
| Stage | `git add .` |
| Commit | `git commit -m "message"` |
| Push | `git push -u origin issue-X-name` |
| Switch | `git checkout main` |
| Update | `git pull` |

After merging:

```
git checkout main
git pull
```

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

# 🎉 You're Ready!

You will build:

- A Django project  
- A custom app  
- URL routing  
- Templates  
- Models & migrations  
- Admin + Superuser  
- A complete backend foundation  

Good luck ⚡🧙‍♂️

---

# 🆘 Need Help?

## 📬 Contact Me on Discord

<a href="https://discord.com/users/tindychan">
  <img src="https://img.shields.io/badge/Message%20Me%20on%20Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" />
</a>

> Happy to help with debugging, installation issues, or anything in the Quest.

Tindy
